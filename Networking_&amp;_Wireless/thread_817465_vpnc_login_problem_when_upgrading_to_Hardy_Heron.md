---
title: "vpnc login problem when upgrading to Hardy Heron"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by JarG0n on 2008-06-03
Hello,

I just upgraded to Hardy Heron, and my existing vpnc conf file no longer
works.  It now asks me for a passcode, after I have entered my initial
password:

user@user-desktop:/usr/share/vpnc$ sudo
vpnc /home/user/vpn/myConfig.conf
[sudo] password for user: 
Enter password for user@[IPSec Gateway]: 
Passcode for VPN user@&#65279;[IPSec Gateway]:   <--- (variation)
vpnc: authentication unsuccessful

Here is my config file, that worked prior to the upgrade to Hardy:

IPSec gateway [gateway IP]
IPSec ID [group id]
IPSec obfuscated secret [hex code string]
Xauth username user
target networks [target network]

Can anyone tell me why this new version is prompting me for 
"Passcode for VPN user@[IPSec Gateway]:" above, when it didn't in Gutsy
Gibbon?  The current version shows as 0.5.1r275-1 (hardy).  I don't know what vpnc version existed in Gutsy.

---

### Post by JarG0n on 2008-06-19
Can anyone help me with this?

---

### Post by JarG0n on 2008-06-19
I think this bug has been cataloged here.

[https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/214399]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/214399")

---

