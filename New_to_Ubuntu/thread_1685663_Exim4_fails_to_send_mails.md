---
title: "Exim4 fails to send mails"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by animade4linux on 2011-02-11
Exim4 fails to send mails outside except gmail at Ubuntu.
All mails are got stuck in queue.
 
Am mentioned the "update-exim4.conf" file below which I configured on a particular sever. Please have a look.
 
 
#/etc/exim4/update-exim4.conf.conf
 
dc_eximconfig_configtype='internet'
dc_other_hostnames='example.com'
dc_local_interfaces='127.0.0.1 ; ::1'
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname=''
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'
/etc/exim4/update-exim4.conf.conf (END)
 
 
I don't know why it's got stuck in queue always. Can anybody help me out from this problem?
 
 
Thanks in advance.

---

