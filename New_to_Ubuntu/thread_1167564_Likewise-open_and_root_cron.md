---
title: "Likewise-open and root cron"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by lazyart on 2009-05-23
I've installed likewise-open some time ago and always noticed something odd in my auth.log.

It dawned on me today that the root cron jobs are not running because the root account cannot be authenticated.

Here is a snippet:

```
May 23 02:00:01 calvin CRON[27542]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:01 calvin CRON[27542]: pam_lwidentity(cron:account): failed to get GP info
May 23 02:00:01 calvin CRON[27541]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:01 calvin CRON[27541]: pam_lwidentity(cron:account): failed to get GP info
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:account): request failed
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:account): User 'root' is not known.
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:account): Returning 7 for user "root"
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:account): request failed
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:account): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:account): Returning 7 for user "root"
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:session): request failed
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:session): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_unix(cron:session): session opened for user root by (uid=0)
May 23 02:00:03 calvin dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.89" (uid=1000 pid=12447 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.681" (uid=0 pid=27541 comm="/USR/SBIN/CRON "))
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:session): request failed
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:session): User 'root' is not known.
May 23 02:00:03 calvin CRON[27542]: pam_unix(cron:session): session opened for user root by (uid=0)
May 23 02:00:03 calvin dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.89" (uid=1000 pid=12447 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.682" (uid=0 pid=27542 comm="/USR/SBIN/CRON "))
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:03 calvin CRON[27542]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:03 calvin CRON[27541]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:03 calvin CRON[27541]: pam_unix(cron:session): session closed for user root
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): request failed
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:setcred): User 'root' is not known.
May 23 02:00:07 calvin CRON[27542]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
May 23 02:00:07 calvin CRON[27542]: pam_unix(cron:session): session closed for user root

```

Any thoughts on how to resolve?  I guess I could create an account named root on my domain controller, but that is just asking for trouble.

---

### Post by oneloveamaru on 2009-12-17
I noticed the same errors in my auth.log but it looks like my cron jobs are still running.

Check to see if the root account isn't expired. chage -l root

Check /etc/nsswitch.conf and make sure it says:

passwd:         compat lwidentity
group:          compat lwidentity

as long as compat is first, it should be checking the local user database first.

I'll do some double checking on my end to make sure my cron jobs really are running.

---

### Post by =not4prophet= on 2009-12-17
I had some issues with LikewiseOpen and local accounts authenticating using compat for passwd and group in nsswitch.conf.  Changing compat to files fixed the problem.

my nsswitch.conf settings:

passwd:  files lsass
group:    files lsass

---

### Post by oneloveamaru on 2009-12-17
On double check, my cron jobs are running just fine with compat in nsswitch.conf but I would like to get rid of the errors in auth.log:

Dec 17 14:55:01 server CRON[5621]: pam_lwidentity(cron:setcred): User 'root' is not known.
Dec 17 14:55:01 server CRON[5621]: pam_lwidentity(cron:setcred): request failed

It isn't holding anything up but I do have some intrusion detection software that is annoying me with these.

Do you still get these errors with "files" in nsswitch.conf?

---

### Post by =not4prophet= on 2009-12-17
no, I do not get those errors running cron jobs as root with files listed first in nsswitch.conf

---

### Post by grayrace on 2010-02-23
Greetings,

I've been having the same issue. I've tried adding files and replacing compat with files. It has produced no change. 

my nsswitch:

passwd:         files lwidentity
group:          files lwidentity
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

I also tried:

passwd:         compat lwidentity
group:          compat lwidentity

AND:

passwd: files         compat  lwidentity
 group: files          compat  lwidentity

Noticeably I have lwidentity rather than lsass. I don't know if this was a change with like-wise in the intervening time. Any other advice or something I'm missing?

Here is my auth log:

Feb 23 13:20:01 openvzdev01 CRON[23446]: pam_lwidentity(cron:setcred): User 'root' is not known.
Feb 23 13:20:01 openvzdev01 CRON[23446]: pam_lwidentity(cron:setcred): request failed
Feb 23 13:20:01 openvzdev01 CRON[23446]: pam_lwidentity(cron:setcred): User 'root' is not known.
Feb 23 13:20:01 openvzdev01 CRON[23446]: pam_lwidentity(cron:session): PAM config: global:krb5_ccache_type 'FILE'
Feb 23 13:20:01 openvzdev01 CRON[23452]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Feb 23 13:20:01 openvzdev01 CRON[23452]: pam_lwidentity(cron:account): failed to get GP info
Feb 23 13:20:01 openvzdev01 CRON[23452]: pam_lwidentity(cron:account): request failed

---

### Post by trinaryouroboros on 2010-05-03
I also was experiencing this problem...

I have a feeling, however, this is largely due to the fact I haven't upgraded the likewise open package to the current developer's recommended version - the Ubuntu repo folk have been loathe to upgrade this package for whatever reason.

I actually have support through Likewise for other servers, and their support team have previously highly recommended to just use the installer on their site fresh and new, since bugs are constantly being fixed and new releases happen quite often:

[http://www.likewise.com/download/index.php](http://www.likewise.com/download/index.php)

If you've already registered, or don't like registration in general - there is a direct download page for the deb's, I believe. Just google "likewise open community download" - or something to that effect.

---

