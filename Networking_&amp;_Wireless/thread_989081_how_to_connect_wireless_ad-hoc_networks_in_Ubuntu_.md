---
title: "how to connect wireless ad-hoc networks in Ubuntu !"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by Faraj on 2008-11-21
[SIZE="4"]Hi everyone.. i wana create an ad-hoc wireless network to share my internet connection with a nother laptop. The problem is i couldn't create one..

Can anyone please help me to :
[B]1) create an ad-hoc wireless network
2) connect the other computer to that network
3) and then share the internet...[/B]

plzzz im really helpless... i search hell of a lot of forums but couldn't find a method which works for me...[/SIZE]
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by superprash2003 on 2008-11-21
1) create adhoc network - [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)
2) what do you mean by connect to other computers?? file sharing??which OS does the other computer run?
3) to share internet connection you could use application called firestarter ( sudo apt-get install firestarter) it has Internet connection sharing(ICS) Feature

---

### Post by Faraj on 2008-11-21
no brother.. i numbered it as a sequence of steps to be done.. usually when we create an adhoc in windows to share internet we create it.. conect it and then share the internet.. thats wht im trying to say...

Anyhow i also needed to share files too. but before that i just cant figure out how to connect to computers in ubuntu.. so that it can be 'ping'ed.

yes bro.. i did wht you were told in your blog before.. and even now i gave it a try.. still cannot ping :confused: 

i have installed ubuntu 8.04

the error msg i get in one laptop is a bit different too.. it says access denied. i also pinged as a super user.. still no use..

but in the other laptop, it gets pinged but 100% loss :confused:

Wont i be able to get any software such as in windows to search for adhoc networks avaliable.. 

Bro im new to the world of linux.. plzz give me a hand to get rid of this windows..  it really f***s.

and i have the firestarter.. i was thinking it's a firewall. and it just disable the firewall restriction in internet sharing..

---

### Post by superprash2003 on 2008-11-22
are both the pcs running ubuntu?
firestarter is a GUI for iptables which is the firewall for linux (ubuntu).. you could deal with that later as you said. first its better to get both the pcs to ping..

---

### Post by Faraj on 2008-11-22
yes both th pcs run on ubuntu 8.04 OS
i did the whole bunch of steps that you were asked to do in ur blog... still ping is not working bro

it says something about "access denied" in one pc and in the other 'ping' works but not gets pinged..
this hapens even if i typed 

sudo ping ---.---.---.---
or
ping ---.---.---.---

more over eth1 is not working... it says about unidentified hardware..

i used 'wlan0' which can be configured

---

### Post by superprash2003 on 2008-11-24
wifi drivers have to be checked then.. go to the terminal and post output of following commands
1)iwconfig
2)lshw -C network

---

