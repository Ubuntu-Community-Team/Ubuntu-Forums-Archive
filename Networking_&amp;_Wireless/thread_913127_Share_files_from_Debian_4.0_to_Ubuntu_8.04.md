---
title: "Share files from Debian 4.0 to Ubuntu 8.04"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by linuxisevolution on 2008-09-07
I want to be able to share the /home/guest directory on the debian machine to the /home/guest directory on the Ubuntu 8.04 machine.

specs:

Pentium 3 550mhz 64mb ram debian 4.0 xfce desktop ( runs okay ) ip = 192.168.1.125


hardy machine:

c2duo 4gb ram 250gb X 2. kde4.1 ... ip= 192.168.1.103

How can i do this? I don't care if its nfs or samba. whichever is easiest :)








EDIT: I tried the directions from [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")
but i get this:

sudo mount 192.168.1.125:/home/guest ~/guest
mount: wrong fs type, bad option, bad superblock on 192.168.1.125:/home/guest,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



THANKS!

COULD SOMEONE PLEASE ANSWER!!!??? I HAVE A LOT TO DO TODAY AND I CAN'T WAIT TEN HOURS FOR THIS! EVEN IF YOU DON'T KNOW, JUST ANSWER!!!!!!

---

