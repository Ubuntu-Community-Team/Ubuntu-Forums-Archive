---
title: "Cant connect with ethernet cable"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by revenge2 on 2008-07-06
Hey guys, ive had ubuntu installed on my dualboot comp or awhile now and i havent yet been able to connect to the internet using it.  When i plug the ethernet cable in and run any online app, it doesnt work. 

I am very keen on trying out linux but i cant really do anything without the internet.  Could someone please help me out.

-Thanks rev2

oh and im using ubuntu 7.10

---

### Post by Bubba64 on 2008-07-06
Have you opened the network manager to try and set it up, a easy way may just to set the wired on roam and let it do the voodoo that it does.

---

### Post by revenge2 on 2008-07-06
yeah i did, but what do you mean by set it on roam?

---

### Post by Bubba64 on 2008-07-06
[QUOTE=revenge2;5328779]yeah i did, but what do you mean by set it on roam?[/QUOTE

open network manager click on wired then properties then the roam box in the top left corner. This has worked for me to save time.

---

### Post by revenge2 on 2008-07-06
yeah i just did that, then i opened firefox and it said connecting for a long period of time and nothing happend. And my internet works fine on windows. So how do i fix it?

---

### Post by Bubba64 on 2008-07-06
> **revenge2 said:**
> yeah i just did that, then i opened firefox and it said connecting for a long period of time and nothing happend. And my internet works fine on windows. So how do i fix it?

have you tried turning off your router then on then doing a restart with this newest attempt, sometimes this works. I would also check how your computer is set for connecting to the net on my laptop it is called network proxy on Gutsy, mine is a direct connection. This getting things to work can be frustrating and usually requires several systems to be configured, there is no one thing which will get it going.

---

### Post by revenge2 on 2008-07-06
Hey there, unfortunately the problem persists. It now says connection times out on ff.
Im using the same ethernet cable (runs from a dlink modem) that im using on windows to post this message. And this is the same cable i use to test whether ubtunu connects. (i take it off and put it back, dont have two cables lol.)

What should i do?

---

### Post by dfreer on 2008-07-06
I'd open the command line in Windows, figure out the IP settings, and then do the same in Ubuntu. It may be your Windows machine is configured for a static IP address.

Windows: Start > Run. Type "cmd" and press <Enter>. It should bring up a DOS-Like window, the command prompt. Type:
```
ipconfig /all
```

And then copy + paste that here.

Ubuntu: Applications > Accessories > Terminal. Type:
```
ifconfig -a
```
And then copy + paste that here.

---

### Post by revenge2 on 2008-07-06
>----------under windows-------<
win-ip-config-
host name :616044914e
primary dns suffix:-
node type: unknown
ip routing enabled:no
wins prxy enabled:no

ether adapter local area connections-
media state:media disconnected
description:SiS 900-Based PCI Fast Ethernet Adapter

>-------under ubuntu-----<
etho  link encal:Ethernet Hwaddr 00:0B:6a:5A: DA:B8
      UP BROADCAST MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 fram:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 b) TX bytes:0 (0.0b)
      Interrupts:16 Base Address:0xd400

lo    link encap:local loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      UP LOOPBACK RUNNING MT:16436 Metric:1
      RX packets:0 errors:0 dropped:0 overuns:0 frames:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txquelen:0
      RX bytes:0 (0.0b) TX bytes:0(0.0b)


yeap..thats what it says..:)

---

### Post by thewebpromoter on 2008-07-20
hey there revenge2, 

let me first advise you the term "roam", it is equivalent to the window's network config as "Obtain IP Address Automatically" and "Obtain DNS Automatically", "roam" is the term Ubuntu uses.

Then, I saw when you paste the result of your ipconfig /all under Windows, that you are using SiS ethernet/LAN Card which is not compatible with Ubuntu, I had the same LAN Card brand built-in to my PC that cause me to buy another one which is LinkSys as it works on Ubuntu, Realtek works also in that OS.

I am also researching for a way to let SiS LAN Card work on Ubuntu but I cant find any...Can somebody help me? Thanks....

---

### Post by KaneSOT on 2009-04-26
I also Need Help with SiS lan ....dang I blew my old Motherboard:(

---

