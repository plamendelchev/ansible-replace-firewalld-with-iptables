# Replace Firewalld with Iptables

Ansible role for replacing firewalld with iptables.

## Role Variables

**IMPORTANT** This role will check whether the `firewalld` is installed. If yes, it will flush all rules from the `filter` table and set the chain policies (INPUT, FORWARD, OUTPUT) to ACCEPT. To modify this behaviour, use:

- `replace_firewalld_with_iptables_accept_chain_policy` *type:bool, default:true* Whether to set the chain policies to ACCEPT **if firewalld is removed**.
- `replace_firewalld_with_iptables_remove_leftovers` *type:bool, default:true* Whether to remove all iptables rules from filter table **if firewalld is removed**.

If the `firewalld` package is **not** installed on the system, the role will **not** try to flush the rules and set the chains policy.

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: ansible-replace-firewalld-with-iptables
```

## License

GPL-3.0
