---
title: "Intel BG2200 Kill Switch"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by sbm on 2005-05-09
Hi

I have successfully connected to my WLAN router, which is using WPA encryption. I followed the guide found elsewhere on this forum.

Sometimes I am able to connect at startup.
Sometimes I need to restart the network in order to receive an IP from the router.
But the problem is, that sometimes the card is totally unactivatable. 
dmesg | grep ipw concludes that the drivers are correctly loaded but states the following error:
The Kill Switch is set to ON   (Probably not a 100% correct copy of the errormessage - but you know the meaning right)

The kill switch is not on. In other words, the network card is turned on. Why does this happen? Is it because I just used the nic on another network? Can it be dealt with?

/SBM

This is my final hastle with ubuntu. When the WLAN is implemented this distro will rock.

PS - Anyone know how to change file associations in gnome?

---

### Post by sbm on 2005-05-09
Just played with it.

If I connect to my WLAN from within windows, then reboots the machine and tries to connect using Ubuntu everything works great.
This is weird. It seems as if the ipw2200 driver (or the firmware) is not able to setup the device correctly, but is able to use it if it is configured.

Anyone with some thoughts?

/SBM

---

### Post by sbm on 2005-05-10
Found a possible solution. Haven't checked it yet. But should work:

[ Taken from [http://www.flawless.dk/znote4200.php](http://www.flawless.dk/znote4200.php) ]
laptop Zepto4200;
The wireless NIC is a MiniPCI Centrino 2200 802.11b/g, which works very well with the open-source intel driver ipw2200. You can get the latest version (1.0.1 at the time of writing) from the Intel page on SourceForge

An increasing problem with wifi on laptops, is that the wifi-radio is turned off by a "kill switch". This kill switch is either in hardware, software, or as in the case of the znote, both. Whenever the hardware switch is on, the software switch rules. If the hardware switch is off, no software command can make the radio work. If both switches are activated, the wireless LED will light up (orange).

You can activate it the following way: 
1.Download the program acerhk ([http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)) 
2.Compile acerhk 
3.Run "modprobe acerhk" 
4.Now you can turn on the radio with the command "echo 1 > /proc/driver/acerhk/wirelessled" 
Thanks to Sverry Johansen for finding these obscure commands on the web.

If things are working this far and you, like me, would like a little more automatic operation, download the modprobe configuration file and save it to "/etc/modprobe.d/wlan". Now every time you do "modprobe ipw2200" the acerhk module is loaded and turns your radio on, and every time you do "modprobe -r ipw2200", the acerhk module is unloaded and your radio is turned off. If you want ipw2200 automatically loaded on startup, just add "ipw2200" to "/etc/modules". If the file doesn't exist, just create it. 

/SBM

---

### Post by epb613 on 2005-05-12
a more detailed guide for that same laptop (cl56):
[http://heim.ifi.uio.no/~krisvh/linux/cl56.html](http://heim.ifi.uio.no/~krisvh/linux/cl56.html)

I have a cl56 and I followed the guide and it worked great.

---

### Post by ifrflyer on 2005-05-12
I had a very similar problem with the same card on a different notebook. I believe I have the answer to MY problem, and I have written a how to to share it. I can only hope someone makes a sticky and I hope it helps you

Problem:
Users of Ubuntu 5.04 with computers which use the Intel® Pro/Wireless 2200 802.11B/G WLAN experience troubles including:

* Intermittent connectivity
* Inability to switch between networks or regain a lost network connection without rebooting
* Inability to configure wireless connection using Network Connection GUI

Cause:
Ubuntu 5.04 Hoary Hedgehog ships with version 0.19 of the driver for this card. The current version is 1.0.3. The stable version is 1.0.0, and this is the version it is recommended to use with Ubuntu. Of course, you can try any version you like!

Solution:
Remove completely version 0.19 and upgrade to version 1.0.*


HOW TO:
[http://nickselby.com/articles/technology/index.htm?a=1807](http://nickselby.com/articles/technology/index.htm?a=1807)

---

### Post by epb613 on 2005-05-12
ifrflyer, his problem is unrelated to yours. His problem is that his bios doesnt automatically recognize his kill switch. When he boots into windows and turns it on, then the bios registers it until he cuts the power for a bit. He just has to install acerhk to get his problem fixed,

sbm, incidently, what model laptop do you have?

---

### Post by ifrflyer on 2005-05-12
Thanks epb. I couldn't be sure but this problem was so frustrating and it sounded pretty familiar! I did like that article on the kill switch as well.

---

### Post by luca_linux on 2005-05-12
Try to update the driver to 1.0.3. Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

