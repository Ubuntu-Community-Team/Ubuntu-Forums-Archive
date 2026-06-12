---
title: "[SOLVED] winbind does not ping hostnames without .local in the end"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-09-23
Good day!
I have installed winbind and it shows netbios names finally, but it does it in a strange way:
ping server runs fine. 'server' has a static IP and it is a master browser in Samba. Pinging client machines is impossible without .local in the end, i.e:
> peter@lion:~$ ping cheetah
ping: unknown host cheetah
fails, and > peter@lion:~$ ping cheetah.local
PING cheetah.local (192.168.0.45) 56(84) bytes of data.
64 bytes from cheetah.local (192.168.0.45): icmp_seq=1 ttl=64 time=3.74 ms
64 bytes from cheetah.local (192.168.0.45): icmp_seq=2 ttl=64 time=0.247 ms
works...
Why does it happen and is it possible to get rid of the .local in the end? Winbind is installed everywhere.

Thank you,
Peter.

---

### Post by Iowan on 2008-09-23
A [similar]("http://ubuntuforums.org/showthread.php?t=851447") thread - unfortunately, still unsolved.
Check **/etc/hosts** file to see if .local is attached.

---

### Post by PryGuy on 2008-09-24
Thanks for the response! It appears that I have mixed up things a bit... :-\"

The syntax 'hostname.local' belongs to [Avahi]("http://en.wikipedia.org/wiki/Avahi_(software)"). It's a Zeroconf implementation and it is not connected with Winbind. Winbind is to be installed with Samba or you won't see your computer pinging it from another computer in your LAN. In two words, Winbind just shows the hostnames that are in your Samba network. The thread is solved now!

EDIT: You can install mdns-scan to see mdns (Avahi) resources.

---

