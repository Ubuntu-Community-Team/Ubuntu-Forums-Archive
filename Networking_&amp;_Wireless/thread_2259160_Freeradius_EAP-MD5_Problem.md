---
title: "Freeradius EAP-MD5 Problem"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by nabil5 on 2015-01-02
Hi all of you. I just registered on this forum and i wish you a happy new year ! :)

Well, i have a little problem with freeradius. I have installed it on Ubuntu Server 12.04 LTS. Here is my project. I want to make a radius server where users can use an username and password to logon on access points. But nothing more and nothing less. I have configured the radius server for EAP-MD5 authentification but when i try to test the configuration with freeradius -XXX, i get this message at the end :

Fri Jan  2 18:13:27 2015 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Feb 24 2014 at 15:16:51
Fri Jan  2 18:13:27 2015 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors.
Fri Jan  2 18:13:27 2015 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
Fri Jan  2 18:13:27 2015 : Info: PARTICULAR PURPOSE.
Fri Jan  2 18:13:27 2015 : Info: You may redistribute copies of FreeRADIUS under the terms of the
Fri Jan  2 18:13:27 2015 : Info: GNU General Public License v2.
Fri Jan  2 18:13:27 2015 : Info: Starting - reading configuration files ...
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/radiusd.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/proxy.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/clients.conf
Fri Jan  2 18:13:27 2015 : Debug: including files in directory /etc/freeradius/modules/
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/linelog
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/radutmp
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/otp
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/realm
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/checkval
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/unix
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/logintime
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/expr
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/digest
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/detail.log
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/pam
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/files
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/etc_group
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/exec
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/preprocess
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/ippool
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/echo
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/counter
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/krb5
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/perl
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/mschap
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/wimax
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/policy
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/ldap
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/sql_log
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/passwd
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/smsotp
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/chap
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/pap
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/expiration
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/cui
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/detail
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/always
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/eap.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sql.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/policy.conf
Fri Jan  2 18:13:27 2015 : Debug: including files in directory /etc/freeradius/sites-enabled/
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sql.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Fri Jan  2 18:13:27 2015 : Debug: including configuration file /etc/freeradius/sites-enabled/control-socket
Fri Jan  2 18:13:27 2015 : Debug: main {
Fri Jan  2 18:13:27 2015 : Debug:       user = "freerad"
Fri Jan  2 18:13:27 2015 : Debug:       group = "freerad"
Fri Jan  2 18:13:27 2015 : Debug:       allow_core_dumps = no
Fri Jan  2 18:13:27 2015 : Debug: }
Fri Jan  2 18:13:27 2015 : Debug: including dictionary file /etc/freeradius/dictionary
Fri Jan  2 18:13:27 2015 : Debug: main {
Fri Jan  2 18:13:27 2015 : Debug:       prefix = "/usr"
Fri Jan  2 18:13:27 2015 : Debug:       localstatedir = "/var"
Fri Jan  2 18:13:27 2015 : Debug:       logdir = "/var/log/freeradius"
Fri Jan  2 18:13:27 2015 : Debug:       libdir = "/usr/lib/freeradius"
Fri Jan  2 18:13:27 2015 : Debug:       radacctdir = "/var/log/freeradius/radacct"
Fri Jan  2 18:13:27 2015 : Debug:       hostname_lookups = no
Fri Jan  2 18:13:27 2015 : Debug:       max_request_time = 30
Fri Jan  2 18:13:27 2015 : Debug:       cleanup_delay = 5
Fri Jan  2 18:13:27 2015 : Debug:       max_requests = 1024
Fri Jan  2 18:13:27 2015 : Debug:       pidfile = "/var/run/freeradius/freeradius.pid"
Fri Jan  2 18:13:27 2015 : Debug:       checkrad = "/usr/sbin/checkrad"
Fri Jan  2 18:13:27 2015 : Debug:       debug_level = 0
Fri Jan  2 18:13:27 2015 : Debug:       proxy_requests = yes
Fri Jan  2 18:13:27 2015 : Debug:  log {
Fri Jan  2 18:13:27 2015 : Debug:       stripped_names = no
Fri Jan  2 18:13:27 2015 : Debug:       auth = no
Fri Jan  2 18:13:27 2015 : Debug:       auth_badpass = no
Fri Jan  2 18:13:27 2015 : Debug:       auth_goodpass = no
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  security {
Fri Jan  2 18:13:27 2015 : Debug:       max_attributes = 200
Fri Jan  2 18:13:27 2015 : Debug:       reject_delay = 1
Fri Jan  2 18:13:27 2015 : Debug:       status_server = yes
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug: }
Fri Jan  2 18:13:27 2015 : Debug: radiusd: #### Loading Realms and Home Servers ####
Fri Jan  2 18:13:27 2015 : Debug:  proxy server {
Fri Jan  2 18:13:27 2015 : Debug:       retry_delay = 5
Fri Jan  2 18:13:27 2015 : Debug:       retry_count = 3
Fri Jan  2 18:13:27 2015 : Debug:       default_fallback = no
Fri Jan  2 18:13:27 2015 : Debug:       dead_time = 120
Fri Jan  2 18:13:27 2015 : Debug:       wake_all_if_all_dead = no
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  home_server localhost {
Fri Jan  2 18:13:27 2015 : Debug:       ipaddr = 127.0.0.1
Fri Jan  2 18:13:27 2015 : Debug:       port = 1812
Fri Jan  2 18:13:27 2015 : Debug:       type = "auth"
Fri Jan  2 18:13:27 2015 : Debug:       secret = "testing123"
Fri Jan  2 18:13:27 2015 : Debug:       response_window = 20
Fri Jan  2 18:13:27 2015 : Debug:       max_outstanding = 65536
Fri Jan  2 18:13:27 2015 : Debug:       require_message_authenticator = yes
Fri Jan  2 18:13:27 2015 : Debug:       zombie_period = 40
Fri Jan  2 18:13:27 2015 : Debug:       status_check = "status-server"
Fri Jan  2 18:13:27 2015 : Debug:       ping_interval = 30
Fri Jan  2 18:13:27 2015 : Debug:       check_interval = 30
Fri Jan  2 18:13:27 2015 : Debug:       num_answers_to_alive = 3
Fri Jan  2 18:13:27 2015 : Debug:       num_pings_to_alive = 3
Fri Jan  2 18:13:27 2015 : Debug:       revive_interval = 120
Fri Jan  2 18:13:27 2015 : Debug:       status_check_timeout = 4
Fri Jan  2 18:13:27 2015 : Debug:       irt = 2
Fri Jan  2 18:13:27 2015 : Debug:       mrt = 16
Fri Jan  2 18:13:27 2015 : Debug:       mrc = 5
Fri Jan  2 18:13:27 2015 : Debug:       mrd = 30
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  home_server_pool my_auth_failover {
Fri Jan  2 18:13:27 2015 : Debug:       type = fail-over
Fri Jan  2 18:13:27 2015 : Debug:       home_server = localhost
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  realm example.com {
Fri Jan  2 18:13:27 2015 : Debug:       auth_pool = my_auth_failover
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  realm LOCAL {
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug: radiusd: #### Loading Clients ####
Fri Jan  2 18:13:27 2015 : Debug:  client localhost {
Fri Jan  2 18:13:27 2015 : Debug:       ipaddr = 127.0.0.1
Fri Jan  2 18:13:27 2015 : Debug:       require_message_authenticator = no
Fri Jan  2 18:13:27 2015 : Debug:       secret = "cht1000"
Fri Jan  2 18:13:27 2015 : Debug:       nastype = "other"
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug:  client 192.168.100.15 {
Fri Jan  2 18:13:27 2015 : Debug:       require_message_authenticator = no
Fri Jan  2 18:13:27 2015 : Debug:       secret = "cht1000"
Fri Jan  2 18:13:27 2015 : Debug:       shortname = "TP-Link"
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug: radiusd: #### Instantiating modules ####
Fri Jan  2 18:13:27 2015 : Debug:  instantiate {
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_exec, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_exec
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Fri Jan  2 18:13:27 2015 : Debug:   exec {
Fri Jan  2 18:13:27 2015 : Debug:       wait = no
Fri Jan  2 18:13:27 2015 : Debug:       input_pairs = "request"
Fri Jan  2 18:13:27 2015 : Debug:       shell_escape = yes
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_expr, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_expr
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_expiration
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Fri Jan  2 18:13:27 2015 : Debug:   expiration {
Fri Jan  2 18:13:27 2015 : Debug:       reply-message = "Password Has Expired  "
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_logintime
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Fri Jan  2 18:13:27 2015 : Debug:   logintime {
Fri Jan  2 18:13:27 2015 : Debug:       reply-message = "You are calling outside your allowed timespan  "
Fri Jan  2 18:13:27 2015 : Debug:       minimum-timeout = 60
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:  }
Fri Jan  2 18:13:27 2015 : Debug: radiusd: #### Loading Virtual Servers ####
Fri Jan  2 18:13:27 2015 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Fri Jan  2 18:13:27 2015 : Debug:  modules {
Fri Jan  2 18:13:27 2015 : Debug:  Module: Checking authenticate {...} for more modules to load
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_pap, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_pap
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Fri Jan  2 18:13:27 2015 : Debug:   pap {
Fri Jan  2 18:13:27 2015 : Debug:       encryption_scheme = "auto"
Fri Jan  2 18:13:27 2015 : Debug:       auto_header = no
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_chap, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_chap
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_mschap
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Fri Jan  2 18:13:27 2015 : Debug:   mschap {
Fri Jan  2 18:13:27 2015 : Debug:       use_mppe = yes
Fri Jan  2 18:13:27 2015 : Debug:       require_encryption = no
Fri Jan  2 18:13:27 2015 : Debug:       require_strong = no
Fri Jan  2 18:13:27 2015 : Debug:       with_ntdomain_hack = no
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_unix, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_unix
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Fri Jan  2 18:13:27 2015 : Debug:   unix {
Fri Jan  2 18:13:27 2015 : Debug:       radwtmp = "/var/log/freeradius/radwtmp"
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:     (Loaded rlm_eap, checking if it's valid)
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to module rlm_eap
Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Fri Jan  2 18:13:27 2015 : Debug:   eap {
Fri Jan  2 18:13:27 2015 : Debug:       default_eap_type = "md5"
Fri Jan  2 18:13:27 2015 : Debug:       timer_expire = 60
Fri Jan  2 18:13:27 2015 : Debug:       ignore_unknown_eap_types = no
Fri Jan  2 18:13:27 2015 : Debug:       cisco_accounting_username_bug = no
Fri Jan  2 18:13:27 2015 : Debug:       max_sessions = 4096
Fri Jan  2 18:13:27 2015 : Debug:   }
Fri Jan  2 18:13:27 2015 : Debug:  Module: Linked to sub-module rlm_eap_md5
[I][B]Fri Jan  2 18:13:27 2015 : Debug:  Module: Instantiating eap-md5
Fri Jan  2 18:13:27 2015 : Error: rlm_eap: Unknown EAP type cache
Fri Jan  2 18:13:27 2015 : Error: /etc/freeradius/eap.conf[17]: Instantiation failed for module "eap"
Fri Jan  2 18:13:27 2015 : Error: /etc/freeradius/sites-enabled/inner-tunnel[236]: Failed to load module "eap".
Fri Jan  2 18:13:27 2015 : Error: /etc/freeradius/sites-enabled/inner-tunnel[189]: Errors parsing authenticate section.[/B][/I]

My configuration is the next : 

Freeradius Database : MySQL
2 NIC connected and configured
DHCP service ON and working for eth1.

The access points are configured with WPA2 Enterprise security and i have given the radius server IP with the shared key.

I have already tested the basic configuration of freeradius before testing with EAP-MD5 and it worked. If someone can help me about this... That'll help me a lot :cool:

Thanks in advance :)

---

