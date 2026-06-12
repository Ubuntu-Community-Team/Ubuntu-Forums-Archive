---
title: "Wireless network problem with Linksys wmp54gs card"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Lystrodom on 2006-10-13
So I've just today installed linux on my machine, on a second hard drive. I get my internet through a LAN, using the Linksys Wireless G PCI card with Speedbooster thing. Using ndiswrapper, I got the driver. The machine recognizes the card, but not any networks. Under networking, I can see the device, listed as eth1, try to change the connection, and try to activate it. It will say that it is activated, but when I click ok, it takes a long time, the internet doesn't work, and if I go back into networking, the device is deactivated.

My connection is WEP key protected, and I my IP address is done by DHCP

iwconfig allows me to change the settings, but ifconfig doesn't register the device.

I tried to give as much information as I knew how to give. Any suggestions?

---

### Post by Lystrodom on 2006-10-13
Oh, I forgot to mention I'm dual booting Win XP and the card works fine on that.

---

### Post by CanadianMan on 2006-10-22
I have this exact same problem.  I figured the wireless device shouldn't be eth1 but something like wlan0 or w/e which is what i've been looking for a solution for but haven't found anything.  Were you able to find anything or does anyone else know what is going on?  Thanks.

---

### Post by tech2k5 on 2006-10-23
Have you guys checked this out?
Linksys WMP54GS with Broadcom BCM4306 chipset under Linux 2.6 kernel by Dossy's Blog

 [http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html)

---

### Post by CanadianMan on 2006-10-24
tech2k5,

Yes i have tried [http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html) i downloaded those drivers from WMP54GS_20040423.exe and installed them using ndiswrapper (my version is 1.8 if that helps) but there was a WMP54GS.inf not a bcmwl5.inf.  I do get this message afterwards:

Installed ndis drivers:
wmp54gs driver present, hardware present

but no amount of restarting and modprobe ndiswrapper will bring the green light on.  Just yesterday i downloaded ndiswrapper 1.27 to try that out but i get some error when i do make:

Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make

I have used the KBUILD to direct it to the right path but that doesn't seem to work either.  I have been looking at this page for help as well [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and was wondering if I should use ndiswrapper 0.11 or 0.12 but i didn't see anything about ubuntu on there either. Thanks for the help.

---

### Post by tech2k5 on 2006-10-25
that shucks. I also have a Linksys WMP54GS (bought it bcoz it works with osx86 ;-) and having problems getting it to run under LAMP. I read the Dossy article but havn't actually tried it yet, so TY for the feedback. Also, for other readers information the DL link for ndiswrapper .deb file in Dossy's article is broken. Try this instead:

[http://distro.ibiblio.org/pub/linux/distributions/gibraltar/archive/binary/](http://distro.ibiblio.org/pub/linux/distributions/gibraltar/archive/binary/)

---

### Post by bionnaki on 2006-10-25
See the link in my signature.

---

### Post by tech2k5 on 2006-10-25
thanks for the link but we're discussing Linksys WMP54GS (please mind the S at the end) here. I dont think they're the same.

---

### Post by bionnaki on 2006-10-25
what driver does it use?

---

### Post by tech2k5 on 2006-10-25
Ubuntu Drapper detects it as Broad Comm (the numbers that follows varies from card model to model and even between same cards of different FW versions). Mine is indicated as follows when I did 'lspci':

0000:60:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN adapter (rev 02).

None of us who have posted in this thread have been successful in getting this card to work under drapper. *Again, I want to emphasize on the difference between WMP54G and WMP54G*S*

 Another issue I am facing is ndiswrapper does not work correctly under drapper. When I attempted to install the package I got error message saying dipendencies are missing.

---

### Post by tech2k5 on 2006-10-25
> **bionnaki said:**
> See the link in my signature.

Can you please delete this post because WMP54G is NOT same as WMPG54S

---

### Post by CanadianMan on 2006-10-25
tech2k5 and Lystrodom,

I've got my wireless working FINALLY.  Thanks to nickm and crag277.  I
followed crag277's post:

[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)

and thats all I needed, use the files he provides as well.  I see tech2k5
you said your card was:

0000:60:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN adapter (rev 02).

which is EXACTLY what I have (same chipset as well).  I was able to get ndiswrapper working with this my version 1.8, have you tried installing from Synaptic or are you downloading it and trying to install from there.

Lystrodom run this command like tech2k5 and nickm said in their post:

lspci | grep Broadcom\ Corporation

and see if you get something like BCM4318 hopefully you do cuz I'm willing to bet that you'll have wireless very soon.  Hope this helps you man.  Now I just want Ad-hoc mode and WPA. I'm looking at you bionnaki ;) got anything on the GS?  I'm guessing we are using ome3 drivers or w/e that means.  Thanks.

-CanadianMan

---

### Post by tech2k5 on 2006-10-26
Finally I got mine working as well :-) Refer to the instructions at: [http://ubuntuforums.org/showthread.php?t=190177&page=1](http://ubuntuforums.org/showthread.php?t=190177&page=1) 
but there are minor differences. For instance I used the WMP54G.inf and bcmwl5.sys files from my linksys driver CD instead of the files suggested in the post. ok,it's 4am here and I need some rest. will post the rest tomorrow :-D But I know I'll get a good night sleep bcoz I beat it! :-D

---

### Post by tech2k5 on 2006-10-26
ok, here's my complete report on what I did to get [Linksys WMP54GS]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&packedargs=site%3DUS&pagename=Linksys%2FCommon%2FVisitorWrapper") card working under [Ubuntu 6.06 LTS Server]("http://www.ubuntu.com/server").
Before anything else, run lspci in your console and make sure your card is identified as 
**Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN adapter (rev 02).** There are various models of WMP54 cards out there. Some are WMP54G and I think there are even different versions of WMP54GS. This is something that I wish some of the forum contributor/guide authors would do: to specify exactly which model and even the firmware version of the device they are writing about because  some devices wont work if the firmware version is different.

First of all these are my system specs:

Systemboard: [Intel D915GAGLK]("http://developer.intel.com/products/motherboard/d915gag/index.htm") 
Processor: [Intel Celeron D 326]("http://www.intel.com/products/processor_number/eng/chart/celeron_d.htm") 2.53 Ghz
Memory: 512 MB [(2 x Samsung DDR 256MB 266MHz (PC 2100)]("http://www.directron.com/ddr256266.html")
Wifi Card: [Linksys WMP54GS]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&packedargs=site%3DUS&pagename=Linksys%2FCommon%2FVisitorWrapper")

The reason I chose this card is primarily because it's comptible with the OSX86 Project. Now I have this card working with WinXP, Vista RC2, osx86, and Ubuntu 6.06 LTS :-)

I used the boot CD created using the 6.06 LTS Drapper Drake iso image download from [their website]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease"). 
Problem Encountered: During the initial install process both Linksys card and my onboard LAN adapter were detected and identified correctly but I cant obtain DHCP using wifi nor can get it to work with static IP address. So I just selected my onboard LAN card to get internet connection. 

After the installation and first time logon needless to say my wifi card wasn't found. But luckily I had the LAN connection to the internet to do what I needed to do. So I searched around on google and came across this excellent article:
[http://ubuntuforums.org/showthread.php?t=190177&page=1](http://ubuntuforums.org/showthread.php?t=190177&page=1)

But the problem is my Drapper install CD didn't have gedit, ubuntu-desktop and other packages needed to configure the settings in the instruction. That's why my LAN connection was useful for this. So to get gedit I did "sudo apt-get install gedit" . But later I figured I could have done it in console using pico or nano instead. Next I had to install ubuntu-desktop from the net by running "sudo apt-get install ubuntu-desktop" 

Ok now I have gedit and Ubuntu-desktop and ready to do the configuration. There rest is pretty much following "piracyrocks" [excellent guide on setting up WMP54GS]("http://ubuntuforums.org/showthread.php?t=190177"). 
Exceptions:
In step 3 he recommended using windows driver files from a download link, but instead I used WMP54GS.inf and bcmwl5.sys files found under the DRIVERS folder of my Linksys CD. I had no problem installing the drivers and everything went through like he said. Except when I ran "echo ndiswrapper >> /etc/modules" i got "permission denied", eventhough I added sudo to it in the second attempt. But it really didn't matter so skip this step if it doesn't work for you as well.

Next I had to do sudo gedit /etc/network/interfaces to add my linksys card in there. In the interfaces file I just added under my ethernet settings:

iface wlan0 inet dhcp
auto wlan0

and then I did sudo /etc/modprobe.d/ndiswrapper and replaced eth0 with wlan0. sudo reboot after that.
Note: try not to mess with the settings in System | Administration | Netowrking because it will overwrite your linksys card as eth0 in /etc/network/interfaces file. When that happens the gnote network-manager utility will work because it's not seeing any wlan cards. 

During the bootprocess I was happy to see the greenlight on my Linksys card lit up when network interface modules are being loaded :-) After the logon I did right click on the network-manager icon on top right of the taskbar and selected my access point. My Dlink DI524 uses 64/128bit Hex WEP key so I entered it and chose Open key access. After that everythings working fine and I no longer needed my ethernet LAN connection :-)

Good luck and I can only say these instructions are likely to work if you see "Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN adapter (rev 02)" when u do lspci.

---

### Post by Lystrodom on 2006-10-26
I'd forgotten about this thread. The day after I posted, I think, I found that Ubuntu was trying to use that bcm43xx driver for it, and found out how to blacklist it on my own.

Sorry I didn't come back sooner. Now I've just got to figure out how do use WPA...

---

