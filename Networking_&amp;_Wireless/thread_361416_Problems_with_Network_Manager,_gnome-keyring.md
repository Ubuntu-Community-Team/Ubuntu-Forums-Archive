---
title: "Problems with Network Manager, gnome-keyring"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by timjay73 on 2007-02-14
Using Broadcom 43xx 802.11g wireless card with network manager.

when i first set it up with [_this tutorial_]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") it was working flawlessly. 

i was getting to close to being annoyed about having to enter the gnome  keyring password everytime i booted up. well, today i got what i wished for b/c it didnt ask me for it and i havent been able to get on wifi since. 

system>administration>network eth1 and wlan0 disabled
deleted file  ~/.gnome/keyrings/default.keyring
    - no change - didnt ask me to give a new one nor did it make a new one.
deleted folder  /tmp/keyring.xxxx/ 
    - no change - but it put in a new one

i can still wire in but that's it. what can i do?

---

### Post by timjay73 on 2007-02-17
bump

does anybody have any ideas? i've been stuck on xp since, and i'm really missing ubuntu.

---

### Post by timjay73 on 2007-02-21
bump. 
again.

hello? does anybody have any idea as to what i could do? is this too hard of a question/problem for people? do you need more information? 

dont fail me now ubuntu.

---

### Post by dekalbave on 2007-02-21
> **timjay73 said:**
> bump. 
again.

hello? does anybody have any idea as to what i could do? is this too hard of a question/problem for people? do you need more information? 

dont fail me now ubuntu.

Are you using the newest kernel?  There are a lot of problems with that.  I had to revert back to using the old one.

---

### Post by MighMoS on 2007-02-21
Try manually typing in the network to connect to, and the key (if any) under "Connect to other wireless network".  I've gotten the issue before, and that usually fixes it (there happen to be three networks in my neighborhood named "linksys", and my roommates refuse to change router names.

---

### Post by timjay73 on 2007-02-21
Thank you so much for responding!

@dekalbave
i'm using 6.06 dapper. that's not the newest kernel is it? or is it? i got a cd sent to me from linux

@MighMoS
when i try to connect there is no longer a list of available networks in the drop down menu and there usually are two or three other networks that windows sees. i have changed the network name multiple times along with the password, thinking that it was stuck on a certain ssid but nothing helped.  when i try to manually connect the icon just stays blue with those little dots and it goes around and around and around and never connects.

---

### Post by robbie75 on 2007-02-21
Hi,
try installing gnome keyring manager, so that
you can inspect/delete all the keys in your keyring ;)

Moreover, you can make network-manager stop asking
to unlock the keyring at each boot simply follwing the tutorial
on this forum (Tried just few days ago and it worked flawlessly ;)

Rob

---

### Post by timjay73 on 2007-03-01
havent been able to use ubuntu b/c of lack of wireless. today was the first attempt

installed gnome keyring manager didnt help. 
whenever i open gnome keyring manager it says "Error: no such keyring." what does that mean? 
when i go to view>keyrings there is only one by the name of "session"


when that didnt work. i completely removed them through synaptic and then reinstalled them. that didnt help either
i am frustrated. this is my first time back on ubuntu in a week and it's a no go.

is there another wireless program that i could try?

---

### Post by robbie75 on 2007-03-03
Yes, you can try wifi-radar but, IMHO network-manager
is more friendly and more "laptop-oriented" :)

---

### Post by timjay73 on 2007-03-03
if network manager is superior what can i do to go back to the way network manager it was? is there a way to "restore" all of the settings and files?  i thought that by going through synaptic and marking it for complete removal and then reinstalling it would have done that but i guess not. 

are there residual files/folders left by network manager that can be deleted so that it has to recreate them instead of using the ones that were leftover? does that make sense?

---

### Post by robbie75 on 2007-03-03
Uhmmmm if you select all the packages regarding network manager
for "complete removal" in synaptic this should wipe out everything
along with configuration files.
However I think that you have some problem with the keyring since
you say that the keyring manager returns an error when tryng to
access your keyring....
I think you should locate and delete you keyring file and then retry with
network manager.
HTH :)

---

### Post by timjay73 on 2007-03-03
Success!! at least partially.

i did a "complete removal" of anything i could find related to network manager and gnome keyring.  rebooted.

installed:
network manager
network manager - dev
network manager - dbg
network manager - gnome
network manager - gnome dbg

rebooted.

now i can see the wireless access point but am unable to connect to it. i get one green light but it says it's waiting for the network key or something. why cant i connect? is it waiting for the keyring? 

what should i do at this point? is there something i'm missing? 

i'm so close i can taste it. mmm....delicious.

---

### Post by timjay73 on 2007-03-03
Success!! Complete Success!!

i tried it one last time after i rebooted for the millionth time and it took. it even asked for my default keyring password. yaaahhhaaa!!!!!! hopefully i dont screw it up. i'm not touching anything related to wireless again. whew

thanks for all your help

---

