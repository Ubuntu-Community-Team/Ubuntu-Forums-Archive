---
title: "No eth0 after install Xubuntu on Toshiba Satellite 4300"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by iahim on 2006-08-22
Hello,

I am wondering why Xubuntu 6.06 Live works perfect (I have eth0 configured and I can connect to internet) but there is no more eth0 after installing to HDD ? It's about a Toshiba Satellite 4300 laptop.
ifconfig says that there is no such device (eth0) but only lo.
I have a 3Com Model 3CCFE574BT pcmcia network card, and I have tried all possible bios settings and combinations.PCMCIA services seems to be started when I am looking at dmesg. 
About the bios - well, PCI has to be on IRQ 11 because that setting cannot be changed, it is omly displayed.

Do you have any ideeas ? What shall I try (besides another distro)?

Thanks.

---

### Post by GeorgeAD on 2006-08-23
I have the same problem, I think:

[http://www.ubuntuforums.org/showthread.php?t=239375](http://www.ubuntuforums.org/showthread.php?t=239375)

Are these any help:

[http://www.ubuntuforums.org/showthread.php?t=193794](http://www.ubuntuforums.org/showthread.php?t=193794)

[http://www.ubuntuforums.org/showthread.php?t=192049](http://www.ubuntuforums.org/showthread.php?t=192049)

?

---

### Post by iahim on 2006-08-25
Follow this link, it can solve your problem, it surely fixed my problem with Toshiba satellite 4300.
[http://www.linuxquestions.org/questions/showthread.php?t=454810](http://www.linuxquestions.org/questions/showthread.php?t=454810)
It says 
"I had a similar problem and what it came down to is "/etc/pcmcia/config.opts". If you copy the one that existed when you booted up the install cd to your drive after everythings setup then it'll fix the problem. One way of doing this would be;

(If your main linux drive is hda1)

sudo mkdir /mnt/hda1
sudo mount /dev/hda1 /mnt/hda1
sudo cp /etc/pcmcia/config.opts /mnt/hda1/etc/pcmcia/
sudo umount /mnt/hda1
reboot"

---

### Post by iahim on 2006-08-25
And by the way, I have copied all files from "/etc/pcmcia/" not just "/etc/pcmcia/config.opts".
It should work for you too.:)

---

