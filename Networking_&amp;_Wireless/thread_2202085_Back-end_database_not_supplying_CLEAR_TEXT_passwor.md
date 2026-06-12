---
title: "Back-end database not supplying CLEAR TEXT password"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by okay7675 on 2014-01-27
Hi, 

I have installed a FreeRadius server for use in my Wi-Fi HotSpot, with daloRADIUS as the RADIUS web management application (using CoovaChilli as my captive portal). If i create users using daloRADIUS, authentication fails. FreeRadius debug output:
```
root@ubuntu:~# freeradius -XXX
Mon Jan 27 15:42:50 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Mon Jan 27 15:42:50 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Mon Jan 27 15:42:50 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Mon Jan 27 15:42:50 2014 : Info: PARTICULAR PURPOSE. 
Mon Jan 27 15:42:50 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Mon Jan 27 15:42:50 2014 : Info: GNU General Public License v2. 
Mon Jan 27 15:42:50 2014 : Info: Starting - reading configuration files ...
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Mon Jan 27 15:42:50 2014 : Debug: including files in directory /etc/freeradius/modules/
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/always
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/files
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Mon Jan 27 15:42:50 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Mon Jan 27 15:42:50 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default.backup
Mon Jan 27 15:42:50 2014 : Debug: main {
Mon Jan 27 15:42:50 2014 : Debug:     user = "freerad"
Mon Jan 27 15:42:50 2014 : Debug:     group = "freerad"
Mon Jan 27 15:42:50 2014 : Debug:     allow_core_dumps = no
Mon Jan 27 15:42:50 2014 : Debug: }
Mon Jan 27 15:42:50 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Mon Jan 27 15:42:50 2014 : Debug: main {
Mon Jan 27 15:42:50 2014 : Debug:     prefix = "/usr"
Mon Jan 27 15:42:50 2014 : Debug:     localstatedir = "/var"
Mon Jan 27 15:42:50 2014 : Debug:     logdir = "/var/log/freeradius"
Mon Jan 27 15:42:50 2014 : Debug:     libdir = "/usr/lib/freeradius"
Mon Jan 27 15:42:50 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Mon Jan 27 15:42:50 2014 : Debug:     hostname_lookups = no
Mon Jan 27 15:42:50 2014 : Debug:     max_request_time = 30
Mon Jan 27 15:42:50 2014 : Debug:     cleanup_delay = 5
Mon Jan 27 15:42:50 2014 : Debug:     max_requests = 1024
Mon Jan 27 15:42:50 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Mon Jan 27 15:42:50 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Mon Jan 27 15:42:50 2014 : Debug:     debug_level = 0
Mon Jan 27 15:42:50 2014 : Debug:     proxy_requests = yes
Mon Jan 27 15:42:50 2014 : Debug:  log {
Mon Jan 27 15:42:50 2014 : Debug:     stripped_names = no
Mon Jan 27 15:42:50 2014 : Debug:     auth = no
Mon Jan 27 15:42:50 2014 : Debug:     auth_badpass = no
Mon Jan 27 15:42:50 2014 : Debug:     auth_goodpass = no
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug:  security {
Mon Jan 27 15:42:50 2014 : Debug:     max_attributes = 200
Mon Jan 27 15:42:50 2014 : Debug:     reject_delay = 1
Mon Jan 27 15:42:50 2014 : Debug:     status_server = yes
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug: }
Mon Jan 27 15:42:50 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Mon Jan 27 15:42:50 2014 : Debug:  proxy server {
Mon Jan 27 15:42:50 2014 : Debug:     retry_delay = 5
Mon Jan 27 15:42:50 2014 : Debug:     retry_count = 3
Mon Jan 27 15:42:50 2014 : Debug:     default_fallback = no
Mon Jan 27 15:42:50 2014 : Debug:     dead_time = 120
Mon Jan 27 15:42:50 2014 : Debug:     wake_all_if_all_dead = no
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug:  home_server localhost {
Mon Jan 27 15:42:50 2014 : Debug:     ipaddr = 127.0.0.1
Mon Jan 27 15:42:50 2014 : Debug:     port = 1812
Mon Jan 27 15:42:50 2014 : Debug:     type = "auth"
Mon Jan 27 15:42:50 2014 : Debug:     secret = "testing123"
Mon Jan 27 15:42:50 2014 : Debug:     response_window = 20
Mon Jan 27 15:42:50 2014 : Debug:     max_outstanding = 65536
Mon Jan 27 15:42:50 2014 : Debug:     require_message_authenticator = yes
Mon Jan 27 15:42:50 2014 : Debug:     zombie_period = 40
Mon Jan 27 15:42:50 2014 : Debug:     status_check = "status-server"
Mon Jan 27 15:42:50 2014 : Debug:     ping_interval = 30
Mon Jan 27 15:42:50 2014 : Debug:     check_interval = 30
Mon Jan 27 15:42:50 2014 : Debug:     num_answers_to_alive = 3
Mon Jan 27 15:42:50 2014 : Debug:     num_pings_to_alive = 3
Mon Jan 27 15:42:50 2014 : Debug:     revive_interval = 120
Mon Jan 27 15:42:50 2014 : Debug:     status_check_timeout = 4
Mon Jan 27 15:42:50 2014 : Debug:     irt = 2
Mon Jan 27 15:42:50 2014 : Debug:     mrt = 16
Mon Jan 27 15:42:50 2014 : Debug:     mrc = 5
Mon Jan 27 15:42:50 2014 : Debug:     mrd = 30
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug:  home_server_pool my_auth_failover {
Mon Jan 27 15:42:50 2014 : Debug:     type = fail-over
Mon Jan 27 15:42:50 2014 : Debug:     home_server = localhost
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug:  realm example.com {
Mon Jan 27 15:42:50 2014 : Debug:     auth_pool = my_auth_failover
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug:  realm LOCAL {
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug: radiusd: #### Loading Clients ####
Mon Jan 27 15:42:50 2014 : Debug:  client localhost {
Mon Jan 27 15:42:50 2014 : Debug:     ipaddr = 127.0.0.1
Mon Jan 27 15:42:50 2014 : Debug:     require_message_authenticator = no
Mon Jan 27 15:42:50 2014 : Debug:     secret = "testing123"
Mon Jan 27 15:42:50 2014 : Debug:     nastype = "other"
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug: radiusd: #### Instantiating modules ####
Mon Jan 27 15:42:50 2014 : Debug:  instantiate {
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_exec
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Mon Jan 27 15:42:50 2014 : Debug:   exec {
Mon Jan 27 15:42:50 2014 : Debug:     wait = no
Mon Jan 27 15:42:50 2014 : Debug:     input_pairs = "request"
Mon Jan 27 15:42:50 2014 : Debug:     shell_escape = yes
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Mon Jan 27 15:42:50 2014 : Debug:   sqlcounter chillispot_max_bytes {
Mon Jan 27 15:42:50 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Mon Jan 27 15:42:50 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Mon Jan 27 15:42:50 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Mon Jan 27 15:42:50 2014 : Debug:     key = "User-Name"
Mon Jan 27 15:42:50 2014 : Debug:     sqlmod-inst = "sql"
Mon Jan 27 15:42:50 2014 : Debug:     query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
Mon Jan 27 15:42:50 2014 : Debug:     reset = "never"
Mon Jan 27 15:42:50 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Current Time: 1390830170 [2014-01-27 15:42:50], Next reset 0 [2014-01-27 15:00:00]
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Current Time: 1390830170 [2014-01-27 15:42:50], Prev reset 0 [2014-01-27 15:00:00]
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Mon Jan 27 15:42:50 2014 : Debug:   sqlcounter noresetcounter {
Mon Jan 27 15:42:50 2014 : Debug:     counter-name = "Session-Timeout"
Mon Jan 27 15:42:50 2014 : Debug:     check-name = "Session-Timeout"
Mon Jan 27 15:42:50 2014 : Debug:     reply-name = "Session-Timeout"
Mon Jan 27 15:42:50 2014 : Debug:     key = "User-Name"
Mon Jan 27 15:42:50 2014 : Debug:     sqlmod-inst = "sql"
Mon Jan 27 15:42:50 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Mon Jan 27 15:42:50 2014 : Debug:     reset = "never"
Mon Jan 27 15:42:50 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Current Time: 1390830170 [2014-01-27 15:42:50], Next reset 0 [2014-01-27 15:00:00]
Mon Jan 27 15:42:50 2014 : Debug: rlm_sqlcounter: Current Time: 1390830170 [2014-01-27 15:42:50], Prev reset 0 [2014-01-27 15:00:00]
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_expr
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_expiration
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Mon Jan 27 15:42:50 2014 : Debug:   expiration {
Mon Jan 27 15:42:50 2014 : Debug:     reply-message = "Password Has Expired  "
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_logintime
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Mon Jan 27 15:42:50 2014 : Debug:   logintime {
Mon Jan 27 15:42:50 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Mon Jan 27 15:42:50 2014 : Debug:     minimum-timeout = 60
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:  }
Mon Jan 27 15:42:50 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Mon Jan 27 15:42:50 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Mon Jan 27 15:42:50 2014 : Debug:  modules {
Mon Jan 27 15:42:50 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_pap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Mon Jan 27 15:42:50 2014 : Debug:   pap {
Mon Jan 27 15:42:50 2014 : Debug:     encryption_scheme = "auto"
Mon Jan 27 15:42:50 2014 : Debug:     auto_header = no
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_chap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_mschap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Mon Jan 27 15:42:50 2014 : Debug:   mschap {
Mon Jan 27 15:42:50 2014 : Debug:     use_mppe = yes
Mon Jan 27 15:42:50 2014 : Debug:     require_encryption = no
Mon Jan 27 15:42:50 2014 : Debug:     require_strong = no
Mon Jan 27 15:42:50 2014 : Debug:     with_ntdomain_hack = no
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_unix
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Mon Jan 27 15:42:50 2014 : Debug:   unix {
Mon Jan 27 15:42:50 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to module rlm_eap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Mon Jan 27 15:42:50 2014 : Debug:   eap {
Mon Jan 27 15:42:50 2014 : Debug:     default_eap_type = "md5"
Mon Jan 27 15:42:50 2014 : Debug:     timer_expire = 60
Mon Jan 27 15:42:50 2014 : Debug:     ignore_unknown_eap_types = no
Mon Jan 27 15:42:50 2014 : Debug:     cisco_accounting_username_bug = no
Mon Jan 27 15:42:50 2014 : Debug:     max_sessions = 4096
Mon Jan 27 15:42:50 2014 : Debug:   }
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating eap-md5
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating eap-leap
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating eap-gtc
Mon Jan 27 15:42:50 2014 : Debug:    gtc {
Mon Jan 27 15:42:50 2014 : Debug:     challenge = "Password: "
Mon Jan 27 15:42:50 2014 : Debug:     auth_type = "PAP"
Mon Jan 27 15:42:50 2014 : Debug:    }
Mon Jan 27 15:42:50 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Mon Jan 27 15:42:50 2014 : Debug:  Module: Instantiating eap-tls
Mon Jan 27 15:42:50 2014 : Debug:    tls {
Mon Jan 27 15:42:50 2014 : Debug:     rsa_key_exchange = no
Mon Jan 27 15:42:50 2014 : Debug:     dh_key_exchange = yes
Mon Jan 27 15:42:50 2014 : Debug:     rsa_key_length = 512
Mon Jan 27 15:42:50 2014 : Debug:     dh_key_length = 512
Mon Jan 27 15:42:50 2014 : Debug:     verify_depth = 0
Mon Jan 27 15:42:50 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Mon Jan 27 15:42:50 2014 : Debug:     pem_file_type = yes
Mon Jan 27 15:42:50 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Mon Jan 27 15:42:50 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Mon Jan 27 15:42:50 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Mon Jan 27 15:42:50 2014 : Debug:     private_key_password = "whatever"
Mon Jan 27 15:42:50 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Mon Jan 27 15:42:50 2014 : Debug:     random_file = "/dev/urandom"
Mon Jan 27 15:42:50 2014 : Debug:     fragment_size = 1024
Mon Jan 27 15:42:50 2014 : Debug:     include_length = yes
Mon Jan 27 15:42:50 2014 : Debug:     check_crl = no
Mon Jan 27 15:42:50 2014 : Debug:     cipher_list = "DEFAULT"
Mon Jan 27 15:42:50 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Mon Jan 27 15:42:50 2014 : Debug:     cache {
Mon Jan 27 15:42:50 2014 : Debug:     enable = no
Mon Jan 27 15:42:50 2014 : Debug:     lifetime = 24
Mon Jan 27 15:42:50 2014 : Debug:     max_entries = 255
Mon Jan 27 15:42:50 2014 : Debug:     }
Mon Jan 27 15:42:50 2014 : Debug:     verify {
Mon Jan 27 15:42:50 2014 : Debug:     }
Mon Jan 27 15:42:50 2014 : Debug:    }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating eap-ttls
Mon Jan 27 15:42:51 2014 : Debug:    ttls {
Mon Jan 27 15:42:51 2014 : Debug:     default_eap_type = "md5"
Mon Jan 27 15:42:51 2014 : Debug:     copy_request_to_tunnel = no
Mon Jan 27 15:42:51 2014 : Debug:     use_tunneled_reply = no
Mon Jan 27 15:42:51 2014 : Debug:     virtual_server = "inner-tunnel"
Mon Jan 27 15:42:51 2014 : Debug:     include_length = yes
Mon Jan 27 15:42:51 2014 : Debug:    }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating eap-peap
Mon Jan 27 15:42:51 2014 : Debug:    peap {
Mon Jan 27 15:42:51 2014 : Debug:     default_eap_type = "mschapv2"
Mon Jan 27 15:42:51 2014 : Debug:     copy_request_to_tunnel = no
Mon Jan 27 15:42:51 2014 : Debug:     use_tunneled_reply = no
Mon Jan 27 15:42:51 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Mon Jan 27 15:42:51 2014 : Debug:     virtual_server = "inner-tunnel"
Mon Jan 27 15:42:51 2014 : Debug:    }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating eap-mschapv2
Mon Jan 27 15:42:51 2014 : Debug:    mschapv2 {
Mon Jan 27 15:42:51 2014 : Debug:     with_ntdomain_hack = no
Mon Jan 27 15:42:51 2014 : Debug:    }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_realm
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Mon Jan 27 15:42:51 2014 : Debug:   realm suffix {
Mon Jan 27 15:42:51 2014 : Debug:     format = "suffix"
Mon Jan 27 15:42:51 2014 : Debug:     delimiter = "@"
Mon Jan 27 15:42:51 2014 : Debug:     ignore_default = no
Mon Jan 27 15:42:51 2014 : Debug:     ignore_null = no
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_files
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Mon Jan 27 15:42:51 2014 : Debug:   files {
Mon Jan 27 15:42:51 2014 : Debug:     usersfile = "/etc/freeradius/users"
Mon Jan 27 15:42:51 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Mon Jan 27 15:42:51 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Mon Jan 27 15:42:51 2014 : Debug:     compat = "no"
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking session {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_radutmp
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Mon Jan 27 15:42:51 2014 : Debug:   radutmp {
Mon Jan 27 15:42:51 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Mon Jan 27 15:42:51 2014 : Debug:     username = "%{User-Name}"
Mon Jan 27 15:42:51 2014 : Debug:     case_sensitive = yes
Mon Jan 27 15:42:51 2014 : Debug:     check_with_nas = yes
Mon Jan 27 15:42:51 2014 : Debug:     perm = 384
Mon Jan 27 15:42:51 2014 : Debug:     callerid = yes
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_attr_filter
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Mon Jan 27 15:42:51 2014 : Debug:   attr_filter attr_filter.access_reject {
Mon Jan 27 15:42:51 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Mon Jan 27 15:42:51 2014 : Debug:     key = "%{User-Name}"
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  } # modules
Mon Jan 27 15:42:51 2014 : Debug: } # server
Mon Jan 27 15:42:51 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Mon Jan 27 15:42:51 2014 : Debug:  modules {
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_digest
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_preprocess
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Mon Jan 27 15:42:51 2014 : Debug:   preprocess {
Mon Jan 27 15:42:51 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Mon Jan 27 15:42:51 2014 : Debug:     hints = "/etc/freeradius/hints"
Mon Jan 27 15:42:51 2014 : Debug:     with_ascend_hack = no
Mon Jan 27 15:42:51 2014 : Debug:     ascend_channels_per_line = 23
Mon Jan 27 15:42:51 2014 : Debug:     with_ntdomain_hack = no
Mon Jan 27 15:42:51 2014 : Debug:     with_specialix_jetstream_hack = no
Mon Jan 27 15:42:51 2014 : Debug:     with_cisco_vsa_hack = no
Mon Jan 27 15:42:51 2014 : Debug:     with_alvarion_vsa_hack = no
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_sql
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Mon Jan 27 15:42:51 2014 : Debug:   sql {
Mon Jan 27 15:42:51 2014 : Debug:     driver = "rlm_sql_mysql"
Mon Jan 27 15:42:51 2014 : Debug:     server = "localhost"
Mon Jan 27 15:42:51 2014 : Debug:     port = ""
Mon Jan 27 15:42:51 2014 : Debug:     login = "radius"
Mon Jan 27 15:42:51 2014 : Debug:     password = "radpass"
Mon Jan 27 15:42:51 2014 : Debug:     radius_db = "radius"
Mon Jan 27 15:42:51 2014 : Debug:     read_groups = yes
Mon Jan 27 15:42:51 2014 : Debug:     sqltrace = no
Mon Jan 27 15:42:51 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Mon Jan 27 15:42:51 2014 : Debug:     readclients = no
Mon Jan 27 15:42:51 2014 : Debug:     deletestalesessions = yes
Mon Jan 27 15:42:51 2014 : Debug:     num_sql_socks = 5
Mon Jan 27 15:42:51 2014 : Debug:     lifetime = 0
Mon Jan 27 15:42:51 2014 : Debug:     max_queries = 0
Mon Jan 27 15:42:51 2014 : Debug:     sql_user_name = "%{User-Name}"
Mon Jan 27 15:42:51 2014 : Debug:     default_user_profile = ""
Mon Jan 27 15:42:51 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Mon Jan 27 15:42:51 2014 : Debug:     authorize_check_query = "SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Mon Jan 27 15:42:51 2014 : Debug:     authorize_reply_query = "SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Mon Jan 27 15:42:51 2014 : Debug:     authorize_group_check_query = "SELECT id, groupname, attribute,           Value, op           FROM radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Mon Jan 27 15:42:51 2014 : Debug:     authorize_group_reply_query = "SELECT id, groupname, attribute,           value, op           FROM radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_onoff_query = "          UPDATE radacct           SET              acctstoptime       =  '%S',              acctsessiontime    =  unix_timestamp('%S') -                                    unix_timestamp(acctstarttime),              acctterminatecause =  '%{Acct-Terminate-Cause}',              acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE acctstoptime IS NULL           AND nasipaddress      =  '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_update_query = "           UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_update_query_alt = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,      nasportid,              nasporttype,      acctstarttime,     acctsessiontime,              acctauthentic,    connectinfo_start, acctinputoctets,              acctoutputoctets, calledstationid,   callingstationid,              servicetype,      framedprotocol,    framedipaddress,              acctstartdelay,   xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                       INTERVAL (%{%{Acct-Session-Time}:-0} +                                 %{%{Acct-Delay-Time}:-0}) SECOND),                       '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Service-Type}', '%{Framed-Protocol}',              '%{Framed-IP-Address}',              '0', '%{X-Ascend-Session-Svr-Key}')"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_start_query = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,     username,              realm,            nasipaddress,     nasportid,              nasporttype,      acctstarttime,    acctstoptime,              acctsessiontime,  acctauthentic,    connectinfo_start,              connectinfo_stop, acctinputoctets,  acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,      framedprotocol,   framedipaddress,              acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}', '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',              '', '0', '0',              '%{Called-Station-Id}', '%{Calling-Station-Id}', '',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_start_query_alt = "           UPDATE radacct SET              acctstarttime     = '%S',              acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',              connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'           AND nasipaddress     = '%{NAS-IP-Address}'"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_stop_query = "           UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}'"
Mon Jan 27 15:42:51 2014 : Debug:     accounting_stop_query_alt = "           INSERT INTO radacct             (acctsessionid, acctuniqueid, username,              realm, nasipaddress, nasportid,              nasporttype, acctstarttime, acctstoptime,              acctsessiontime, acctauthentic, connectinfo_start,              connectinfo_stop, acctinputoctets, acctoutputoctets,              calledstationid, callingstationid, acctterminatecause,              servicetype, framedprotocol, framedipaddress,              acctstartdelay, acctstopdelay)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                  INTERVAL (%{%{Acct-Session-Time}:-0} +                  %{%{Acct-Delay-Time}:-0}) SECOND),              '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '',              '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '0', '%{%{Acct-Delay-Time}:-0}')"
Mon Jan 27 15:42:51 2014 : Debug:     group_membership_query = "SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority"
Mon Jan 27 15:42:51 2014 : Debug:     connect_failure_retry_delay = 60
Mon Jan 27 15:42:51 2014 : Debug:     simul_count_query = ""
Mon Jan 27 15:42:51 2014 : Debug:     simul_verify_query = "SELECT radacctid, acctsessionid, username,                                nasipaddress, nasportid, framedipaddress,                                callingstationid, framedprotocol                                FROM radacct                                WHERE username = '%{SQL-User-Name}'                                AND acctstoptime IS NULL"
Mon Jan 27 15:42:51 2014 : Debug:     postauth_query = "INSERT INTO radpostauth                           (username, pass, reply, authdate)                           VALUES (                           '%{User-Name}',                           '%{%{User-Password}:-%{Chap-Password}}',                           '%{reply:Packet-Type}', '%S')"
Mon Jan 27 15:42:51 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Mon Jan 27 15:42:51 2014 : Debug: rlm_sql (sql): starting 0
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Mon Jan 27 15:42:51 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Mon Jan 27 15:42:51 2014 : Debug: rlm_sql (sql): starting 1
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Mon Jan 27 15:42:51 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Mon Jan 27 15:42:51 2014 : Debug: rlm_sql (sql): starting 2
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Mon Jan 27 15:42:51 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Mon Jan 27 15:42:51 2014 : Debug: rlm_sql (sql): starting 3
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Mon Jan 27 15:42:51 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Mon Jan 27 15:42:51 2014 : Debug: rlm_sql (sql): starting 4
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Mon Jan 27 15:42:51 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Mon Jan 27 15:42:51 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_acct_unique
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Mon Jan 27 15:42:51 2014 : Debug:   acct_unique {
Mon Jan 27 15:42:51 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Mon Jan 27 15:42:51 2014 : Debug:  Module: Linked to module rlm_detail
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Mon Jan 27 15:42:51 2014 : Debug:   detail {
Mon Jan 27 15:42:51 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Mon Jan 27 15:42:51 2014 : Debug:     header = "%t"
Mon Jan 27 15:42:51 2014 : Debug:     detailperm = 384
Mon Jan 27 15:42:51 2014 : Debug:     dirperm = 493
Mon Jan 27 15:42:51 2014 : Debug:     locking = no
Mon Jan 27 15:42:51 2014 : Debug:     log_packet_header = no
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Mon Jan 27 15:42:51 2014 : Debug:   attr_filter attr_filter.accounting_response {
Mon Jan 27 15:42:51 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Mon Jan 27 15:42:51 2014 : Debug:     key = "%{User-Name}"
Mon Jan 27 15:42:51 2014 : Debug:   }
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking session {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Mon Jan 27 15:42:51 2014 : Debug:  } # modules
Mon Jan 27 15:42:51 2014 : Debug: } # server
Mon Jan 27 15:42:51 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Mon Jan 27 15:42:51 2014 : Debug: listen {
Mon Jan 27 15:42:51 2014 : Debug:     type = "auth"
Mon Jan 27 15:42:51 2014 : Debug:     ipaddr = *
Mon Jan 27 15:42:51 2014 : Debug:     port = 0
Mon Jan 27 15:42:51 2014 : Debug: }
Mon Jan 27 15:42:51 2014 : Debug: listen {
Mon Jan 27 15:42:51 2014 : Debug:     type = "acct"
Mon Jan 27 15:42:51 2014 : Debug:     ipaddr = *
Mon Jan 27 15:42:51 2014 : Debug:     port = 0
Mon Jan 27 15:42:51 2014 : Debug: }
Mon Jan 27 15:42:51 2014 : Debug: listen {
Mon Jan 27 15:42:51 2014 : Debug:     type = "auth"
Mon Jan 27 15:42:51 2014 : Debug:     ipaddr = 127.0.0.1
Mon Jan 27 15:42:51 2014 : Debug:     port = 18120
Mon Jan 27 15:42:51 2014 : Debug: }
Mon Jan 27 15:42:51 2014 : Debug: Listening on authentication address * port 1812
Mon Jan 27 15:42:51 2014 : Debug: Listening on accounting address * port 1813
Mon Jan 27 15:42:51 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Mon Jan 27 15:42:51 2014 : Debug: Listening on proxy address * port 1814
Mon Jan 27 15:42:51 2014 : Info: Ready to process requests.
rad_recv: Accounting-Request packet from host 127.0.0.1 port 33674, id=5, length=261
    ChilliSpot-Version = "1.2.9"
    ChilliSpot-Attr-10 = 0x00000002
    Event-Timestamp = "Jan 27 2014 15:43:40 CAT"
    User-Name = "randtest"
    Acct-Input-Octets = 101190
    Acct-Output-Octets = 72181
    Acct-Input-Gigawords = 0
    Acct-Output-Gigawords = 0
    Acct-Input-Packets = 504
    Acct-Output-Packets = 595
    Acct-Session-Time = 1202
    Acct-Status-Type = Interim-Update
    Acct-Session-Id = "52e65dc500000001"
    Framed-IP-Address = 10.1.0.2
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 1
    NAS-Port-Id = "00000001"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
Mon Jan 27 15:43:40 2014 : Info: # Executing section preacct from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:43:40 2014 : Info: +- entering group preacct {...}
Mon Jan 27 15:43:40 2014 : Info: ++[preprocess] returns ok
Mon Jan 27 15:43:40 2014 : Info: [acct_unique] Hashing 'NAS-Port = 1,Client-IP-Address = 127.0.0.1,NAS-IP-Address = 10.1.0.1,Acct-Session-Id = "52e65dc500000001",User-Name = "randtest"'
Mon Jan 27 15:43:40 2014 : Info: [acct_unique] Acct-Unique-Session-ID = "81fe01187a0dd1af".
Mon Jan 27 15:43:40 2014 : Info: ++[acct_unique] returns ok
Mon Jan 27 15:43:40 2014 : Info: [suffix] No '@' in User-Name = "randtest", looking up realm NULL
Mon Jan 27 15:43:40 2014 : Info: [suffix] No such realm "NULL"
Mon Jan 27 15:43:40 2014 : Info: ++[suffix] returns noop
Mon Jan 27 15:43:40 2014 : Info: ++[files] returns noop
Mon Jan 27 15:43:40 2014 : Info: # Executing section accounting from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:43:40 2014 : Info: +- entering group accounting {...}
Mon Jan 27 15:43:40 2014 : Info: [detail]     expand: /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d -> /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:43:40 2014 : Info: [detail] /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d expands to /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:43:40 2014 : Info: [detail]     expand: %t -> Mon Jan 27 15:43:40 2014
Mon Jan 27 15:43:40 2014 : Info: ++[detail] returns ok
Mon Jan 27 15:43:40 2014 : Info: ++[unix] returns noop
Mon Jan 27 15:43:40 2014 : Info: [radutmp]     expand: /var/log/freeradius/radutmp -> /var/log/freeradius/radutmp
Mon Jan 27 15:43:40 2014 : Info: [radutmp]     expand: %{User-Name} -> randtest
Mon Jan 27 15:43:40 2014 : Info: ++[radutmp] returns ok
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand: %{User-Name} -> randtest
Mon Jan 27 15:43:40 2014 : Info: [sql] sql_set_user escaped user --> 'randtest'
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand: %{Acct-Input-Gigawords} -> 0
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand: %{Acct-Input-Octets} -> 101190
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand: %{Acct-Output-Gigawords} -> 0
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand: %{Acct-Output-Octets} -> 72181
Mon Jan 27 15:43:40 2014 : Info: [sql]     expand:            UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}' ->            UPDATE radacct           SET              framedipaddress = '10.1.0.2',              acctsessiontime     = '1202',              acctinputoctets     = '0'  << 32 |                                    '101190',              acctoutputoctets    = '0' << 32 |                                    '72181'           WHERE acctsessionid = '52e65dc500000001'           AND username        = 'randtest'           
Mon Jan 27 15:43:40 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 4
Mon Jan 27 15:43:40 2014 : Debug: rlm_sql (sql): Released sql socket id: 4
Mon Jan 27 15:43:40 2014 : Info: ++[sql] returns ok
Mon Jan 27 15:43:40 2014 : Info: ++[exec] returns noop
Mon Jan 27 15:43:40 2014 : Info: [attr_filter.accounting_response]     expand: %{User-Name} -> randtest
Mon Jan 27 15:43:40 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 12
Mon Jan 27 15:43:40 2014 : Info: ++[attr_filter.accounting_response] returns updated
Sending Accounting-Response of id 5 to 127.0.0.1 port 33674
Mon Jan 27 15:43:40 2014 : Info: Finished request 0.
Mon Jan 27 15:43:40 2014 : Info: Cleaning up request 0 ID 5 with timestamp +49
Mon Jan 27 15:43:40 2014 : Debug: Going to the next request
Mon Jan 27 15:43:40 2014 : Info: Ready to process requests.
rad_recv: Accounting-Request packet from host 127.0.0.1 port 33674, id=6, length=261
    ChilliSpot-Version = "1.2.9"
    ChilliSpot-Attr-10 = 0x00000002
    Event-Timestamp = "Jan 27 2014 15:48:40 CAT"
    User-Name = "randtest"
    Acct-Input-Octets = 210171
    Acct-Output-Octets = 95473
    Acct-Input-Gigawords = 0
    Acct-Output-Gigawords = 0
    Acct-Input-Packets = 655
    Acct-Output-Packets = 944
    Acct-Session-Time = 1502
    Acct-Status-Type = Interim-Update
    Acct-Session-Id = "52e65dc500000001"
    Framed-IP-Address = 10.1.0.2
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 1
    NAS-Port-Id = "00000001"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
Mon Jan 27 15:48:41 2014 : Info: # Executing section preacct from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:48:41 2014 : Info: +- entering group preacct {...}
Mon Jan 27 15:48:41 2014 : Info: ++[preprocess] returns ok
Mon Jan 27 15:48:41 2014 : Info: [acct_unique] Hashing 'NAS-Port = 1,Client-IP-Address = 127.0.0.1,NAS-IP-Address = 10.1.0.1,Acct-Session-Id = "52e65dc500000001",User-Name = "randtest"'
Mon Jan 27 15:48:41 2014 : Info: [acct_unique] Acct-Unique-Session-ID = "81fe01187a0dd1af".
Mon Jan 27 15:48:41 2014 : Info: ++[acct_unique] returns ok
Mon Jan 27 15:48:41 2014 : Info: [suffix] No '@' in User-Name = "randtest", looking up realm NULL
Mon Jan 27 15:48:41 2014 : Info: [suffix] No such realm "NULL"
Mon Jan 27 15:48:41 2014 : Info: ++[suffix] returns noop
Mon Jan 27 15:48:41 2014 : Info: ++[files] returns noop
Mon Jan 27 15:48:41 2014 : Info: # Executing section accounting from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:48:41 2014 : Info: +- entering group accounting {...}
Mon Jan 27 15:48:41 2014 : Info: [detail]     expand: /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d -> /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:48:41 2014 : Info: [detail] /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d expands to /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:48:41 2014 : Info: [detail]     expand: %t -> Mon Jan 27 15:48:41 2014
Mon Jan 27 15:48:41 2014 : Info: ++[detail] returns ok
Mon Jan 27 15:48:41 2014 : Info: ++[unix] returns noop
Mon Jan 27 15:48:41 2014 : Info: [radutmp]     expand: /var/log/freeradius/radutmp -> /var/log/freeradius/radutmp
Mon Jan 27 15:48:41 2014 : Info: [radutmp]     expand: %{User-Name} -> randtest
Mon Jan 27 15:48:41 2014 : Info: ++[radutmp] returns ok
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand: %{User-Name} -> randtest
Mon Jan 27 15:48:41 2014 : Info: [sql] sql_set_user escaped user --> 'randtest'
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand: %{Acct-Input-Gigawords} -> 0
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand: %{Acct-Input-Octets} -> 210171
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand: %{Acct-Output-Gigawords} -> 0
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand: %{Acct-Output-Octets} -> 95473
Mon Jan 27 15:48:41 2014 : Info: [sql]     expand:            UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}' ->            UPDATE radacct           SET              framedipaddress = '10.1.0.2',              acctsessiontime     = '1502',              acctinputoctets     = '0'  << 32 |                                    '210171',              acctoutputoctets    = '0' << 32 |                                    '95473'           WHERE acctsessionid = '52e65dc500000001'           AND username        = 'randtest'           
Mon Jan 27 15:48:41 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 3
Mon Jan 27 15:48:41 2014 : Debug: rlm_sql (sql): Released sql socket id: 3
Mon Jan 27 15:48:41 2014 : Info: ++[sql] returns ok
Mon Jan 27 15:48:41 2014 : Info: ++[exec] returns noop
Mon Jan 27 15:48:41 2014 : Info: [attr_filter.accounting_response]     expand: %{User-Name} -> randtest
Mon Jan 27 15:48:41 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 12
Mon Jan 27 15:48:41 2014 : Info: ++[attr_filter.accounting_response] returns updated
Sending Accounting-Response of id 6 to 127.0.0.1 port 33674
Mon Jan 27 15:48:41 2014 : Info: Finished request 1.
Mon Jan 27 15:48:41 2014 : Info: Cleaning up request 1 ID 6 with timestamp +350
Mon Jan 27 15:48:41 2014 : Debug: Going to the next request
Mon Jan 27 15:48:41 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 35409, id=193, length=48
    User-Name = "omniMibN"
    User-Password = "YM8P"
Mon Jan 27 15:48:49 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:48:49 2014 : Info: +- entering group authorize {...}
Mon Jan 27 15:48:49 2014 : Info: ++[preprocess] returns ok
Mon Jan 27 15:48:49 2014 : Info: ++[chap] returns noop
Mon Jan 27 15:48:49 2014 : Info: ++[mschap] returns noop
Mon Jan 27 15:48:49 2014 : Info: ++[digest] returns noop
Mon Jan 27 15:48:49 2014 : Info: [suffix] No '@' in User-Name = "omniMibN", looking up realm NULL
Mon Jan 27 15:48:49 2014 : Info: [suffix] No such realm "NULL"
Mon Jan 27 15:48:49 2014 : Info: ++[suffix] returns noop
Mon Jan 27 15:48:49 2014 : Info: [eap] No EAP-Message, not doing EAP
Mon Jan 27 15:48:49 2014 : Info: ++[eap] returns noop
Mon Jan 27 15:48:49 2014 : Info: [sql]     expand: %{User-Name} -> omniMibN
Mon Jan 27 15:48:49 2014 : Info: [sql] sql_set_user escaped user --> 'omniMibN'
Mon Jan 27 15:48:49 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 2
Mon Jan 27 15:48:49 2014 : Info: [sql]     expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'omniMibN'           ORDER BY id
Mon Jan 27 15:48:49 2014 : Info: [sql]     expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'omniMibN'           ORDER BY priority
Mon Jan 27 15:48:49 2014 : Debug: rlm_sql (sql): Released sql socket id: 2
Mon Jan 27 15:48:49 2014 : Info: [sql] User omniMibN not found
Mon Jan 27 15:48:49 2014 : Info: ++[sql] returns notfound
Mon Jan 27 15:48:49 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Mon Jan 27 15:48:49 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Mon Jan 27 15:48:49 2014 : Info: ++[chillispot_max_bytes] returns noop
Mon Jan 27 15:48:49 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Mon Jan 27 15:48:49 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Mon Jan 27 15:48:49 2014 : Info: ++[noresetcounter] returns noop
Mon Jan 27 15:48:49 2014 : Info: ++[expiration] returns noop
Mon Jan 27 15:48:49 2014 : Info: ++[logintime] returns noop
Mon Jan 27 15:48:49 2014 : Info: [pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
Mon Jan 27 15:48:49 2014 : Info: ++[pap] returns noop
Mon Jan 27 15:48:49 2014 : Info: ERROR: No authenticate method (Auth-Type) found for the request: Rejecting the user
Mon Jan 27 15:48:49 2014 : Info: Failed to authenticate the user.
Mon Jan 27 15:48:49 2014 : Info: Using Post-Auth-Type Reject
Mon Jan 27 15:48:49 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:48:49 2014 : Info: +- entering group REJECT {...}
Mon Jan 27 15:48:49 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniMibN
Mon Jan 27 15:48:49 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Mon Jan 27 15:48:49 2014 : Info: ++[attr_filter.access_reject] returns updated
Mon Jan 27 15:48:49 2014 : Info: Delaying reject of request 2 for 1 seconds
Mon Jan 27 15:48:49 2014 : Debug: Going to the next request
Mon Jan 27 15:48:49 2014 : Debug: Waking up in 0.9 seconds.
Mon Jan 27 15:48:50 2014 : Info: Sending delayed reject for request 2
Sending Access-Reject of id 193 to 127.0.0.1 port 35409
Mon Jan 27 15:48:50 2014 : Debug: Waking up in 4.9 seconds.
Mon Jan 27 15:48:55 2014 : Info: Cleaning up request 2 ID 193 with timestamp +358
Mon Jan 27 15:48:55 2014 : Info: Ready to process requests.
rad_recv: Accounting-Request packet from host 127.0.0.1 port 33674, id=7, length=267
    ChilliSpot-Version = "1.2.9"
    ChilliSpot-Attr-10 = 0x00000002
    Event-Timestamp = "Jan 27 2014 15:51:00 CAT"
    User-Name = "randtest"
    Acct-Input-Octets = 602206
    Acct-Output-Octets = 131120
    Acct-Input-Gigawords = 0
    Acct-Output-Gigawords = 0
    Acct-Input-Packets = 999
    Acct-Output-Packets = 1465
    Acct-Session-Time = 1642
    Acct-Terminate-Cause = User-Request
    Acct-Status-Type = Stop
    Acct-Session-Id = "52e65dc500000001"
    Framed-IP-Address = 10.1.0.2
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 1
    NAS-Port-Id = "00000001"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
Mon Jan 27 15:51:01 2014 : Info: # Executing section preacct from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:01 2014 : Info: +- entering group preacct {...}
Mon Jan 27 15:51:01 2014 : Info: ++[preprocess] returns ok
Mon Jan 27 15:51:01 2014 : Info: [acct_unique] Hashing 'NAS-Port = 1,Client-IP-Address = 127.0.0.1,NAS-IP-Address = 10.1.0.1,Acct-Session-Id = "52e65dc500000001",User-Name = "randtest"'
Mon Jan 27 15:51:01 2014 : Info: [acct_unique] Acct-Unique-Session-ID = "81fe01187a0dd1af".
Mon Jan 27 15:51:01 2014 : Info: ++[acct_unique] returns ok
Mon Jan 27 15:51:01 2014 : Info: [suffix] No '@' in User-Name = "randtest", looking up realm NULL
Mon Jan 27 15:51:01 2014 : Info: [suffix] No such realm "NULL"
Mon Jan 27 15:51:01 2014 : Info: ++[suffix] returns noop
Mon Jan 27 15:51:01 2014 : Info: ++[files] returns noop
Mon Jan 27 15:51:01 2014 : Info: # Executing section accounting from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:01 2014 : Info: +- entering group accounting {...}
Mon Jan 27 15:51:01 2014 : Info: [detail]     expand: /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d -> /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:51:01 2014 : Info: [detail] /var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d expands to /var/log/freeradius/radacct/127.0.0.1/detail-20140127
Mon Jan 27 15:51:01 2014 : Info: [detail]     expand: %t -> Mon Jan 27 15:51:01 2014
Mon Jan 27 15:51:01 2014 : Info: ++[detail] returns ok
Mon Jan 27 15:51:01 2014 : Info: ++[unix] returns ok
Mon Jan 27 15:51:01 2014 : Info: [radutmp]     expand: /var/log/freeradius/radutmp -> /var/log/freeradius/radutmp
Mon Jan 27 15:51:01 2014 : Info: [radutmp]     expand: %{User-Name} -> randtest
Mon Jan 27 15:51:01 2014 : Info: ++[radutmp] returns ok
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{User-Name} -> randtest
Mon Jan 27 15:51:01 2014 : Info: [sql] sql_set_user escaped user --> 'randtest'
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{Acct-Input-Gigawords} -> 0
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{Acct-Input-Octets} -> 602206
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{Acct-Output-Gigawords} -> 0
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{Acct-Output-Octets} -> 131120
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand: %{Acct-Delay-Time} -> 
Mon Jan 27 15:51:01 2014 : Info: [sql]     ... expanding second conditional
Mon Jan 27 15:51:01 2014 : Info: [sql]     expand:            UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}' ->            UPDATE radacct SET              acctstoptime       = '2014-01-27 15:51:01',              acctsessiontime    = '1642',              acctinputoctets    = '0' << 32 |                                   '602206',              acctoutputoctets   = '0' << 32
Mon Jan 27 15:51:01 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 1
Mon Jan 27 15:51:01 2014 : Debug: rlm_sql (sql): Released sql socket id: 1
Mon Jan 27 15:51:01 2014 : Info: ++[sql] returns ok
Mon Jan 27 15:51:01 2014 : Info: ++[exec] returns noop
Mon Jan 27 15:51:01 2014 : Info: [attr_filter.accounting_response]     expand: %{User-Name} -> randtest
Mon Jan 27 15:51:01 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 12
Mon Jan 27 15:51:01 2014 : Info: ++[attr_filter.accounting_response] returns updated
Sending Accounting-Response of id 7 to 127.0.0.1 port 33674
Mon Jan 27 15:51:01 2014 : Info: Finished request 3.
Mon Jan 27 15:51:01 2014 : Info: Cleaning up request 3 ID 7 with timestamp +490
Mon Jan 27 15:51:01 2014 : Debug: Going to the next request
Mon Jan 27 15:51:01 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 59296, id=123, length=291
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniDBKA"
    CHAP-Challenge = 0x3e5ce86d37aa65d48e51a996e9aa8198
    CHAP-Password = 0x005644de6c70279413bac9f04d62813cf1
    Service-Type = Login-User
    Acct-Session-Id = "52e6644500000001"
    Framed-IP-Address = 10.1.0.2
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 1
    NAS-Port-Id = "00000001"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xafd9809f8f922d5309dd62f3ba825bf3
Mon Jan 27 15:51:31 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:31 2014 : Info: +- entering group authorize {...}
Mon Jan 27 15:51:31 2014 : Info: ++[preprocess] returns ok
Mon Jan 27 15:51:31 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Mon Jan 27 15:51:31 2014 : Info: ++[chap] returns ok
Mon Jan 27 15:51:31 2014 : Info: ++[mschap] returns noop
Mon Jan 27 15:51:31 2014 : Info: ++[digest] returns noop
Mon Jan 27 15:51:31 2014 : Info: [suffix] No '@' in User-Name = "omniDBKA", looking up realm NULL
Mon Jan 27 15:51:31 2014 : Info: [suffix] No such realm "NULL"
Mon Jan 27 15:51:31 2014 : Info: ++[suffix] returns noop
Mon Jan 27 15:51:31 2014 : Info: [eap] No EAP-Message, not doing EAP
Mon Jan 27 15:51:31 2014 : Info: ++[eap] returns noop
Mon Jan 27 15:51:31 2014 : Info: [sql]     expand: %{User-Name} -> omniDBKA
Mon Jan 27 15:51:31 2014 : Info: [sql] sql_set_user escaped user --> 'omniDBKA'
Mon Jan 27 15:51:31 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 0
Mon Jan 27 15:51:31 2014 : Info: [sql]     expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'omniDBKA'           ORDER BY id
Mon Jan 27 15:51:31 2014 : Info: [sql]     expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'omniDBKA'           ORDER BY priority
Mon Jan 27 15:51:31 2014 : Debug: rlm_sql (sql): Released sql socket id: 0
Mon Jan 27 15:51:31 2014 : Info: [sql] User omniDBKA not found
Mon Jan 27 15:51:31 2014 : Info: ++[sql] returns notfound
Mon Jan 27 15:51:31 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Mon Jan 27 15:51:31 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Mon Jan 27 15:51:31 2014 : Info: ++[chillispot_max_bytes] returns noop
Mon Jan 27 15:51:31 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Mon Jan 27 15:51:31 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Mon Jan 27 15:51:31 2014 : Info: ++[noresetcounter] returns noop
Mon Jan 27 15:51:31 2014 : Info: ++[expiration] returns noop
Mon Jan 27 15:51:31 2014 : Info: ++[logintime] returns noop
Mon Jan 27 15:51:31 2014 : Info: [pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
Mon Jan 27 15:51:31 2014 : Info: ++[pap] returns noop
Mon Jan 27 15:51:31 2014 : Info: Found Auth-Type = CHAP
Mon Jan 27 15:51:31 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:31 2014 : Info: +- entering group CHAP {...}
Mon Jan 27 15:51:31 2014 : Info: [chap] login attempt by "omniDBKA" with CHAP password
Mon Jan 27 15:51:31 2014 : Info: [chap] Cleartext-Password is required for authentication
Mon Jan 27 15:51:31 2014 : Info: ++[chap] returns invalid
Mon Jan 27 15:51:31 2014 : Info: Failed to authenticate the user.
Mon Jan 27 15:51:31 2014 : Info: Using Post-Auth-Type Reject
Mon Jan 27 15:51:31 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:31 2014 : Info: +- entering group REJECT {...}
Mon Jan 27 15:51:31 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniDBKA
Mon Jan 27 15:51:31 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Mon Jan 27 15:51:31 2014 : Info: ++[attr_filter.access_reject] returns updated
Mon Jan 27 15:51:31 2014 : Info: Delaying reject of request 4 for 1 seconds
Mon Jan 27 15:51:31 2014 : Debug: Going to the next request
Mon Jan 27 15:51:31 2014 : Debug: Waking up in 0.9 seconds.
Mon Jan 27 15:51:32 2014 : Info: Sending delayed reject for request 4
Sending Access-Reject of id 123 to 127.0.0.1 port 59296
Mon Jan 27 15:51:32 2014 : Debug: Waking up in 4.9 seconds.
Mon Jan 27 15:51:37 2014 : Info: Cleaning up request 4 ID 123 with timestamp +520
Mon Jan 27 15:51:37 2014 : Info: Ready to process requests. 
```
This section of the debug output seems to be the problem 
```
Mon Jan 27 15:51:31 2014 : Info: Found Auth-Type = CHAP
Mon Jan 27 15:51:31 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Mon Jan 27 15:51:31 2014 : Info: +- entering group CHAP {...}
Mon Jan 27 15:51:31 2014 : Info: [chap] login attempt by "omniDBKA" with CHAP password
Mon Jan 27 15:51:31 2014 : Info: [chap] Cleartext-Password is required for authentication
Mon Jan 27 15:51:31 2014 : Info: ++[chap] returns invalid
Mon Jan 27 15:51:31 2014 : Info: Failed to authenticate the user.
Mon Jan 27 15:51:31 2014 : Info: Using Post-Auth-Type Reject
Mon Jan 27 15:51:31 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
```
My /etc/freeradius/sites-enabled/default   has the following in the authenticate {...} section
```
authenticate {
        #
        #  PAP authentication, when a back-end database listed
        #  in the 'authorize' section supplies a password.  The
        #  password can be clear-text, or encrypted.
        Auth-Type PAP {
                pap
        }

        #
        #  Most people want CHAP authentication
        #  A back-end database listed in the 'authorize' section
        #  MUST supply a CLEAR TEXT password.  Encrypted passwords
        #  won't work.
        Auth-Type CHAP {
                chap
        }

```
which leads me to suspect that daloRADIUS is encrypting the passwords it is creating and therefore they cannot be used by CHAP authentication. 

If i create add a user to radcheck in mysql, the user is authenticated and authorized with no problem

```
mysql> USE radius;
mysql> insert into radcheck (username, attribute, value) values ('randtest', 'Password', 'randtest');
Query OK, 1 row affected (0.00 sec)
```
Questions:
[LIST=1]
[*]Am i understanding the debug output clearly? 
[*]If yes, how can i make daloRADIUS create Clear-Text passwords? 
[*]Should i change the authentication module to PAP instead? If so, how do i do that? 
[*]Am i asking the right questions? 
[/LIST]
Any help will be greatly appreciated:)

---

### Post by okay7675 on 2014-01-27
SOLVED!!!!!

Turns out i had the wrong database settings in my /var/www/daloradius/library/daloradius.conf.php. I had the wrong database name, and password in the following lines

```
$configValues['CONFIG_DB_USER'] = 'xxxx';
$configValues['CONFIG_DB_PASS'] = 'xxxx';
$configValues['CONFIG_DB_NAME'] = 'xxxx';

```

---

