---
title: "Absolute Beginner FTP question"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by hoptimusPrime on 2010-03-28
hello

i am still quite new to linux and i am having trouble getting an ftp server set up.  i want to be able to access my home folder in my appartment from anywhere i have internet access.

my current isp sends me a dynamic ip which is the reason i have had many problems

i have one computer i want to use as a server/media center in my living room.  so far, i have set up a static dhcp and port porwarding (i think), and the ip seems to not be changing when i reboot : )  internet and networking seems to be working fine

if i am within my network at home, i can access the 192.168.... ip from a web browser or nautilus, and i can see my home directory and access files fine.  

but say for instance i'm in an a wireless hotspot at school, and i want to access my files at home.  when i try the 192.168.1.... ip, it does not connect to anything.  so this is where i am stuck.

any help please?  which ip do i use if i want to connect from outside my network?
thanks!

---

### Post by PocketDog on 2010-03-28
The static address you set up only relates to your home network - 192.168.*.* is the IP address your *router* uses to talk to your PC. If you go to [www.whatsmyip.org](http://www.whatsmyip.org) you'll see the IP is different.

This is just an explanation why it doesn't work; for an explanation of how to make it work you'll need a better expert than I, but you'll probably need something like [VNC](https://help.ubuntu.com/community/VNC)

---

### Post by hoptimusPrime on 2010-03-28
so should i maybe scratch the whole ftp idea? 

i just want an easy way to access my music and movies on my computer at home, which is running off a dhcp ip.  

sorry for the poor terminology

---

### Post by gmargo on 2010-03-28
There are multiple web sites out there that will give you a domain name for your dynamic IP address. I use [www.dyndns.org]("http://www.dyndns.org"). Use the **ddclient** package to keep the IP address updated.

---

### Post by roger_1960 on 2010-03-28
Hi

Have you considered using dropbox?  [www.getdropbox.com](www.getdropbox.com)

---

