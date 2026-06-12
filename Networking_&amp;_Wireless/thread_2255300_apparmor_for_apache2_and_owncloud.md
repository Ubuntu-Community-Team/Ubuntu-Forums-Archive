---
title: "apparmor for apache2 and owncloud"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2014-12-03
I hope I put this in the right place. I need apparmor for apache2 and owncloud I have used the gui at [http://www.tecmint.com/install-owncloud-to-create-personal-storage-in-linux/](http://www.tecmint.com/install-owncloud-to-create-personal-storage-in-linux/) to install apache2 and ownclud. Now I'm trying to secure it I installed apparmor and the profiles from ubuntu but could not find a profile for what i need so how do i set one up.

Can I use this one from [http://samiux.blogspot.com/2013/02/howto-owncloud-with-apache-on-ubuntu.html](http://samiux.blogspot.com/2013/02/howto-owncloud-with-apache-on-ubuntu.html)
I did not use it for installing but found it when a did a google search for apparmor.

---

### Post by Lars Noodén on 2014-12-04
I would start here if you are going to make your own AppArmor profile:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Then take a look at some of the ones for other applications already on your system.

Developing your own profile for Apache2 will be an iterative process and you'll need to watch the logs for quite a while to catch all the edge cases.

---

### Post by lance bermudez on 2014-12-04
aa-status | grep apache2

shows no profile and also I was still looking around google and ran accross something called libapache2-mod-apparmor module but can not find anything to help me figure it out yet either

---

### Post by Lars Noodén on 2014-12-05
> **lance bermudez said:**
> aa-status | grep apache2

shows no profile and also I was still looking around google and ran accross something called libapache2-mod-apparmor module but can not find anything to help me figure it out yet either

Apache2 does not include its own apparmor profile.  You'd have to write one based on where you have your files and what your virtual hosts are up to.  About mod_apparmor, it seems to be for web applications running on Apache2.  How do you plan to use Apache2?

---

### Post by lance bermudez on 2014-12-05
Only going to use it for owncloud with https. The guides I used are at the top in my first post. I posted my guides because they show the packages I have installed to use with apache2.

---

### Post by Lars Noodén on 2014-12-06
Ok.   Owncloud, on the server side, is just PHP with Apache2.  The page you link to has a sample AppArmor profile for Apache2 described in step N.  Have you tried that yet in complain mode to see what it reports?  Where are you stuck?

---

### Post by lance bermudez on 2014-12-07
ok I copied what it said to /etc/apparmor.d to a file called usr.lib.apache2.mpm-prefork.apache2

sudo aa-complain usr.lib.apache2.mpm-prefork.apache2
Setting /etc/apparmor.d/apache2.d/usr.lib.apache2.mpm-prefork.apache2 to complain mode.

Do I have to do anything else? I have been checking /var/log/apparmor and do not see any thing yet.

check out the path /usr/lib/apache2/mpm-prefork/apache2 does not exist I have /usr/lib/apache2/modules

/usr/lib/apache2/modules$ ls | grep mpm
mod_mpm_event.so
mod_mpm_prefork.so
mod_mpm_worker.so

---

### Post by lance bermudez on 2014-12-08
below is what i came up with still testing

# Last Modified: Tue Feb  5 18:19:12 2013
#include <tunables/global>
 
/usr/sbin/apache2  {
  #include <abstractions/base>
  #include <abstractions/nameservice>
#include <abstractions/nis>
 
capability dac_override,
capability kill,
capability setgid,
capability setuid,
capability net_bind_service,
network inet,
network inet6,
 
  /bin/dash rix,
  /bin/which rix,
  /etc/apache2/apache2.conf r,
  /etc/apache2/conf.d/ r,
  /etc/apache2/conf.d/** r,
  /etc/apache2/httpd.conf r,
  /etc/apache2/mods-available/ r,
  /etc/apache2/mods-available/** r,
  /etc/apache2/mods-enabled/ r,
  /etc/apache2/mods-enabled/** r,
  /etc/apache2/ports.conf r,
  /etc/apache2/sites-available/ r,
  /etc/apache2/sites-available/** r,
  /etc/apache2/sites-enabled/ r,
  /etc/apache2/sites-enabled/** r,
  /etc/magic r,
  /etc/mime.types r,
  /etc/modsecurity/ r,
  /etc/modsecurity/** r,
  /etc/php5/apache2/php.ini r,
  /etc/php5/conf.d/ r,
  /etc/php5/conf.d/** r,
  # this ssl key should be change according to your ssl certificate
  /etc/apache2/ssl/owncloud.crt r,
  /proc/*/auxv r,
  /run/apache2.pid rw,
  /run/apache2/mutex wk,
  /run/apache2/ssl_mutex wk,
  /tmp/** rw,
  /usr/bin/file rix,
  /usr/lib{,32,64}/** mr,
  /usr/share/file/magic.mgc r,
  /usr/share/mysql/charsets/Index.xml r,
  /var/lib/apache2/fcgid/shm w,
  /var/lib/php5/** rwk,
  /var/log/apache2/** w,
  /var/log/apache2/modsec_audit.log r,
  /var/www/owncloud/ r,
  /var/www/owncloud/.htaccess r,
  /var/www/owncloud/3rdparty/** r,
  /var/www/owncloud/apps/ r,
  /var/www/owncloud/apps/** r,
  /var/www/owncloud/config/config.php r,
  /var/www/owncloud/core/** r,
  /var/www/owncloud/cron.php r,
  /var/www/owncloud/data/** rw,
  /var/www/owncloud/data/.htaccess r,
  /var/www/owncloud/index.php r,
  /var/www/owncloud/lib/** r,
  /var/www/owncloud/remote.php r,
  /var/www/owncloud/search/** r,
  /var/www/owncloud/settings/** r,
  /var/www/owncloud/status.php r,
 
 
  ^DEFAULT_URI  {
 
 
  }
 
  ^HANDLING_UNTRUSTED_INPUT {
 
 
  }
}

---

### Post by lance bermudez on 2014-12-08
# aa-notify -s 1 -v /usr/sbin/apache2
Profile: unconfined
Operation: change_hat
Logfile: /var/log/kern.log
(122 found, most recent from 'Mon Dec  8 14:57:49 2014')

AppArmor denials: 122 (since Sun Dec  7 15:02:30 2014)
For more information, please see: [https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

So dump question how do I see the denials? 
# cat audit/audit.log | grep /usr/sbin/apache2 | less
type=AVC msg=audit(1418076685.403:1864): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6881 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.419:1865): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/ssl-cache.6857" pid=6881 comm="apache2" requested_mask="wk" denied_mask="wk" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.423:1866): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/ssl-cache.6857" pid=6881 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.479:1867): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6881 comm="apache2" requested_mask="wk" denied_mask="wk" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.491:1868): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6865 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.543:1869): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/tmp/.ZendSem.YRTOYm" pid=6865 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076685.547:1870): apparmor="ALLOWED" operation="open" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/" pid=6865 comm="apache2" requested_mask="r" denied_mask="r" fsuid=33 ouid=33
type=AVC msg=audit(1418076685.547:1871): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/config.php" pid=6865 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=33
type=AVC msg=audit(1418076685.551:1872): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/config.php" pid=6865 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=33
type=AVC msg=audit(1418076685.563:1873): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/apache2" name="/run/mysqld/mysqld.sock" pid=6865 comm="apache2" requested_mask="rw" denied_mask="rw" fsuid=33 ouid=109
type=AVC msg=audit(1418076685.691:1874): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/tmp/.ZendSem.YRTOYm" pid=6865 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076692.712:1875): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6865 comm="apache2" requested_mask="wk" denied_mask="wk" fsuid=33 ouid=0
type=AVC msg=audit(1418076769.408:1877): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6863 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076769.420:1878): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/tmp/.ZendSem.YRTOYm" pid=6863 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076769.424:1879): apparmor="ALLOWED" operation="open" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/" pid=6863 comm="apache2" requested_mask="r" denied_mask="r" fsuid=33 ouid=33
type=AVC msg=audit(1418076769.428:1880): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/config.php" pid=6863 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=33
type=AVC msg=audit(1418076769.428:1881): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/var/www/owncloud/config/config.php" pid=6863 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=33
type=AVC msg=audit(1418076769.436:1882): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/apache2" name="/run/mysqld/mysqld.sock" pid=6863 comm="apache2" requested_mask="rw" denied_mask="rw" fsuid=33 ouid=109
type=AVC msg=audit(1418076769.548:1883): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/tmp/.ZendSem.YRTOYm" pid=6863 comm="apache2" requested_mask="k" denied_mask="k" fsuid=33 ouid=0
type=AVC msg=audit(1418076774.560:1884): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/apache2" name="/run/lock/apache2/mpm-accept.6858" pid=6863 comm="apache2" requested_mask="wk" denied_mask="wk" fsuid=33 ouid=0

So what do I do now?

aa-status | less
apparmor module is loaded.
44 profiles are loaded.
19 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/chromium-browser/chromium-browser//sanitized_helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/apache2//DEFAULT_URI
   /usr/sbin/apache2//HANDLING_UNTRUSTED_INPUT
   /usr/sbin/mysqld
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
25 profiles are in complain mode.
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//lsb_release
   /usr/lib/chromium-browser/chromium-browser//xdgsettings
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/apache2
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/{sbin/traceroute,bin/traceroute.db}
   /{usr/,}bin/ping
15 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (708) 
   /usr/sbin/mysqld (1174) 
   /usr/sbin/ntpd (1681) 
11 processes are in complain mode.
   /usr/sbin/apache2 (6858) 
   /usr/sbin/apache2 (6862) 
   /usr/sbin/apache2 (6863) 
   /usr/sbin/apache2 (6864) 
   /usr/sbin/apache2 (6865) 
   /usr/sbin/apache2 (6866) 
   /usr/sbin/apache2 (6873) 
   /usr/sbin/apache2 (6875) 
   /usr/sbin/apache2 (6878) 
   /usr/sbin/apache2 (6880) 
   /usr/sbin/apache2 (6881) 
1 processes are unconfined but have a profile defined.
   /usr/sbin/dnsmasq (758)

---

### Post by Lars Noodén on 2014-12-09
On Ubuntu 14.04 LTS, I find the AppArmor denied logs in /var/log/syslog and in /var/log/kern.log since I have not modified rsyslogd's configuration to filter out AppArmor into its own log file.  

Also, about grep, you can use it directly on a file without needing cat.

```
grep /usr/sbin/apache2 audit/audit.log | less

```

If you want to watch live, use tail

```

tail -f /var/log/kern.log | grep apparmor

```

After each change to the profile, you have to reload it and that will generate a small burst of messages before getting into the useful 'denied' messages.

---

