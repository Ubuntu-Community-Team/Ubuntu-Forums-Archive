---
title: "Networking gone pear shaped"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by x1zer0 on 2006-10-08
I decided to move my /home to a seperate hard drive, since then I cant get cant connect to the internet or my router. ifconfig does not show my eth0 and enabling eth0 in kde panel fails.

doing ifdown / ifup says network is down,

No DHCPOFFERS recieved
No working leases in persistent database - sleeping
/etc/dhcp3/dhclient-enter-hooks.d/debug: 23: Syntax error: Bad substitution

Does anyone know how I can reset my network settings or any ideas on how to solve this. Any help would be greatly appreciated :)

---

### Post by spd106 on 2006-10-09
Can you still the card in Device Manager or lspci? Can you check that the driver is being loaded? I can't help you much more without knowing what brand of card it is.

---

### Post by Iowan on 2006-10-09
Take this for the wild-eyed-guess that it is: Could it be that a symlink has gone bad - since it has to access a (now) external filesystem?
[http://www.ubuntuforums.org/showthread.php?t=260800]("http://www.ubuntuforums.org/showthread.php?t=260800")
Have you seen this one - anything useful?
[QUOTE=http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely.[/QUOTE]

---

