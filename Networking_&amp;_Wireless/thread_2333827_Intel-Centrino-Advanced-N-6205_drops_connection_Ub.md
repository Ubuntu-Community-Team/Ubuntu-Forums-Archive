---
title: "Intel-Centrino-Advanced-N-6205 drops connection Ubuntu-16.04"
date: 2016-08-13
forum: Networking &amp; Wireless
---

### Post by ax-lx on 2016-08-13
:( Hello all

i have a hp-2760p and i described my bigger problem with this wifi connection here:
[https://ubuntuforums.org/showthread.php?t=2328244&p=13506382#post13506382](https://ubuntuforums.org/showthread.php?t=2328244&p=13506382#post13506382)

its another problem is: sometimes its wifi wireless connction drops without any known reason even after only 2 minutes connection and without any load of data transfer.

after disconnecting (as described in above link) i must do "service network-manager restart" as root to connect again ( its reason was described in the above link or thread) , thus i saved the /var/log/syslog from the moment of stating the network-manager service in pastebin here: [http://pastebin.com/y5K8V6SB](http://pastebin.com/y5K8V6SB)
and the output of wireless-info script is here: [http://paste.ubuntu.com/23051856/](http://paste.ubuntu.com/23051856/)

the disconnection is shown in /var/log/syslog as line bellow:
Aug 13 17:29:39 hpk1604 kernel: [664038.588250] wlo1: disassociated from D-link-932-MAC (Reason: 3)
( is existed in pastebin above )
Do anyone know what is "reason 3" in above log report ?

please help me to solve above problems
Thanks a lot

---

