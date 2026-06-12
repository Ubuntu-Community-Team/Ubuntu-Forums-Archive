---
title: "Teething probl;ems with Ubuntu 9 10"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Blewog on 2010-03-04
[CENTER]Hello every body,
This is my first post to you.
I have just down loaded Ubuntu 9 .10 & it looks & feels nice.
However I have some teething problems that may be some one would like
to help & assist me sort out.

1 I have a Netgear Router, model number DG834GSP.
Can any one assist me with where to down load or buy the programs so that I can use Ubuntu with this router?
My connections to the out side world are done through windows XP,
So can my new Ubunto 9/10 system communicate with the router that is working on XP?
  
Or can some one tell me how to get the router working only on Ubuntu?

2. I cannot play DVD's on my computer, now that I have banished windows XP form my laptop. I purchased a disc from the Linux shop (Mythbuntu) but as yet I have not been able to down load the programme into my laptop.
When I try & play a dvd a fault window appears & say's no URI implemented for DVD's.

3 I purchased my third disc from the Linux shop in the UK. This disc & programme under question is a fire wall, but my system as with Mythbuntu does not seem to recognise the programmes on the disc, so what do I have to do to down load these programmes & to activate them properly?

Thank you for all for your time.

Yours truly
Blewog.
  

[/CENTER]

---

### Post by alexandari on 2010-03-04
Hello there

1. You don't have to buy anything. Usually,all routers access the settings by typing something like "192.168.1.1" in the browser (this works for me) 
If there is anything to install (I kinda doubt it),it should be from the package manager. Sorry I'm using Asus so I can't really help you with that

2. About that you can check -- [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) this 

3. You can find a firewall application in the package manager I think :)

---

### Post by nothingspecial on 2010-03-04
1. Is that one of those mobile broadband dongle thingys?

2. Open a terminal (applications > accessories > terminal) and copy and paste 
```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

3. You don`t really need a firewall with ubuntu. But if you must try firestarter.

---

### Post by nothingspecial on 2010-03-04
Oh yeah, and stop buying things ...... it`s all free, donate or contibute but you really shouldn`t have to buy anything linux wise.

---

### Post by 3rdalbum on 2010-03-04
1. Your router is a miniature computer - it establishes your internet connection and keeps it running even when your computers are turned off. You should just be able to plug the router into your computer via an Ethernet cable, and the Ubuntu machine will automatically get its connection from there.

2. Ubuntu does not come with DVD decryption software by default, due to legal reasons in certain countries. It can be easily added though, by using the Medibuntu website ([www.medibuntu.org](www.medibuntu.org)). Obviously you need an internet connection on Ubuntu to do this.

3. It's easiest to install programs using Ubuntu Software Centre or Synaptic Package Manager, which require an internet connection, but allow you to search for, download and install software with just a few mouse clicks.

---

