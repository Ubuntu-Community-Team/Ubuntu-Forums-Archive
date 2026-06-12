---
title: "committing network settings"
date: 2005-08-04
forum: Networking &amp; Wireless
---

### Post by digitalmouse on 2005-08-04
greetings programs!

thanks to some help in a recent thread ('Re: Internal Network Fine, Internet or WAN access.. FUBAR') i've gotten a little 350Mhz PII running Ubuntu in a server configuration.

during my original installation the machine was at home, and it happily grabbed the home dsl router settings (192.168.2.1) automatically, setting itself up with a net connection.

i moved the server to a colleagues office with a faster net access, and changed the router and other related setting to reflect the new network (10.0.0.0 range).  everything works great at the moment.

i made a test reboot to check for things that were to start automatically on boot, and notcied that the changes i made to the network settings were not kept, and reverted to the home (192...) settings.

my question is:  how do i go about commiting the changes i made so that they take effect permanently?  i'm guessing there are some files that need to have this info stored within, but i am not sure where to look.

any tidbits or hints are appreciated!

---

### Post by heimo on 2005-08-04
[QUOTE=digitalmouse] i'm guessing there are some files that need to have this info stored within, but i am not sure where to look.
[/QUOTE]

/etc/network/interfaces - for syntax [i]man interfaces

[/i]tool to check eth0: [i]ifconfig eth0

[/i]also check /etc/hosts

if any questions

ask

:)

---

### Post by digitalmouse on 2005-08-04
ah- perfect, knowing the files to change made things easier.  thanks!

---

