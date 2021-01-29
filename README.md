Role Name
=========

Ansible Role for configuring Zabbix via Zabbix API (without GUI)


Installation
------------
1) Change directory to your ansible roles directory, for example:

    cd ~/src/ansible/roles


2) Clone repo:

    git clone https://github.com/pavlovdo/ansible-role-zabbixserver


3) Rename role directory to zabbixserver:

    mv ansible-role-zabbixserver zabbixserver


Requirements
------------

None.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Available variables are listed below, along with default values (see `defaults/main.yml`):


User/password for work with Zabbix API (should be added via Zabbix GUI, with permissions to create all objects):

    zabbix_api_user: zbx_api
    zabbix_api_password: test


SNMP community for write to macro of Zabbix hosts with linked SNMP templates:

    zabbix_default_snmp_community: public


User/password for write to macro of Zabbix hosts with linked VMware template:

    zabbix_esxi_user: zbx_monitor
    zabbix_esxi_password: test


User/password for write to macro of Zabbix hosts with linked IPMI templates:

    zabbix_ipmi_user: zbx_monitor
    zabbix_ipmi_password: test


Password for write to macro of Zabbix hosts with linked IPMI templates, when IMM/iBMC card not support strong passwords:    

    zabbix_ipmi_simple_password: zbx_simple_password


Passwords for users: username1, username2 etc:

    zabbix_username1_password: test


User/Password for web checks:

    zabbix_webcheck_user: test
    zabbix_webcheck_password: test


List of loaded templates (*.json files in dir zabbixserver/files):

    zabbix_templates:


List of your common hostgroups (for all your zabbix servers):

    zabbix_hostgroups:


List of your common hosts (for all your zabbix servers):    

    zabbix_hosts:


List of your common web hosts (web checks for all your zabbix servers):    

    zabbix_web_hosts:


List of your common usersgroups (for all your zabbix servers):

    zabbix_usergroups:


List of your common users (for all your zabbix servers):    

    zabbix_users:


List of your common actions (for all your zabbix servers):    

    zabbix_actions:


Zabbix Housekeeping settings:
https://www.zabbix.com/documentation/current/manual/api/reference/housekeeping/object#housekeeping
https://www.zabbix.com/documentation/current/manual/web_interface/frontend_sections/administration/general#housekeeper

    zabbix_hk_events_mode: 1
    zabbix_hk_events_trigger: 365d
    zabbix_hk_events_internal: 1d
    zabbix_hk_events_discovery: 1d
    zabbix_hk_events_autoreg: 1d
    zabbix_hk_services_mode: 1
    zabbix_hk_services: 365d
    zabbix_hk_audit_mode: 1
    zabbix_hk_audit: 365d
    zabbix_hk_sessions_mode: 1
    zabbix_hk_sessions: 365d
    zabbix_hk_history_mode: 1
    zabbix_hk_history_global: 1
    zabbix_hk_history: 93d
    zabbix_hk_trends_mode: 1
    zabbix_hk_trends_global: 1
    zabbix_hk_trends: 365d
    zabbix_compression_status: 1
    zabbix_compress_older: 7d        


Define that variables in playbooks of zabbix servers - expand variables for specific monitoring server:

    zabbix_server_url: "http://mon.example.com/api_jsonrpc.php"
    zabbix_smtp_email_from: "mon@example.com"
    zabbix_templates_custom: []
    zabbix_hostgroups_custom: []
    zabbix_hosts_custom: []
    zabbix_web_hosts_custom: []
    zabbix_usergroups_custom: []
    zabbix_users_custom: []
    zabbix_actions_custom: []    


Dependencies
------------

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - zabbixserver
```


License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
