---
title: "[SOLVED] Help needed - /etc/network/interfaces"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-22
I've been trying to set up a simple version using the server edition but have problems with the network definitions.  I finally gave up and installed the desktop version just so I could use the /etc/network/interfaces file as a basis for one using the server edition.  Unfortunately, I am in a small catch-22:

My wireless USB adaptor was detected and works using the desktop edition, and I can connect to my network.  However, there are NO definitions except the loopback in /etc/network/interfaces.  With the desktop edition I was able to use network  manager to get my connection - the server edition is by default (and I'd prefer to keep it that way for now) text based.

A lshw -C network shows my internal ehternet card as eth0, and my wireless as eth1 even though they are not in the /etc/network/interfaces file, so I assume network manager is somehow taking care of these for me.

I need to know what the /etc/network/interfaces file should look like when:

* I have an internal network card
* I have a wireless adaptor that uses WEP 64bit with a key string of 10 regular numeric digits (not hex, not passphrase, just a ascii key)

I have looked online at a lot of how-to's, supposed explanations of the entries in /etc/network/interfaces, etc., but I don't seem to be able to work when I use the server edition (and therefore without network manager that I know of).

I would put both editions on the box I'm making the server on, but the hard disk for the OS only is pretty small so I can't dual boot, and I'm getting tired of installing 1 on top of the other each time I need to try something in the desktop edition so I can see what it should be in the server edition.  I have another box coming this week to be my Ubuntu desktop box, since I can't mess with my PC I use for working from home (legalities).

If anyone can help me with this or point me to something meaningful that can help me create my /etc/network/interfaces file as needed for my server I would GREATLY appreciate it!

Thanks in advance!
Dave :)

---

### Post by bluefrog on 2008-12-22
auto eth0
iface eth0 inet static
address 192.168.1.2  # your IP
netmask 255.255.255.0
gateway 192.168.1.1  # your gateway

auto eth1
iface eth1 inet dhcp   #if static change following above instructions
wireless-mode managed
wireless-essid your-ssid
wireless-key your-wep-key

---

### Post by anewguy on 2008-12-22
Thank you so much!  I'll try that out in the currently installed desktop version then if all goes okay reinstall the server version again.

Thanks!
dave :)

YES!!  I changed eth0 to dhcp and made eth1 static just as I will need when I reinstall the server edition and it worked great!!   THANKS!!

EDIT-EDIT:  Only 1 small change when using on the server edition -> eth1 no longer existed and was replaced by wlan0.  Very simple to change!  Thanks again!!

---

### Post by anewguy on 2008-12-23
> **bluefrog said:**
> auto eth0
iface eth0 inet static
address 192.168.1.2  # your IP
netmask 255.255.255.0
gateway 192.168.1.1  # your gateway

auto eth1
iface eth1 inet dhcp   #if static change following above instructions
wireless-mode managed
wireless-essid your-ssid
wireless-key your-wep-key

Just wanted to thank you!  When I tested with the desktop version it worked fine - went to server and just had to change eth1 to wlan0, otherwise that worked great, too!!  I now have my wireless ubuntu very simple server going (I guess basically as a NAS - I'm sharing a complete disk off it).

Thanks so much!
dave :P

---

### Post by Maverick1712 on 2008-12-23
I had the same problem, but did not change the interfaces file. For future reference, here is a guide about configuring your wireless connection using the command line:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

You can dump these commands into a script and have it go on start up, and everything works. 

Cheers,
Adam

---

