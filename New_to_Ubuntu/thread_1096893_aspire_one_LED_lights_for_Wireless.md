---
title: "aspire one LED lights for Wireless"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-03-15
ok. i know it not vital. but i want to get these working. i have the steps required to get them working but i dont know how to put the codes in. here it is

Wireless LEDs

    * the wireless leds need an entry in /proc
    * with wireless on/off works, but there is no notification in Gui 

"To get your wireless led to blink for you based on traffic, put these lines at the end of /etc/sysctl.conf."

dev.wifi0.ledpin=3
dev.wifi0.softled=1

Then either reboot or do sysctl -p

The led on the front will now do the association blink, as well as blink based on wireless traffic. 




can someone explain what i do with the /proc and /etc/sysctl.conf? how do i enter these what order and such? thanx in advance for the help

---

### Post by .:Justus:. on 2009-03-15
What it means is that you add a line to the .conf file.

Open up your terminal and type:

sudo su
gedit /etc/sysctl.conf

It will open a text like file, scroll to the bottom and copy paste the following :
dev.wifi0.ledpin=3
dev.wifi0.softled=1


Also, there is a different way of doing it than you described 
check out this link [http://code-hacker.wetpaint.com/page/Install+Ubuntu+on+Acer+Aspire+One?t=anon](http://code-hacker.wetpaint.com/page/Install+Ubuntu+on+Acer+Aspire+One?t=anon)

---

### Post by mspn on 2009-09-14
Hi,

Thanks for the info, just got Jaunty running nicely on my AAO.

Is there anyway to keep the Wireless LED blinking on traffic, but removing the association blink?

---

### Post by pie2mats on 2011-03-15
hello everyone!

wow, this post has been here quite a while but still a top ranking site on search engine. 
got the same idea though, but i won't recommend it, staying in on would mean disaster in case of glitch or power interruption. good day everyone!
[SIZE=2]
[/SIZE]   [SIZE=2]wireless   LED lights[/SIZE]    [SIZE=2][COLOR=Blue]http://www.easyontaillights.com/

[/COLOR][/SIZE]

---

