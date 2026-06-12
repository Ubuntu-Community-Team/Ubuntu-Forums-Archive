---
title: "Wireless &amp; WPA Help needed"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by greywolf79 on 2007-02-27
I am new to linux overall. I have installed about 6-10 versions and distros of linux over the years, but I am still very new to using and operating linux. I am currently using a laptop (Compaq Presario V2000 series V2607CL laptop from HP-Compaq). I have installed Ubuntu 6.10 onto it. I had done this previously with no problem in installing. On the previous installation I had even gotten the wireless card (broadcom 4318, airforce one 54g) to run using fwcutter with the 43xx module and the WPA Supplicant to connect to the WPA enabled router I use. It ran great. But then there was a major crash on windows (dual booting) and the partition for linux got messed up with the crash. I have reinstalled ubuntu now (and just not put windows onto the laptop at all). My problem now is that I have run the fwcutter and wpa supplicant programs and the wifi card is detected in the hardware list but not in networking or anywhere I would be able to use the wireless from. When I turn on the wifi card in the network settings it is turned off immediately and does not let me use the wifi. So I am reinstalling ubuntu right now to see if it will work with a clean slate. Is there a better way to do this? Like I said I am new to linux. I need easy right now and when I have learned more I will do more difficult stuff. I use a Netgear WG614 v6 wireless router at home for the wifi connection, and the broadcom card listed above is built into the laptop. Any help is greatly appreciated. Also, please list in a way a not so great user can understand. Step by step would also be appreciated. Thanks ahead of time for all the help.

---

### Post by srt4play on 2007-02-27
Take a look at this howto : 

[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

It's my experience that you will get better performance with ndiswrapper than the native driver.

I use that howto everytime I do an install on one of my laptops that has the broadcom 4318.

---

### Post by greywolf79 on 2007-02-27
Thank you for the fast response to my inquiry. I am going to try that and see if it works. I just need to get the wireless card up and running with WPA enabled so I can use my home connection... I _NEED_ wireless around the house... 2 little kids running all over the place so I cannot run cables on the floor and I live in an apartment, so no running cables in the walls. Lets hope this works. I will post any successes on the forum so everyone knows what I did and if it works (hopefully it will). Thanks again.

---

### Post by srt4play on 2007-03-15
Any updates?

---

