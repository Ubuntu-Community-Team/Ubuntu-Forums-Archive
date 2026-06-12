---
title: "friggin same problem"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by sickdude on 2005-10-19
damned i installed a ubuntu server and it was running fine until i did a reboot from that point i knew this could go wrong (i hate rebooting)

and yes it did and it was the same friggin problem as i had with my old workstation

[http://ubuntuforums.org/showthread.php?t=74267](http://ubuntuforums.org/showthread.php?t=74267)

i cant get a new ip

and i bet when i put in a new network card it will work like a friggin charm

this sucks big time, are there more nic problems with ubuntu or do i have to install more nic drivers to this machine? it sucks because it worked and that is what i hate most

if anybody has any ideas please let me know

---

### Post by sickdude on 2005-10-20
anybody?

---

### Post by az on 2005-10-20
So, you cannot get a dhcp lease.

From a terminal, type

sudo /etc/init.d/networking stop
sudo dhclient eth0
and tell me what happens.  (You can check the logs using the log tool, too, for anything "funny")

also 

Show me
cat /etc/network/interfaces

---

