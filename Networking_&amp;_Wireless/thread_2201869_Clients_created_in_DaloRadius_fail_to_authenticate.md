---
title: "Clients created in DaloRadius fail to authenticate in FreeRadius"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by okay7675 on 2014-01-26
Hi all, 

Firstly, i hope i'm posting in the right forum, if not, a thousand apologies!!

I have installed and am running FreeRadius+Daloradius+CoovaChilli (according to [http://ubuntuforums.org/showthread.php?t=2070298](http://ubuntuforums.org/showthread.php?t=2070298)). All attempts at accessing the internet by users created in Daloradius are being rejected- running FreeRadius in debug mode gives the following output:

```
root@ubuntu:~# freeradius -XXX
Sun Jan 26 17:19:00 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sun Jan 26 17:19:00 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sun Jan 26 17:19:00 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sun Jan 26 17:19:00 2014 : Info: PARTICULAR PURPOSE. 
Sun Jan 26 17:19:00 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sun Jan 26 17:19:00 2014 : Info: GNU General Public License v2. 
Sun Jan 26 17:19:00 2014 : Info: Starting - reading configuration files ...
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sun Jan 26 17:19:00 2014 : Debug: including files in directory /etc/freeradius/modules/
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sun Jan 26 17:19:00 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sun Jan 26 17:19:00 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sun Jan 26 17:19:00 2014 : Debug: main {
Sun Jan 26 17:19:00 2014 : Debug:     user = "freerad"
Sun Jan 26 17:19:00 2014 : Debug:     group = "freerad"
Sun Jan 26 17:19:00 2014 : Debug:     allow_core_dumps = no
Sun Jan 26 17:19:00 2014 : Debug: }
Sun Jan 26 17:19:00 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sun Jan 26 17:19:00 2014 : Debug: main {
Sun Jan 26 17:19:00 2014 : Debug:     prefix = "/usr"
Sun Jan 26 17:19:00 2014 : Debug:     localstatedir = "/var"
Sun Jan 26 17:19:00 2014 : Debug:     logdir = "/var/log/freeradius"
Sun Jan 26 17:19:00 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sun Jan 26 17:19:00 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sun Jan 26 17:19:00 2014 : Debug:     hostname_lookups = no
Sun Jan 26 17:19:00 2014 : Debug:     max_request_time = 30
Sun Jan 26 17:19:00 2014 : Debug:     cleanup_delay = 5
Sun Jan 26 17:19:00 2014 : Debug:     max_requests = 1024
Sun Jan 26 17:19:00 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sun Jan 26 17:19:00 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sun Jan 26 17:19:00 2014 : Debug:     debug_level = 0
Sun Jan 26 17:19:00 2014 : Debug:     proxy_requests = yes
Sun Jan 26 17:19:00 2014 : Debug:  log {
Sun Jan 26 17:19:00 2014 : Debug:     stripped_names = no
Sun Jan 26 17:19:00 2014 : Debug:     auth = no
Sun Jan 26 17:19:00 2014 : Debug:     auth_badpass = no
Sun Jan 26 17:19:00 2014 : Debug:     auth_goodpass = no
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug:  security {
Sun Jan 26 17:19:00 2014 : Debug:     max_attributes = 200
Sun Jan 26 17:19:00 2014 : Debug:     reject_delay = 1
Sun Jan 26 17:19:00 2014 : Debug:     status_server = yes
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug: }
Sun Jan 26 17:19:00 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sun Jan 26 17:19:00 2014 : Debug:  proxy server {
Sun Jan 26 17:19:00 2014 : Debug:     retry_delay = 5
Sun Jan 26 17:19:00 2014 : Debug:     retry_count = 3
Sun Jan 26 17:19:00 2014 : Debug:     default_fallback = no
Sun Jan 26 17:19:00 2014 : Debug:     dead_time = 120
Sun Jan 26 17:19:00 2014 : Debug:     wake_all_if_all_dead = no
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug:  home_server localhost {
Sun Jan 26 17:19:00 2014 : Debug:     ipaddr = 127.0.0.1
Sun Jan 26 17:19:00 2014 : Debug:     port = 1812
Sun Jan 26 17:19:00 2014 : Debug:     type = "auth"
Sun Jan 26 17:19:00 2014 : Debug:     secret = "testing123"
Sun Jan 26 17:19:00 2014 : Debug:     response_window = 20
Sun Jan 26 17:19:00 2014 : Debug:     max_outstanding = 65536
Sun Jan 26 17:19:00 2014 : Debug:     require_message_authenticator = yes
Sun Jan 26 17:19:00 2014 : Debug:     zombie_period = 40
Sun Jan 26 17:19:00 2014 : Debug:     status_check = "status-server"
Sun Jan 26 17:19:00 2014 : Debug:     ping_interval = 30
Sun Jan 26 17:19:00 2014 : Debug:     check_interval = 30
Sun Jan 26 17:19:00 2014 : Debug:     num_answers_to_alive = 3
Sun Jan 26 17:19:00 2014 : Debug:     num_pings_to_alive = 3
Sun Jan 26 17:19:00 2014 : Debug:     revive_interval = 120
Sun Jan 26 17:19:00 2014 : Debug:     status_check_timeout = 4
Sun Jan 26 17:19:00 2014 : Debug:     irt = 2
Sun Jan 26 17:19:00 2014 : Debug:     mrt = 16
Sun Jan 26 17:19:00 2014 : Debug:     mrc = 5
Sun Jan 26 17:19:00 2014 : Debug:     mrd = 30
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug:  home_server_pool my_auth_failover {
Sun Jan 26 17:19:00 2014 : Debug:     type = fail-over
Sun Jan 26 17:19:00 2014 : Debug:     home_server = localhost
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug:  realm example.com {
Sun Jan 26 17:19:00 2014 : Debug:     auth_pool = my_auth_failover
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug:  realm LOCAL {
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug: radiusd: #### Loading Clients ####
Sun Jan 26 17:19:00 2014 : Debug:  client localhost {
Sun Jan 26 17:19:00 2014 : Debug:     ipaddr = 127.0.0.1
Sun Jan 26 17:19:00 2014 : Debug:     require_message_authenticator = no
Sun Jan 26 17:19:00 2014 : Debug:     secret = "testing123"
Sun Jan 26 17:19:00 2014 : Debug:     nastype = "other"
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug: radiusd: #### Instantiating modules ####
Sun Jan 26 17:19:00 2014 : Debug:  instantiate {
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_exec
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sun Jan 26 17:19:00 2014 : Debug:   exec {
Sun Jan 26 17:19:00 2014 : Debug:     wait = no
Sun Jan 26 17:19:00 2014 : Debug:     input_pairs = "request"
Sun Jan 26 17:19:00 2014 : Debug:     shell_escape = yes
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sun Jan 26 17:19:00 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sun Jan 26 17:19:00 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sun Jan 26 17:19:00 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sun Jan 26 17:19:00 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sun Jan 26 17:19:00 2014 : Debug:     key = "User-Name"
Sun Jan 26 17:19:00 2014 : Debug:     sqlmod-inst = "sql"
Sun Jan 26 17:19:00 2014 : Debug:     query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
Sun Jan 26 17:19:00 2014 : Debug:     reset = "never"
Sun Jan 26 17:19:00 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Current Time: 1390749540 [2014-01-26 17:19:00], Next reset 0 [2014-01-26 17:00:00]
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Current Time: 1390749540 [2014-01-26 17:19:00], Prev reset 0 [2014-01-26 17:00:00]
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sun Jan 26 17:19:00 2014 : Debug:   sqlcounter noresetcounter {
Sun Jan 26 17:19:00 2014 : Debug:     counter-name = "Session-Timeout"
Sun Jan 26 17:19:00 2014 : Debug:     check-name = "Session-Timeout"
Sun Jan 26 17:19:00 2014 : Debug:     reply-name = "Session-Timeout"
Sun Jan 26 17:19:00 2014 : Debug:     key = "User-Name"
Sun Jan 26 17:19:00 2014 : Debug:     sqlmod-inst = "sql"
Sun Jan 26 17:19:00 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sun Jan 26 17:19:00 2014 : Debug:     reset = "never"
Sun Jan 26 17:19:00 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Current Time: 1390749540 [2014-01-26 17:19:00], Next reset 0 [2014-01-26 17:00:00]
Sun Jan 26 17:19:00 2014 : Debug: rlm_sqlcounter: Current Time: 1390749540 [2014-01-26 17:19:00], Prev reset 0 [2014-01-26 17:00:00]
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_expr
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_expiration
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sun Jan 26 17:19:00 2014 : Debug:   expiration {
Sun Jan 26 17:19:00 2014 : Debug:     reply-message = "Password Has Expired  "
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_logintime
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sun Jan 26 17:19:00 2014 : Debug:   logintime {
Sun Jan 26 17:19:00 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sun Jan 26 17:19:00 2014 : Debug:     minimum-timeout = 60
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:  }
Sun Jan 26 17:19:00 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sun Jan 26 17:19:00 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sun Jan 26 17:19:00 2014 : Debug:  modules {
Sun Jan 26 17:19:00 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_pap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sun Jan 26 17:19:00 2014 : Debug:   pap {
Sun Jan 26 17:19:00 2014 : Debug:     encryption_scheme = "auto"
Sun Jan 26 17:19:00 2014 : Debug:     auto_header = no
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_chap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_mschap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sun Jan 26 17:19:00 2014 : Debug:   mschap {
Sun Jan 26 17:19:00 2014 : Debug:     use_mppe = yes
Sun Jan 26 17:19:00 2014 : Debug:     require_encryption = no
Sun Jan 26 17:19:00 2014 : Debug:     require_strong = no
Sun Jan 26 17:19:00 2014 : Debug:     with_ntdomain_hack = no
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_unix
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sun Jan 26 17:19:00 2014 : Debug:   unix {
Sun Jan 26 17:19:00 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to module rlm_eap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sun Jan 26 17:19:00 2014 : Debug:   eap {
Sun Jan 26 17:19:00 2014 : Debug:     default_eap_type = "md5"
Sun Jan 26 17:19:00 2014 : Debug:     timer_expire = 60
Sun Jan 26 17:19:00 2014 : Debug:     ignore_unknown_eap_types = no
Sun Jan 26 17:19:00 2014 : Debug:     cisco_accounting_username_bug = no
Sun Jan 26 17:19:00 2014 : Debug:     max_sessions = 4096
Sun Jan 26 17:19:00 2014 : Debug:   }
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating eap-md5
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating eap-leap
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating eap-gtc
Sun Jan 26 17:19:00 2014 : Debug:    gtc {
Sun Jan 26 17:19:00 2014 : Debug:     challenge = "Password: "
Sun Jan 26 17:19:00 2014 : Debug:     auth_type = "PAP"
Sun Jan 26 17:19:00 2014 : Debug:    }
Sun Jan 26 17:19:00 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sun Jan 26 17:19:00 2014 : Debug:  Module: Instantiating eap-tls
Sun Jan 26 17:19:00 2014 : Debug:    tls {
Sun Jan 26 17:19:00 2014 : Debug:     rsa_key_exchange = no
Sun Jan 26 17:19:00 2014 : Debug:     dh_key_exchange = yes
Sun Jan 26 17:19:00 2014 : Debug:     rsa_key_length = 512
Sun Jan 26 17:19:00 2014 : Debug:     dh_key_length = 512
Sun Jan 26 17:19:00 2014 : Debug:     verify_depth = 0
Sun Jan 26 17:19:00 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sun Jan 26 17:19:00 2014 : Debug:     pem_file_type = yes
Sun Jan 26 17:19:00 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sun Jan 26 17:19:00 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sun Jan 26 17:19:00 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sun Jan 26 17:19:00 2014 : Debug:     private_key_password = "whatever"
Sun Jan 26 17:19:00 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sun Jan 26 17:19:00 2014 : Debug:     random_file = "/dev/urandom"
Sun Jan 26 17:19:00 2014 : Debug:     fragment_size = 1024
Sun Jan 26 17:19:00 2014 : Debug:     include_length = yes
Sun Jan 26 17:19:00 2014 : Debug:     check_crl = no
Sun Jan 26 17:19:00 2014 : Debug:     cipher_list = "DEFAULT"
Sun Jan 26 17:19:00 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sun Jan 26 17:19:00 2014 : Debug:     cache {
Sun Jan 26 17:19:00 2014 : Debug:     enable = no
Sun Jan 26 17:19:00 2014 : Debug:     lifetime = 24
Sun Jan 26 17:19:00 2014 : Debug:     max_entries = 255
Sun Jan 26 17:19:00 2014 : Debug:     }
Sun Jan 26 17:19:00 2014 : Debug:     verify {
Sun Jan 26 17:19:00 2014 : Debug:     }
Sun Jan 26 17:19:00 2014 : Debug:    }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating eap-ttls
Sun Jan 26 17:19:01 2014 : Debug:    ttls {
Sun Jan 26 17:19:01 2014 : Debug:     default_eap_type = "md5"
Sun Jan 26 17:19:01 2014 : Debug:     copy_request_to_tunnel = no
Sun Jan 26 17:19:01 2014 : Debug:     use_tunneled_reply = no
Sun Jan 26 17:19:01 2014 : Debug:     virtual_server = "inner-tunnel"
Sun Jan 26 17:19:01 2014 : Debug:     include_length = yes
Sun Jan 26 17:19:01 2014 : Debug:    }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating eap-peap
Sun Jan 26 17:19:01 2014 : Debug:    peap {
Sun Jan 26 17:19:01 2014 : Debug:     default_eap_type = "mschapv2"
Sun Jan 26 17:19:01 2014 : Debug:     copy_request_to_tunnel = no
Sun Jan 26 17:19:01 2014 : Debug:     use_tunneled_reply = no
Sun Jan 26 17:19:01 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sun Jan 26 17:19:01 2014 : Debug:     virtual_server = "inner-tunnel"
Sun Jan 26 17:19:01 2014 : Debug:    }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating eap-mschapv2
Sun Jan 26 17:19:01 2014 : Debug:    mschapv2 {
Sun Jan 26 17:19:01 2014 : Debug:     with_ntdomain_hack = no
Sun Jan 26 17:19:01 2014 : Debug:    }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_realm
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sun Jan 26 17:19:01 2014 : Debug:   realm suffix {
Sun Jan 26 17:19:01 2014 : Debug:     format = "suffix"
Sun Jan 26 17:19:01 2014 : Debug:     delimiter = "@"
Sun Jan 26 17:19:01 2014 : Debug:     ignore_default = no
Sun Jan 26 17:19:01 2014 : Debug:     ignore_null = no
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_files
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sun Jan 26 17:19:01 2014 : Debug:   files {
Sun Jan 26 17:19:01 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sun Jan 26 17:19:01 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sun Jan 26 17:19:01 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sun Jan 26 17:19:01 2014 : Debug:     compat = "no"
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking session {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_radutmp
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sun Jan 26 17:19:01 2014 : Debug:   radutmp {
Sun Jan 26 17:19:01 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sun Jan 26 17:19:01 2014 : Debug:     username = "%{User-Name}"
Sun Jan 26 17:19:01 2014 : Debug:     case_sensitive = yes
Sun Jan 26 17:19:01 2014 : Debug:     check_with_nas = yes
Sun Jan 26 17:19:01 2014 : Debug:     perm = 384
Sun Jan 26 17:19:01 2014 : Debug:     callerid = yes
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Sun Jan 26 17:19:01 2014 : Debug:   attr_filter attr_filter.access_reject {
Sun Jan 26 17:19:01 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sun Jan 26 17:19:01 2014 : Debug:     key = "%{User-Name}"
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  } # modules
Sun Jan 26 17:19:01 2014 : Debug: } # server
Sun Jan 26 17:19:01 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sun Jan 26 17:19:01 2014 : Debug:  modules {
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_digest
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_preprocess
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sun Jan 26 17:19:01 2014 : Debug:   preprocess {
Sun Jan 26 17:19:01 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sun Jan 26 17:19:01 2014 : Debug:     hints = "/etc/freeradius/hints"
Sun Jan 26 17:19:01 2014 : Debug:     with_ascend_hack = no
Sun Jan 26 17:19:01 2014 : Debug:     ascend_channels_per_line = 23
Sun Jan 26 17:19:01 2014 : Debug:     with_ntdomain_hack = no
Sun Jan 26 17:19:01 2014 : Debug:     with_specialix_jetstream_hack = no
Sun Jan 26 17:19:01 2014 : Debug:     with_cisco_vsa_hack = no
Sun Jan 26 17:19:01 2014 : Debug:     with_alvarion_vsa_hack = no
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_sql
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sun Jan 26 17:19:01 2014 : Debug:   sql {
Sun Jan 26 17:19:01 2014 : Debug:     driver = "rlm_sql_mysql"
Sun Jan 26 17:19:01 2014 : Debug:     server = "localhost"
Sun Jan 26 17:19:01 2014 : Debug:     port = ""
Sun Jan 26 17:19:01 2014 : Debug:     login = "radius"
Sun Jan 26 17:19:01 2014 : Debug:     password = "radpass"
Sun Jan 26 17:19:01 2014 : Debug:     radius_db = "radius"
Sun Jan 26 17:19:01 2014 : Debug:     read_groups = yes
Sun Jan 26 17:19:01 2014 : Debug:     sqltrace = no
Sun Jan 26 17:19:01 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sun Jan 26 17:19:01 2014 : Debug:     readclients = no
Sun Jan 26 17:19:01 2014 : Debug:     deletestalesessions = yes
Sun Jan 26 17:19:01 2014 : Debug:     num_sql_socks = 5
Sun Jan 26 17:19:01 2014 : Debug:     lifetime = 0
Sun Jan 26 17:19:01 2014 : Debug:     max_queries = 0
Sun Jan 26 17:19:01 2014 : Debug:     sql_user_name = "%{User-Name}"
Sun Jan 26 17:19:01 2014 : Debug:     default_user_profile = ""
Sun Jan 26 17:19:01 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sun Jan 26 17:19:01 2014 : Debug:     authorize_check_query = "SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sun Jan 26 17:19:01 2014 : Debug:     authorize_reply_query = "SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sun Jan 26 17:19:01 2014 : Debug:     authorize_group_check_query = "SELECT id, groupname, attribute,           Value, op           FROM radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sun Jan 26 17:19:01 2014 : Debug:     authorize_group_reply_query = "SELECT id, groupname, attribute,           value, op           FROM radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_onoff_query = "          UPDATE radacct           SET              acctstoptime       =  '%S',              acctsessiontime    =  unix_timestamp('%S') -                                    unix_timestamp(acctstarttime),              acctterminatecause =  '%{Acct-Terminate-Cause}',              acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE acctstoptime IS NULL           AND nasipaddress      =  '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_update_query = "           UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_update_query_alt = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,      nasportid,              nasporttype,      acctstarttime,     acctsessiontime,              acctauthentic,    connectinfo_start, acctinputoctets,              acctoutputoctets, calledstationid,   callingstationid,              servicetype,      framedprotocol,    framedipaddress,              acctstartdelay,   xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                       INTERVAL (%{%{Acct-Session-Time}:-0} +                                 %{%{Acct-Delay-Time}:-0}) SECOND),                       '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Service-Type}', '%{Framed-Protocol}',              '%{Framed-IP-Address}',              '0', '%{X-Ascend-Session-Svr-Key}')"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_start_query = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,     username,              realm,            nasipaddress,     nasportid,              nasporttype,      acctstarttime,    acctstoptime,              acctsessiontime,  acctauthentic,    connectinfo_start,              connectinfo_stop, acctinputoctets,  acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,      framedprotocol,   framedipaddress,              acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}', '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',              '', '0', '0',              '%{Called-Station-Id}', '%{Calling-Station-Id}', '',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_start_query_alt = "           UPDATE radacct SET              acctstarttime     = '%S',              acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',              connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'           AND nasipaddress     = '%{NAS-IP-Address}'"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_stop_query = "           UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}'"
Sun Jan 26 17:19:01 2014 : Debug:     accounting_stop_query_alt = "           INSERT INTO radacct             (acctsessionid, acctuniqueid, username,              realm, nasipaddress, nasportid,              nasporttype, acctstarttime, acctstoptime,              acctsessiontime, acctauthentic, connectinfo_start,              connectinfo_stop, acctinputoctets, acctoutputoctets,              calledstationid, callingstationid, acctterminatecause,              servicetype, framedprotocol, framedipaddress,              acctstartdelay, acctstopdelay)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                  INTERVAL (%{%{Acct-Session-Time}:-0} +                  %{%{Acct-Delay-Time}:-0}) SECOND),              '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '',              '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '0', '%{%{Acct-Delay-Time}:-0}')"
Sun Jan 26 17:19:01 2014 : Debug:     group_membership_query = "SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority"
Sun Jan 26 17:19:01 2014 : Debug:     connect_failure_retry_delay = 60
Sun Jan 26 17:19:01 2014 : Debug:     simul_count_query = ""
Sun Jan 26 17:19:01 2014 : Debug:     simul_verify_query = "SELECT radacctid, acctsessionid, username,                                nasipaddress, nasportid, framedipaddress,                                callingstationid, framedprotocol                                FROM radacct                                WHERE username = '%{SQL-User-Name}'                                AND acctstoptime IS NULL"
Sun Jan 26 17:19:01 2014 : Debug:     postauth_query = "INSERT INTO radpostauth                           (username, pass, reply, authdate)                           VALUES (                           '%{User-Name}',                           '%{%{User-Password}:-%{Chap-Password}}',                           '%{reply:Packet-Type}', '%S')"
Sun Jan 26 17:19:01 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sun Jan 26 17:19:01 2014 : Debug: rlm_sql (sql): starting 0
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sun Jan 26 17:19:01 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Sun Jan 26 17:19:01 2014 : Debug: rlm_sql (sql): starting 1
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sun Jan 26 17:19:01 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Sun Jan 26 17:19:01 2014 : Debug: rlm_sql (sql): starting 2
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sun Jan 26 17:19:01 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Sun Jan 26 17:19:01 2014 : Debug: rlm_sql (sql): starting 3
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sun Jan 26 17:19:01 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Sun Jan 26 17:19:01 2014 : Debug: rlm_sql (sql): starting 4
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sun Jan 26 17:19:01 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sun Jan 26 17:19:01 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sun Jan 26 17:19:01 2014 : Debug:   acct_unique {
Sun Jan 26 17:19:01 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sun Jan 26 17:19:01 2014 : Debug:  Module: Linked to module rlm_detail
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sun Jan 26 17:19:01 2014 : Debug:   detail {
Sun Jan 26 17:19:01 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sun Jan 26 17:19:01 2014 : Debug:     header = "%t"
Sun Jan 26 17:19:01 2014 : Debug:     detailperm = 384
Sun Jan 26 17:19:01 2014 : Debug:     dirperm = 493
Sun Jan 26 17:19:01 2014 : Debug:     locking = no
Sun Jan 26 17:19:01 2014 : Debug:     log_packet_header = no
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Sun Jan 26 17:19:01 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sun Jan 26 17:19:01 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sun Jan 26 17:19:01 2014 : Debug:     key = "%{User-Name}"
Sun Jan 26 17:19:01 2014 : Debug:   }
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking session {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sun Jan 26 17:19:01 2014 : Debug:  } # modules
Sun Jan 26 17:19:01 2014 : Debug: } # server
Sun Jan 26 17:19:01 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sun Jan 26 17:19:01 2014 : Debug: listen {
Sun Jan 26 17:19:01 2014 : Debug:     type = "auth"
Sun Jan 26 17:19:01 2014 : Debug:     ipaddr = *
Sun Jan 26 17:19:01 2014 : Debug:     port = 0
Sun Jan 26 17:19:01 2014 : Debug: }
Sun Jan 26 17:19:01 2014 : Debug: listen {
Sun Jan 26 17:19:01 2014 : Debug:     type = "acct"
Sun Jan 26 17:19:01 2014 : Debug:     ipaddr = *
Sun Jan 26 17:19:01 2014 : Debug:     port = 0
Sun Jan 26 17:19:01 2014 : Debug: }
Sun Jan 26 17:19:01 2014 : Debug: listen {
Sun Jan 26 17:19:01 2014 : Debug:     type = "auth"
Sun Jan 26 17:19:01 2014 : Debug:     ipaddr = 127.0.0.1
Sun Jan 26 17:19:01 2014 : Debug:     port = 18120
Sun Jan 26 17:19:01 2014 : Debug: }
Sun Jan 26 17:19:01 2014 : Debug: Listening on authentication address * port 1812
Sun Jan 26 17:19:01 2014 : Debug: Listening on accounting address * port 1813
Sun Jan 26 17:19:01 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sun Jan 26 17:19:01 2014 : Debug: Listening on proxy address * port 1814
Sun Jan 26 17:19:01 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 34933, id=70, length=291
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniE37r"
    CHAP-Challenge = 0x0d083ea131d4ac60ee5e38a8a8697683
    CHAP-Password = 0x0064b5fb0fbcc344a2b9449ade22f1a2b0
    Service-Type = Login-User
    Acct-Session-Id = "52e5266500000002"
    Framed-IP-Address = 10.1.0.6
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xf6ff748d5c79faebb0b2781c2d170455
Sun Jan 26 17:20:28 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sun Jan 26 17:20:28 2014 : Info: +- entering group authorize {...}
Sun Jan 26 17:20:28 2014 : Info: ++[preprocess] returns ok
Sun Jan 26 17:20:28 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sun Jan 26 17:20:28 2014 : Info: ++[chap] returns ok
Sun Jan 26 17:20:28 2014 : Info: ++[mschap] returns noop
Sun Jan 26 17:20:28 2014 : Info: ++[digest] returns noop
Sun Jan 26 17:20:28 2014 : Info: [suffix] No '@' in User-Name = "omniE37r", looking up realm NULL
Sun Jan 26 17:20:28 2014 : Info: [suffix] No such realm "NULL"
Sun Jan 26 17:20:28 2014 : Info: ++[suffix] returns noop
Sun Jan 26 17:20:28 2014 : Info: [eap] No EAP-Message, not doing EAP
Sun Jan 26 17:20:28 2014 : Info: ++[eap] returns noop
Sun Jan 26 17:20:28 2014 : Info: [sql]     expand: %{User-Name} -> omniE37r
Sun Jan 26 17:20:28 2014 : Info: [sql] sql_set_user escaped user --> 'omniE37r'
Sun Jan 26 17:20:28 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 4
Sun Jan 26 17:20:28 2014 : Info: [sql]     expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'omniE37r'           ORDER BY id
Sun Jan 26 17:20:28 2014 : Info: [sql]     expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'omniE37r'           ORDER BY priority
Sun Jan 26 17:20:28 2014 : Debug: rlm_sql (sql): Released sql socket id: 4
Sun Jan 26 17:20:28 2014 : Info: [sql] User omniE37r not found
Sun Jan 26 17:20:28 2014 : Info: ++[sql] returns notfound
Sun Jan 26 17:20:28 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sun Jan 26 17:20:28 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sun Jan 26 17:20:28 2014 : Info: ++[chillispot_max_bytes] returns noop
Sun Jan 26 17:20:28 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sun Jan 26 17:20:28 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sun Jan 26 17:20:28 2014 : Info: ++[noresetcounter] returns noop
Sun Jan 26 17:20:28 2014 : Info: ++[expiration] returns noop
Sun Jan 26 17:20:28 2014 : Info: ++[logintime] returns noop
Sun Jan 26 17:20:28 2014 : Info: [pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
Sun Jan 26 17:20:28 2014 : Info: ++[pap] returns noop
Sun Jan 26 17:20:28 2014 : Info: Found Auth-Type = CHAP
Sun Jan 26 17:20:28 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sun Jan 26 17:20:28 2014 : Info: +- entering group CHAP {...}
Sun Jan 26 17:20:28 2014 : Info: [chap] login attempt by "omniE37r" with CHAP password
Sun Jan 26 17:20:28 2014 : Info: [chap] Cleartext-Password is required for authentication
Sun Jan 26 17:20:28 2014 : Info: ++[chap] returns invalid
Sun Jan 26 17:20:28 2014 : Info: Failed to authenticate the user.
Sun Jan 26 17:20:28 2014 : Info: Using Post-Auth-Type Reject
Sun Jan 26 17:20:28 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sun Jan 26 17:20:28 2014 : Info: +- entering group REJECT {...}
Sun Jan 26 17:20:28 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniE37r
Sun Jan 26 17:20:28 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sun Jan 26 17:20:28 2014 : Info: ++[attr_filter.access_reject] returns updated
Sun Jan 26 17:20:28 2014 : Info: Delaying reject of request 0 for 1 seconds
Sun Jan 26 17:20:28 2014 : Debug: Going to the next request
Sun Jan 26 17:20:28 2014 : Debug: Waking up in 0.9 seconds.
Sun Jan 26 17:20:29 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 70 to 127.0.0.1 port 34933
Sun Jan 26 17:20:29 2014 : Debug: Waking up in 4.9 seconds.
Sun Jan 26 17:20:34 2014 : Info: Cleaning up request 0 ID 70 with timestamp +87
Sun Jan 26 17:20:34 2014 : Info: Ready to process requests.

 
```
I think the problem lies here
```
Sun Jan 26 17:20:28 2014 : Info: [pap] WARNING! No "known good" password  found for the user.  Authentication may fail because of this.
Sun Jan 26 17:20:28 2014 : Info: ++[pap] returns noop
Sun Jan 26 17:20:28 2014 : Info: Found Auth-Type = CHAP
Sun Jan 26 17:20:28 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sun Jan 26 17:20:28 2014 : Info: +- entering group CHAP {...}
[B]Sun Jan 26 17:20:28 2014 : Info: [chap] login attempt by "omniE37r" with CHAP password
Sun Jan 26 17:20:28 2014 : Info: [chap] Cleartext-Password is required for authentication[/B]
Sun Jan 26 17:20:28 2014 : Info: ++[chap] returns invalid
Sun Jan 26 17:20:28 2014 : Info: Failed to authenticate the user.
Sun Jan 26 17:20:28 2014 : Info: Using Post-Auth-Type Reject 
```

 If, however, i insert a user directly into radcheck, they can authenticate and are given authorisation 

```
mysql> USE radius;
mysql> insert into radcheck (username, attribute, value) values ('randtest', 'Password', 'randtest');
Query OK, 1 row affected (0.00 sec)

```

Questions:
[LIST=1]
[*]Is this because the passwords that are being generated in DaloRadius are not in Cleartext? If so, how do i fix that? 
[*]Or are the credentials that are being generated in Daloradius not being added into radcheck? 
[*]Is there any accounting thats being 'applied' to this user 'randtest' (the one added directly into radcheck)? Can i restrict bandwidth, time etc? 
[/LIST]

---

### Post by okay7675 on 2014-01-27
SOLVED!!!!!

Turns out i had the wrong database settings in my  /var/www/daloradius/library/daloradius.conf.php. I had the wrong  database name, and password in the following lines

```
$configValues['CONFIG_DB_USER'] = 'xxxx';
$configValues['CONFIG_DB_PASS'] = 'xxxx';
$configValues['CONFIG_DB_NAME'] = 'xxxx';

```

---

