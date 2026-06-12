---
title: "Internet connection won't work..."
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by psychoadonis on 2007-05-04
Hi...

In windows, I use a ADSL connection (I think) with a cable modem which is connected to my phone line. The modem is called "Huawei SmartAX MT 882". Under network connections, the particular ethernet card for this connection is configured with an (apparently) static IP address and two DNS addresses. To use the internet, I just switch on the modem. No username/password required.

In Ubuntu, I tried to do the same under Network Settings, by configuring the card to the same address, and adding the two DNS addresses. After doing so, I get a "connected" icon near the date & time, but when I try to browse, fireox just says "looking up..." and after a while says page not available.

I've tried restarting the modem, with no effect. Any ideas?

I'm using Ubuntu 7.04 Feisty Fawn, directly form the CD (without installing).

---

### Post by Candace on 2007-05-05
Hi psychoadonis,
It really depends on exactly what the problem is, and I am not sure what questions to ask you, but  this is what I did. I don't know if you can get a wireless connection booting from the Live CD because as far as I know, any changes you make will be lost next time you boot up. Anybody else, any thoughts? So I think you need to install Ubuntu on your computer (which involves partitioning, et al), and then follow the instructions here (including link 2) to download the wireless driver (I used ndiswrapper) and change some files that came with Ubuntu. JHere's the link:

[http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

I just did this (also with 7.04) and my wireless internet is now working great! Good luck, if you have more questions, just post 'em. :)

---

### Post by sdide on 2007-05-05
Psychodanis,

I think you need to add at least a default gateway to make you setup work.

you should be able to determine your default gateway in wondows by doing
c:\ ipconfig /all  
(at least i think so)
Lets say you plug your cable into eth0 then you do (as root or with sudo)

~# ip r a default via <gateway_found_above_goes_here> dev eth0

---

### Post by psychoadonis on 2007-05-05
> **Candace said:**
> I just did this (also with 7.04) and my wireless internet is now working great!

I think you misunderstood... I'm using a wired connection.

And sdide, I've added the same IP, subnet mask, gateway and DNS as in windows.

---

### Post by sdide on 2007-05-05
please post (all commands executed as root or with sudo)

~# ip route 

~# cat /etc/resolv.conf

~# ip link

~# ip neigh

~# ip a show

---

### Post by Candace on 2007-05-05
Very sorry psychoadonis - I shouldn't stay up so late. My sincere apologies.

---

### Post by psychoadonis on 2007-05-05
Haha.. thats alright candace.

I'll need to make some space on my drive before I install, so I'll keep u posted sdide.. thanks

---

### Post by psychoadonis on 2007-05-10
hey sdide...

I cleared up my hdd, made some space and installed ubuntu.
Now my internet connection works just fine. I guess the problem was bcoz of trying to make it work from the live CD.

Thanks for all the help!!

---

