---
title: "network setup via Network configuration tool GUI"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by f76 on 2005-07-14
Hi all!/first post

I have tried searching but i need a pointer in the right direction.

I have 2 network cards one 3com and one NC100 Linksys. I used these on my old xp setup to connect to both dhcp<->internet and xbox simultaniously. 

Ubuntu has been great, installing dhcp and both network cards simultaniously.

the 3com is an older 10mbit card used for the dhcp=eth0
the Linksys is an newer 10/100mbit card used for the xbox=eth1

Each one on their own works fine but the eth0 keeps turning up as the default gateway nomatter how many times i save the eth1 as default gateway and then i cant access the internet. -or is something else the problem?

I dont have any trouble ftp:/stream:ing to my xbox or the internet but i have to disable one card at a time....

Can this be solved via the gui? or which config file do i need to edit?

---

### Post by f76 on 2005-07-14
Well maybe i solved the problem in by using gui.. 
I had to create a "place" or "location".. i dont know how it translates...

Lets see if it works on my next boot.

---

### Post by f76 on 2005-07-16
Nope, it didnt work on restart. btw networkmanager crashed on me :)

Maybe i need to configure this manually... 
Can anyone point me i the right direction to a FAQ or so?

---

### Post by skyboy on 2005-07-16
can you paste you /etc/network/interfaces 

you might have a mapping problem

---

### Post by f76 on 2005-07-29
well now it works automagically again. Connected to xbox&windows...

I dread the day i need to setup a new/differnt connectio and have to go through the same random process....

Maybe by then i can work this out via the shell...

As i said... Funny enough its working now..

---

