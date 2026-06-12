---
title: "Just put this in beginner thread. No responses after 1.5 hours. Help me please!!!"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by PreviousN on 2007-09-21
Hello,

I've got a ubuntu server that is "headless". I recently just plugged in a monitor so I could configure bridging. Below I will give what I currently have and then what I want:

== Current: ==
Ubuntu server (gigabit) ==> (gigabit) Windows (100mbit) ==> (dhcp 100mbit) router ==> cable modem

I've connected my server and windows together w/gigabit because I've got a buch of hard drives on the ubuntu machine and specifically, a raid that I use via a samba share on my windows computer to backup important documents. So, overall, my entire network runs on 100mbit, except for the connection between my windows and ubuntu server (using a crossover cable, of course).

== What I want ==
Windows (gigabit) ==> (gigabit)(eth1) ubuntu server (10/100)(eth0) ==> (dhcp) router ==> cable modem
Third computer ==> (10/100)(eth2) ubuntu server ----------- ^^^^^

side note: I've followed this guide somewhat: [http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu](http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu) and have managed to f*ck up my /etc/networking file. Does anyone have a default they can paste in that I can use? I forgot to make a backup...(opps)

So from what I understand I type in
{{ brctl addbr br0 }}
{{ brctl addif br0 eth1}}
{{ brctl addif br0 eth0}}
{{ brctl addif br0 eth2}}
{{ ifconfig br0 up }}
And sometimes that works...but I frequently (ok...like once a month) have to reboot my server . Since I administer it via ssh and need to access the samba shares, the fact that bridging doesn't start on boot is a pain. Especially considering that this computer doesn't have a keyboard, mouse, or display plugged in.

== what I need help with ==
How do I make it run on boot? Do I add these to my /etc/rc.d/local? Guidance?
A pasted in /etc/networks file. If these are "unique" just paste yours and I can probably figure it out myself.

---

### Post by Sef on 2007-09-21
Here is the [original thread]("http://ubuntuforums.org/showthread.php?t=556227").

Since this is a duplicate thread, I am locking it.

---

