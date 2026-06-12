---
title: "[SOLVED] Netgear WG111v3 and WEP security"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by IanB2 on 2007-11-30
Please please please will someone help ...... I posted problems I was having with stability for a WG111v1 and as I got no replies I decided to buy a new Netgear adaptor in the hope I would get one that 'just worked' ....... oh dear!!!

I've managed to get the WG111v3 working using NDISWRAPPER and can connect to my network PROVIDED the WEP security is turned off. I've been unable to find any discussion on this problem and would be extremely grateful if you can help me work out what is the problem.....

As soon as I turn on the WEP encryption the wireless network continually asks for the passphrase (which I know is correct as I used cut,copy,paste and have double checked it several times), and I cannot get onto the network. I have a laptop using a WG511 which connects with no problems.

:confused:

---

### Post by mdurham on 2007-12-05
I'm having the same problem with a  WG111 V3, it works ok without security but not with it.
If anyone knows an answer to fix this I'd be extremely interested to hear it.
As a matter of interest it works ok under Win XP of course but, I have another WG111 V3 and if I remove the working one and plug in the second it only works for about 60 seconds then drops out.
I discovered that re-installing the setup software wizard thing the second one works ok but the first one drops out after 60 secs.
So it looks like changing the adapter requires re-installing the software. Very strange that it will work for a short time and the die.

Cheers, Mike

---

### Post by mdurham on 2007-12-09
I finally got the WG111 v3 to work by:
disconnect my wired connection
plug in the WG111 v3
using the manual network config
disable roaming
insert the ESSID
Password type: WEP key (hexadecimal)
paste the hex code obtained from the router (I obtained this with a wired connection)
Configuration: Automatic (DHCP)
Click the enable tick box on and off and on again
wait for a connection, use Firefox or whatever as there is no other indication that it's working.

I 'think' my problem was having the wired connection at the same time I was trying to connect via wireless. Anyway it seems to work at the moment.

Cheers, Mike

---

### Post by kplaxmaster on 2007-12-14
How did you get WG111v3 to work under ndiswrapper? I am running Ubuntu 7.10 x64.  When I try and install the WG111v3 driver (both the 32 and 64 version), it installs correctly, ndiswrapper -l shows the driver is installed and the device is present.  However, dmesg gives me an error stating it couldn't load the driver correctly...

Any help??

---

### Post by mdurham on 2007-12-14
> **kplaxmaster said:**
> How did you get WG111v3 to work under ndiswrapper? I am running Ubuntu 7.10 x64.  When I try and install the WG111v3 driver (both the 32 and 64 version), it installs correctly, ndiswrapper -l shows the driver is installed and the device is present.  However, dmesg gives me an error stating it couldn't load the driver correctly...

Any help??

I installed ndiswrapper-common and ndiswrapper-utils and ndisgtk.
On my 32 bit system I put WG111v3.sys and WG111v3.inf in a directory and used "sudo ndisgtk".
I 'think' that's all I did. Then I setup the network using the manual network config as I wrote above.

---

### Post by kplaxmaster on 2007-12-15
it seems that since i am running ubuntu 7.10 x64, i need a 64-bit driver, not a 32-bit driver.  However, ndiswrapper doesn't support Vista drivers.  Where/How can i get an XP x64 driver for wg111v3?

any tricks on doing this? I am reading the driver info now which states it supports x64 versions which isn't the vista driver but the regular driver.  however, ndiswrapper still complains about it not being 64-bit driver.  is there a way to edit the driver to get rid of the other calls to make this driver a driver ONLY for XP x64 (since Vista again is its own driver in another folder/file)??

Thanks guys!

---

### Post by IanB2 on 2008-05-29
I returned the usb dongle and bought one from linuxemporium which is now supported 'out of the box' in Hardy ...... fantastic!

---

