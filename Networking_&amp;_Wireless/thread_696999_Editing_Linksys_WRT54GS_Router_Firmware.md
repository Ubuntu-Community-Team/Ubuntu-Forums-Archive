---
title: "Editing Linksys WRT54G/S Router Firmware"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by kool_kat_os on 2008-02-14
Is there any way that I can edit the linksys WRT54G/S firmware...i.e. changing the logos and stuff like that.

---

### Post by mrsteveman1 on 2008-02-14
You mean the stock firmware? 

If you really want to alter the firmware on a linksys box you are better off using DD-WRT or another similar project.

---

### Post by kool_kat_os on 2008-02-14
i used dd-wrt....it make me get a new router:(

---

### Post by mrsteveman1 on 2008-02-14
You mean it bricked itself somehow? There are ways to recover from that, but for now what is the goal here?

If you really want to there are certainly ways to change things about the stock firmware, but it's not easy to do.

---

### Post by Linux Lurker on 2008-03-09
> **mrsteveman1 said:**
> You mean the stock firmware? 

If you really want to alter the firmware on a linksys box you are better off using DD-WRT or another similar project.

I'm no expert, but I was able to follow their directions for my newer WRT-54Gv8 (Walmart Special) router.  Granted, because the v8 only has 2meg flash ability I had to use DD-WRT micro version.... but following the directions [here]("http://www.dd-wrt.com/wiki/index.php/How_To_Flash_the_WRT54Gv8") EXACTLY worked just fine for me.
*For anyone contemplating flashing using DD-WRT... Make SURE you read all applicable data on their site.  Start [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices"), with their supported hardware section and read it all.  I just wanted to point out that the WRT54G comes in at least 8 different versions, and most require different steps. *

The administration interface changed of course.  But, I couldn't see a whole hell of a lot of added functionality.  As expected from their description of the "micro" version flash.  The main thing I noticed was that it added UPnP (auto port forwarding) ability.  So, it's kinda cool that KTorrent's  UPnP plugin works with it now.

The main reason I wanted to flash it is because this is the **THIRD** WRT53G I've had that bricked itself after running torrents all night.  When it was a windows box I ran utorrent.  Worked fine for a few weeks, then suddenly dead.  Tried all the "bring em back to life" techniques from  the web, but they didn't help.  Best technique I tried?  Take it back to Wally World. :)

Then, after installing kubuntu and running KTorrent... same problem... only it happened even sooner.  So, I decided to try to find better firmware.  That's what brought me to the DD-WRT site.
Now, I still have the problem with running KTorrent and it eventually killing my connection.  However, unplugging the router for a minute and plugging it back in resets it.  Before, it would have just been forever dead.

The only settings area that I found applicable to this problems looks like this:
================
IP Filter Settings (adjust these for P2P)

Maximum Ports                     4096          (Default: 4096, Range: 256 - 4096)
TCP Timeout (in seconds)    120            (Default: 3600, Range: 1 - 86400)
UDP Timeout (in seconds)    120            (Default: 120, Range: 1 - 86400)
================

When you click on "more..." which provides additional help, it says only this:

   *_ IP Filter Settings (adjust these for P2P)_*
If you have any peer-to-peer (P2P) applications running on your network please increase the maximum ports and lower the TCP/UDP timeouts. This is necessary to maintain router stability because peer-to-peer applications open many connections and don't close them properly. Consider using these:

        * Maximum Ports: 4096
        * TCP Timeout: 120 sec
        * UDP Timeout: 120 sec

So I guess that would be the explanation as to why my routers kept dying - "poor router stability".
But, to be honest, it's not all that much better... except when it dies, I can wake it back up with a simple unplugging.  (I think in all my searching I found something that said this router in particular experienced problems when running torrents.)
[I][B]
Does anyone know how to adjust this for more stable results???[/B][/I]

---

### Post by mrsteveman1 on 2008-03-09
One of the problem with these boxes is that the chips have no heatsinks whatsoever, so to help things a bit i installed some custom heatsinks on all the hot chips in the device:

[http://i141.photobucket.com/albums/r65/mrsteveman1/IM000395.jpg]("http://i141.photobucket.com/albums/r65/mrsteveman1/IM000395.jpg")

What is interesting is that the switching chip gets hotter than anything else on the board, even with that heatsink (its on the left), the thing is very hot, but the CPU in this thing is now room temp.

The other thing is i got tired of DD-WRT, both because i don't like the project and the things they have done recently, and because it doesn't seem all that stable to me. Plus, they haven't implemented QoS correctly so it doesn't actually work very well.

I switched my WRT54Gv2.2 to Tomato firmware the other day and I like it a lot more, QoS works, the system is stable and fast, and it has a much nicer interface that doesn't need to restart the entire box every time you change a setting, it just restarts individual services.

---

### Post by Linux Lurker on 2008-03-09
> **mrsteveman1 said:**
> I switched my WRT54Gv2.2 to Tomato firmware the other day and I like it a lot more, QoS works, the system is stable and fast, and it has a much nicer interface that doesn't need to restart the entire box every time you change a setting, it just restarts individual services.

After posting, I did some more reading, and stumbled upon Tomato.  Unfortunately, it only supports WRT54G v1-v4... nothing beyond v4.
So, as a result of my further research, I've opted to return this v8 after I order and receive a WRT54GL.  DD-WRT and Tomato both fully support the GL (which seems logical), and everyone seems really happy with it.
Many people on the Tomato micro [thread]("http://www.linksysinfo.org/forums/showthread.php?t=52896&page=10") have been waiting and hoping for a micro-Tomato, but it seems to be going no where.  I've decided not to wait around and hope, when it will only cost me a few bucks more to get something already proven, (the GL).

---

### Post by mrsteveman1 on 2008-03-10
The newer Linksys boxes aren't that nice anyway, they have very poor antennas and poor range. The GL boxes (and the older < v4 boxes) have more flash, more ram and seem to be more stable.

---

### Post by stoeptegel on 2008-03-11
> **Linux Lurker said:**
> 
Then, after installing kubuntu and running KTorrent... same problem... only it happened even sooner.  So, I decided to try to find better firmware.  That's what brought me to the DD-WRT site.
Now, I still have the problem with running KTorrent and it eventually killing my connection.  However, unplugging the router for a minute and plugging it back in resets it.  Before, it would have just been forever dead.

The only settings area that I found applicable to this problems looks like this:
================
IP Filter Settings (adjust these for P2P)

Maximum Ports                     4096          (Default: 4096, Range: 256 - 4096)
TCP Timeout (in seconds)    120            (Default: 3600, Range: 1 - 86400)
UDP Timeout (in seconds)    120            (Default: 120, Range: 1 - 86400)
================

When you click on "more..." which provides additional help, it says only this:

   *_ IP Filter Settings (adjust these for P2P)_*
If you have any peer-to-peer (P2P) applications running on your network please increase the maximum ports and lower the TCP/UDP timeouts. This is necessary to maintain router stability because peer-to-peer applications open many connections and don't close them properly. Consider using these:

        * Maximum Ports: 4096
        * TCP Timeout: 120 sec
        * UDP Timeout: 120 sec

So I guess that would be the explanation as to why my routers kept dying - "poor router stability".
But, to be honest, it's not all that much better... except when it dies, I can wake it back up with a simple unplugging.  (I think in all my searching I found something that said this router in particular experienced problems when running torrents.)
[I][B]
Does anyone know how to adjust this for more stable results???[/B][/I]

Try lowering the max number of connection setups in KTorrent setting, 10 would be safe but i expect linksys to be able to do more.

---

