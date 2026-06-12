---
title: "Intrepid Ibex &quot;failed to join domain: failed to get DC for domain xxxx.LOCAL&quot; issue"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by innovate2000 on 2008-11-26
I am having the "failed to join domain: failed to get DC for domain XXXX.LOCAL" issue in Intrepid - anyone else solve this?  "net ads lookup dc" and "net ads info" work fine. Pinging DC by FQDN or netbios works fine. At least one other person is having the same issue (I emailed him to see if he'd had a resolution - he hasn't responded): [http://ubuntuforums.org/showthread.php?p=6252005](http://ubuntuforums.org/showthread.php?p=6252005) (entry by DouglasK on pg 18 ). I've stopped avahi, adjusted "hosts" line in /etc/nsswitch.conf (putting "dns" 2nd in list after "files")and added IP (of DC), netbios & fqdn domain (in caps) to /etc/hosts (below 127.0.1.1 entry). I don't know what else to do - I've been working on this for 8 days - I'd hate to have to reinstall to go back to 8.04 Hardy - BIG MESS. I have successfully integrated 8 Hardy servers with Windows network/DC - Hardy was simple - apparently many things changed with Intrepid. If anyone can help, it would be appreciated. Thanks

---

### Post by Causer1984 on 2008-12-03
I can't help, but maybe a little more information could help someone else explain it.

Kerberos appears to be failing preauthentication. In the example below, I have a valid ticket:

```

root@comp:~# net ads join -U domainadmin
Enter domainadmin's password: *BLANK*
Failed to join domain: failed to lookup DC info for domain 'REALM.COM' over rpc: Logon failure
root@comp:~# net ads join -U domainadmin
Enter domainadmin's password: *CORRECT PASSWORD*
Using short domain name -- REALM
Joined 'comp' to realm 'realm.com'
[2008/12/03 14:27:21,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password COMP$@REALM.COM failed: Preauthentication failed
root@comp:~#

```

Hope that helps
This works in Hardy (ie with a blank password). Does anyone know what is going wrong?

---

### Post by Metusalem on 2009-01-09
I have also noticed same problem Ubuntu 8.10. I tried 5 different setup instructions for this, but it is not still working.

I have no clue how to solve this, so my only suggestion is to wait until someone solve it.

---

