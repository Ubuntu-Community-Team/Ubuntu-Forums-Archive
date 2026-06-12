---
title: "wierd network problem"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by nisse161 on 2008-07-24
Hello

I have a strange problem with my latest ubuntu-server. It is supposed to work as a filserver with a dc client and a azureus with webmanagement. 

I installed the latest version (8.04)  and soon realised that it seemed to be too new for my machine which is about 6 years old.
I kept getting ata errors similar to this [http://ubuntuforums.org/showthread.php?t=866983&highlight=drdy]("http://ubuntuforums.org/showthread.php?t=866983&highlight=drdy").

So i tried with older versions starting with 7.10 and 7.04. Still the same error. So i tried 6.10 and finaly it worked. I'm actualy using 6.06 since 6.10 took a long time booting for some reason.
Next step was to install a gui since i hate working with VI and i don't know any other program except nano which i'm not familiar with. I tried to install the gnome desktop.
```
sudo apt-get install gnome-desktop-environment
```
the server went through all packages that was going to be downloaded and began to download. when it came to about 20% it suddenly stops and fails to connect to the ubuntu archives. After several automatic retrys the install fails.

I tried again and again, I monitored my internet connection during the download and it was stable. Then i noticed that if i were to physicaly disconnect the network cable and then insert it again the download would proceed another 20%. To se if this was a internet or local problem i installed openssh and tried to connect with putty. It worked fine for about 10 seconds, then i got a connection error and a new session didn't work either. I also tried to ping the server which confirmed the results of the "openssh test" a.k.a. it timed out after a few seconds (to be sure I both pinged the sever and connected through ssh simultaneously, both failed at the same time.

I've got no idea why this is happening since it works just great on windows XP. Any help on the matter would be appreciated.

The specs are:

DELL dimention 8200
P4 1.8 Ghz.
512mb RDRAM.
64mb agp nvidia-card.
10/100 mbit network-card using the tulip driver.
sata controllercard with 4 internal ports.
6 HDDs, 2x500, 1x400, 1x250, 1x200, 1x40(OS).

---

### Post by nisse161 on 2008-07-27
Thx for all help... NONE!

I finaly solved the problem by discovering that the tulip drive is bugged. Somehow it takes control of the networkcard instead of the dmfe driver which is supposed to be used.

---

