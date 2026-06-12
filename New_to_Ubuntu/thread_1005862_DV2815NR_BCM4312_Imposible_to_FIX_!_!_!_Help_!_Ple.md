---
title: "DV2815NR BCM4312 Imposible to FIX ! ! ! Help ! Please"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Sibko on 2008-12-08
Hi everyone,
This are my specs:
Computer Hp pavilon DV2815nr.
Wireless> BCM4312 (rev 01)
Ubuntu 8.10 (intrepid) 
Kernel 2.6.27-9-generic

Everything Works perfect Except the Built-in Wireless.
I've tried all of this solutions in both 8.04 hardy and 8.10 intrepid.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312)

[http://ubuntuforums.org/showthread.php?t=961454](http://ubuntuforums.org/showthread.php?t=961454)

the classic: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

:confused:And the OFFICIAL VERSION from BroadCom too!!! :

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

In every case the installation process was successful, but then again, with the official drivers  (or any other) installed i get this msg when i tried to connect to my non protected router "(disconnected) THE NETWORK CONNECTION HAVE BEEN DISCONNECTED"
I can see all the wifi's around me and when ever it's procesing the request after taking it's time, it just sends that msg, if like i unplugged the cable somehow....
We have a MacBook in the house and it works fine, so it's not the router.
I use this computer for work and i love Linux there has to be a way to make this BCM4312 (rev 01) Work. Plase Help !!!!!!  

:mad:

---

### Post by newbee70 on 2008-12-08
> **Sibko said:**
> Hi everyone,
This are my specs:
Computer Hp pavilon DV2815nr.
Wireless> BCM4312 (rev 01)
Ubuntu 8.10 (intrepid) 
Kernel 2.6.27-9-generic

Everything Works perfect Except the Built-in Wireless.
I've tried all of this solutions in both 8.04 hardy and 8.10 intrepid.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312)

[http://ubuntuforums.org/showthread.php?t=961454](http://ubuntuforums.org/showthread.php?t=961454)

the classic: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

:confused:And the OFFICIAL VERSION from BroadCom too!!! :

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

In every case the installation process was successful, but then again, with the official drivers  (or any other) installed i get this msg when i tried to connect to my non protected router "(disconnected) THE NETWORK CONNECTION HAVE BEEN DISCONNECTED"
I can see all the wifi's around me and when ever it's procesing the request after taking it's time, it just sends that msg, if like i unplugged the cable somehow....
We have a MacBook in the house and it works fine, so it's not the router.
I use this computer for work and i love Linux there has to be a way to make this BCM4312 (rev 01) Work. Plase Help !!!!!!  

:mad:

Have you went into administration hardware drivers to see if yours is activated?

Have you left clicked on your internet connection icon and activated your wireless?

and then right click on your internet icon to activate wired and wireless
communications.

I think that is the order, but don't make me promise.

---

### Post by Sibko on 2008-12-08
Yes,
The connection is active and i can browse the different wireless networks, but it's impossible to establish the connection. 
The hardware and "soft" seem to be perfectly, but i still think it's a problem with the drivers from BroadCom co.
I need to solve this as soon as possible it's my work tool. 
Thanks for the help anyway.

---

### Post by andrew.46 on 2008-12-09
Hi,

Well I am running exactly the same chip:

```
andrew@skamandros:~$ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

And the good news is that it runs beautifully under Intrepid Ibex. My own installation method was for the required firmware:

[LIST=1]
[*]Install the b43-fwcutter package from the repository
[*]Run the script: /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
[/LIST]

I had a few problems with the Network Manager and this chip so I installed [wicd]("http://wicd.sourceforge.net/"). There are instructions on [the download page]("http://wicd.sourceforge.net/download.php") for setting up repository access and an important warning that the Network Manager will be uninstalled.

Reboot, having first crossed your fingers, and hopefully like me you will have troublefree wifi access :-).

  Andrew

**Edit:** Just had a look at those guides you mentioned. I managed without all that complicated stuff :-).

---

### Post by Sibko on 2008-12-09
Ciao,:roll:
Andrew thanks for your proposal but it seems it's not possible to establish a connection, it's waiting to obtain an Ip and then it's simply disconnected after 45 seconds, then i have this small (!) icon on the icon tray connection from Wicd Manager as if there was a conflict...

All the connections are displayed and the program runs really smoothy, but does not connect i verify and over verify my router, everything it's neat.:-({|=
I tried to connect to other wifi and nothing, I assign static IP and it connects 100% but in the manager it appears as "not connected" and off-course there's no packages flowing....

Is there  a procedure to completily remove the firmware better than b43fwcutter... how do i know it's actually blocking it... i still have the display of the broadcom sta wireless driver, not active off-course but it's still there.

Is there a way to make mi wireless WORK !!!!?

should i re install 8.10 (intrepid)  everything again and try the Wicd method again.
Thank you so much for your support, i hope this will be solved soon.
](*,)

---

### Post by Sibko on 2008-12-12
\\:D/Thanks everyone for your help,
but it seems that i complicate my life more than i should.
My Wife save my ***, she is awesome.
Now the problem is solved.
She has the most amaizing *** EVER!!
Im gonna buy her a new pair of shoes and she's going to get to pick them.
Love ya all. 
Thanks again !
:P

---

### Post by Michael.Godawski on 2008-12-12
> \\:D/Thanks everyone for your help,
but it seems that i complicate my life more than i should.
My Wife save my ***, she is awesome.
Now the problem is solved.
She has the most amaizing *** EVER!!
Im gonna buy her a new pair of shoes and she's going to get to pick them.
Love ya all. 
Thanks again !

Would be nice to know what your wife did :p...

---

