---
title: "Can't get list of wireless networks to display"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by dora5 on 2015-04-08
I just installed Ubuntu 14.04 with gnome interface on a Dell Inspiron B130 laptop, which was running Windows XP service pack 3, and the wireless worked as recently as yesterday.    

It says that the wireless is enabled - there is a check mark by "enable wi-fi".    

The wireless controller is Broadcom Corporation BCM4318 802.11a/b/g PCI Express Transceiver Dell Wireless 1470 Dua Band WLAN Mini-PCI.   The driver in use is b43-pci-bridge.   

Online it says to download a Broadcom driver, and that b43 is the correct driver for BCM4318.    So it's got the correct driver automatically installed.   

I tried Fn + F2, which Bios says is my system's shortcut to start the wireless or whatever.

I did the command to kill the whatever that sometimes hangs and restart it.   (Whatever whatever was got away.)

What do I do to get the list of wireless networks to show up? 

I need to be able to use my laptop on the bus; there you don't enter the identity of the wireless, you just connect to the open bus wifi.   

Thanks!

---

### Post by cariboo on 2015-04-08
Removed two posts that had nothing to do with the thread.

---

### Post by Vladlenin5000 on 2015-04-09
For Broadcom chipsets please follow instructions here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by dora5 on 2015-04-11
LOL, thanks for that link, Vladlenin.   I had found it - trouble is, while it IS part of the solution, and it's good information as far as it goes, it contains only part of the information, and the instructions on what to uninstall first only apply sometimes.

Here is the solution.  After days of working on it, I am now connected.   It took several steps, and not only one, to solve the problem.  

The trouble I ran into was 50 million posts online, including on this forum, saying vaguely that one needs multiple drivers to make Broadcom wireless mini-PCI cards work, coupled with 50 million MORE posts saying that people tried this strategy or that strategy with assorted drivers and it happened to work for them or didn't work at all for them, with no rhyme or reason why.  I also found many bits and pieces of how to get Broadcom wireless working that were true as far as they went, but didn't get my card working because all six things that could go wrong did.  Nearly missing is a complete, systematic discussion of how to get a Broadcom wireless card working, complete with which drivers to use when and how to use them.  
 
Now, I had given up and bought a dongle thingy, before I finally found the solution.   Dongle thingy didn&#8217;t even solve all of the issues!
 
Any time it takes me three days of hard work to find an answer it should have taken someone fifteen minutes to explain to me, I post the answer for the benefit of all the other subhumans out there who weren&#8217;t born knowing everything.   There are also other subhumans who just want to use our computers to do our work!   Of course worthwhile people spend their lives solving IT problems, and were born knowing everything.   What is more, nothing really upsets the sort of people who gave me a hard time about this like making information easy to find.  Wasting three days of my life that I needed to spend doing productive work was not how to keep the information esoteric.  If you&#8217;d simply deigned to tell me how to fix the problem, the information would have been buried in your big old forum like everything else that gets published here that you require us to have read every word on it that was ever written before asking a simple question.    Which just convinced me I&#8217;d probably better publish it elsewhere as well, because noone ever needs to go through this again with this question.    If you want respect, give it, if you can imagine how. 
 
One problem is that these Broadcom cards are both outdated and cheap &#8211; as in standard Dell and Lenovo cheap.   They weren&#8217;t worth that much in their own time.   I looked into simply getting a more user friendly brand, and discovered that, for instance, they only ever came out in G wireless.   I mean&#8230; you know.   However I learned that a newer usb wireless device won&#8217;t necessarily work better since it can&#8217;t take advantage of the machine&#8217;s wireless antenna.  
 
I&#8217;ve got a slightly old Dell laptop of my brother&#8217;s and got tired of Windows XP service pack 3 and Dell bloatware slowing the thing down to where an up to date browser can&#8217;t take it&#8217;s 1 gig of RAM without slowing the machine that is maxed out at 2 gigs of RAM to a halt!  Ubuntu both runs much better and takes one and a half times as long to drain the battery.  
 
**1.  Identifying the correct drivers**
 
Ubuntu DOES need multiple things done with Broadcom wireless drivers in order for the driver that came with the kernel, if there was one, to work properly.   Usually one or two other things have to be installed.  These other things are variously called firmware and installers, and all one needs to know is that the wireless won&#8217;t work without them.   In the words of one web site, &#8220;The b43/b43legacy drivers require proprietary firmware to be loaded onto the wireless chip before it can operate. &#8220;  Since the basic b43 driver that came with the Linux kernel is surely proprietary too, that doesn&#8217;t make any sense, but I&#8217;m not the first person to notice that.  
 
There are specifically one or two of them that have to be installed for any given card, and which ones those are depends on the specific card.  
 
Anything else that was installed needs to be removed.   Often people have installed wrong things, installed everything Broadcom in Synaptic, or installed multiple things because the confusing discussions on these forums gave them the idea they should.  If it&#8217;s not on the table, it should be removed.  
 
There are actual living discussions online that advise people that they have to compile or build the driver; that is NOT TRUE!  
 
The single best discussion I found of what drivers to install was this discussion.   The post Vladlenin pointed me to got his table from it.  
 
_[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)_ 
 
This table is the product of long collecting of information on what actually causes Broadcom wireless devices to run, because cheap computer manufacturers have a long consistent history of pawning them off on people who buy computers, even though it has long been known they aren&#8217;t the best devices.  
 
This actually isn&#8217;t identical to the table in the thread referenced above; it has more information.
 
[h=2]BROADCOM WIRELESS TABLE (Updated 21 February 2015)[/h]PCI.ID              12.04 LTS                       14.04+------------------------------------------------------------------------------------14e4:0576           Special Case #1                 Special Case #1         14e4:4301           firmware-b43legacy-installer    firmware-b43-installer  14e4:4306           firmware-b43legacy-installer    firmware-b43-installer  14e4:4306 rev 02    firmware-b43legacy-installer    firmware-b43-installer  14e4:4306 rev 03    linux-firmware-nonfree          firmware-b43-installer      14e4:4307           linux-firmware-nonfree          firmware-b43-installer          14e4:4311           linux-firmware-nonfree          firmware-b43-installer      14e4:4312           linux-firmware-nonfree          firmware-b43-installer      14e4:4313           linux-firmware-nonfree          firmware-b43-installer         14e4:4315           firmware-b43-lpphy-installer    firmware-b43-installer      14e4:4315 rev 01    firmware-b43-installer          firmware-b43-installer / Case #4      14e4:4318           linux-firmware-nonfree          firmware-b43-installer          14e4:4318 rev 02    firmware-b43-installer          firmware-b43-installer          14e4:4319           linux-firmware-nonfree          firmware-b43-installer         14e4:4320 rev 02    firmware-b43legacy-installer    firmware-b43-installer         14e4:4320 rev 03    linux-firmware-nonfree          firmware-b43-installer      14e4:4324           linux-firmware-nonfree          firmware-b43-installer  14e4:4325           firmware-b43legacy-installer    firmware-b43-installer14e4:4328           bcmwl-kernel-source             firmware-b43-installer   14e4:4329           bcmwl-kernel-source             bcmwl-kernel-source     14e4:432a           bcmwl-kernel-source             bcmwl-kernel-source     14e4:432b           bcmwl-kernel-source             bcmwl-kernel-source     14e4:432c           bcmwl-kernel-source             bcmwl-kernel-source     14e4:432d           bcmwl-kernel-source             bcmwl-kernel-source    14e4:4331           linux-firmware-nonfree          firmware-b43-installer    14e4:4335           UNKNOWN                         firmware-b43-installer14e4:4353           Special Case #1                 Special Case #1         14e4:4357           Special Case #1                 Special Case #1         14e4:4358           bcmwl-kernel-source             bcmwl-kernel-source     14e4:4359           bcmwl-kernel-source             bcmwl-kernel-source     14e4:4365           Special Case #2                 bcmwl-kernel-source 14e4:4365 rev 01    Special Case #2                 bcmwl-kernel-source 14e4:43a0           UNKNOWN                         bcmwl-kernel-source        14e4:4727           Special Case #3                 Special Case #1     14e4:a962           UNKNOWN                         firmware-b43-installer 
 
**Special Case #1** - Uses bcma and brcmsmac driver combination. Required firmware is installed by default in the package linux-firmware .
**Special Case #2** - [Probably only working in 64-bit only]("http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560") for versions older than 14.04. Some cases need to install the linux-firmware-nonfree and bcmwl-kernel-source packages, then proceed to reboot.
**Special Case #3** - Use brcmwl-kernel-source for kernel versions less than 3.8. To check for Kernel version open the terminal and type: uname -r. For kernel versions 3.8 and later, use brcmsmac.
**Special Case #4** - In hardware like the Lenovo S10-2, if your wireless card gets stuck trying to connect to an SSID (keeps trying to connect), then the alternative to get it working would be to install the brcmwl-kernel-source package (Remove any other installed packages related to it). Read the Debugging section below for more information regarding this wireless device.
**IMPORTANT NOTE** - After September 2014, if you follow this answer and still you have problems installing the correct driver, please try the firmware-b43-installer package. There were some changes and some drivers will only work with this package. Remember to have a clean system before installing it:
 
 
Here is a systematic explanation someone added:
[TABLE="width: 589"]
[TR]
[TD] 
[/TD]
[TD]As I've found out, to systemize this a little, there are four driver families available:

[LIST=1]
[*]open-source b43 from the the [b43m project][1] that is available in [Linux kernel],
[*]open-source brcmsmac/brcmfmac, also availalble in [kernel]
[*]Windows libs via [ndiswrapper], and
[*][Broadcom][5]'s own linux [libs (STA)]
[/LIST]
[/TD]
[/TR]
[/TABLE]
 
I am pretty sure that there are atleast two relatively recent Broadcom wireless cards that take brcmsmac/ brcmfmac (2 names for the same file).  I don&#8217;t think they are listed above.  
 
**You need information from your system to use the table.   **
 
Run
*sudo lspci &#8211;nn &#8211;d 14e4:*
 
will get you something like
 
Ethernet controller BCM4401-B0 100 Base-TX [14e4:170](rev 02)
Network Controller:  BCM4318 [AirForce 54g] 082.11a/b/g PCI Express Transceiver 14e4:4319] (rev 02)
 
For this table you need to know the pci.id, which in this case is 14e4:4319.
 
I&#8217;ve seen other tables that go by the number represented by BCM4318.
 
It is also good to know what driver your system is trying to use.   In my case that was b43-pci-bridge, and that is what driver it ended up using; it just needed its helper drivers.
 
*sudo* *lshw* will get you information about the devices running on your system.  It should give you the driver associated with the device under configuration.  If instead you see UNCLAIMED, that&#8217;s a problem.  It could mean the driver isn&#8217;t active or isn&#8217;t installed, especially if there isn&#8217;t a driver listed, or it could be because for instance Ethernet isn&#8217;t plugged in; more often the former.  Usually something simpler than driver not there is keeping the driver from working.  I currently see UNCLAIMED for Ethernet, and the rest of the information gives you a clue what four lines of code in terminal will fix it., to be explained below;
 
*network: 0 UNCLAIMED  (this is wrong)*
*description: Ethernet controller*
*product:  **BCM4401-B0 100Base-TX** (there&#8217;s your clue)*
*vendor: **Broadcom Corporation***
*physical id: 0*
*&#8230;*
*configuration:  latency=64 (something missing here)*
*resources: memory:dfbfc000-dfbfdfff*
 
*Network:1*
*description: Network controller*
*product:  **BCM4318 [AirForce 54g] 802.11a/b/g PCI  Express Trasceiver***
*vendor: **Broadcom Corporation***
*&#8230;..*
*configuration: **driver=b43-pci-bridge** latency=64*
 
You should also know what linux kernel you are running, as in some cases that makes a difference what drivers you will use.
 
*uname &#8211;r*    will give you your kernel version.    
 
You need to know both that the controller is BCM4318, and that the PCI.ID is 14e4:4319 (or whatever yours is).  I found real disagreement on which is the more specific information, but different tables break it down differently.   
 
Now, the table above often says to install ONLY the firmware-b43-installer, and part of the discussion says that while online discussions often say to install b43-fwcutter as an end in itself, it is outdated and doesn&#8217;t work.   Actually it is a dependency for firmware-b43-installer to work.   Synaptic won&#8217;t let you not install it with firmware-b43-installer.  
 
Sometimes updates in various things have caused the firmware-b43-installer to be what is going to work no matter what is in the table.   Also, the two newest sets of Broadcom wireless cards, which need drivers that aren&#8217;t on this table, aren&#8217;t in this table.   What is more the drivers aren&#8217;t in Synaptic nor the Software Center, or I didn&#8217;t find them.  
 
Another contributor to this discussion gave his systematic version of what not to use and what to use.   He said that b43-fwcutter by itself won&#8217;t work for 4313 and newer; unclear what that cutoff actually is.   the STA driver is unstable junk, and ndiswrapper is worse.   He advised people should use brcm80211 aka brmscmac, which I understand one should specifically use for certain less ancient Broadcom wireless cards.   I didn&#8217;t try it, since using the combo the table advised me to worked.  
 
Where to find the drivers/ installers isn&#8217;t the mystery that has come across; most are available in the Synaptic Package Manager, and some are available in the Ubuntu Software Center.   Much advice online says to uninstall them and install them manually using sudo apt-get install; I installed them from Synaptic and it worked fine.   It isn&#8217;t clear why it would make a difference how it was installed &#8211; except that the Synaptic package manager takes care of dependencies.   If you for instance successfully install firmware-b43-installer without its dependency b43-fwcutter you&#8217;ll be in trouble, and almost noone points out that  you have to install both, and I&#8217;ve seen someone who otherwise wrote one of the better discussions explicitly say not to. 
 
There are several discussions that instruct people with no internet access to get the driver off of their Ubuntu install dvds.   I tried to go that route, and found only, I think it was a debian package to install b43-fwcutter, on the dvd, and that was all that was there.   I didn&#8217;t locate the individual driver on the dvd.   B43-fwcutter is itself an installer.  
 
There is also a good discussion here, containing complex instructions on how to get the whole thing working for the Debian OS.   Ubuntu is a Debian- based system.  
 
_[https://wiki.debian.org/bcm43xx#b43_and_b43legacy](https://wiki.debian.org/bcm43xx#b43_and_b43legacy)  _
 
There are multiple pages and levels of this discussion; it addresses multiple aspects of how to actually get a machine that runs one of these cards to run wireless.
 
Many discussions advise people to uninstall any drivers they have already installed and intend to keep, and reinstall them, often manually by using apt-get install, which of course works since the files are available in both Synaptic and the Software Center.   I installed them from Synaptic and they worked.   I&#8217;m not sure by what magic it would make a difference, but one can always try it.
 
If you DO remove a driver/ helper driver and it isn&#8217;t found, that isn&#8217;t necessarily because you already successfully removed it.   Run
 
*dmesg | grep b43*
 
If there are errors like bre-phy0 ERROR, probably this is a specific indication that the correct firmware for the Broadcom card is not installed.
 
**Before you run this stuff, you often also have to run other things**.  For one thing, the dependencies your system may nor may not have all built up to date &#8211; and I think I&#8217;m glad I hadn&#8217;t even tried to use VLC to play dvds yet from what happened when I ran it.  If you just found out the wireless doesn&#8217;t work chances are you pretty recently installed Ubuntu on the computer&#8230;
 
*apt-get install build-essential linux-headers-generic*
*apt-get build-dep linux*
if everything already installed, run* sudo apt-get build-dep-linux* 
 
One person found that this alone solved his issue as what he&#8217;d already installed evidently didn&#8217;t have the dependencies to function correctly.   
 
**If that doesn&#8217;t get wireless one has to do more troubleshooting**.
 
Of course make sure wireless is enabled.  
 
If  everything is basically grayed out on your wireless connection icon, on a laptop, **make sure the wireless is turned on**, even if was turned on an hour ago and you didn&#8217;t turn it off.
 
Mine had somehow turned itself off.    Most laptops have a physical switch to turn it back on.   Cheapy Dell laptop does not.   It would cost five cents.   Often a keystroke combination, most often fn + F2 on a Dell will turn it back on; it didn&#8217;t work on mine though from the BIOS settings it should have.    When I checked BIOS I found wireless was not configured to start itself at startup, and I evidently couldn&#8217;t manually turn it on.   I fixed the BIOS setting and the wireless menu changed in appearance but didn&#8217;t&#8217; begin working.
 
Of course, since I&#8217;d had the wireless mini-PCI card in and out several times I took it out and put it back in case of loose connection. 
 
**Check whether the driver is blocked from functioning.**
 
Run *sudo rfkill list*.
 
If you see a hard or a soft block, that is keeping the driver from functioning.   Usually that is because your other network device&#8217;s driver has blocked it, in a configuration file.  
 
If soft blocked = no and hard blocked = no, this isn&#8217;t the problem.
 
I saw long discussion after long discussion of how to edit the configuration file.   File tells you it can&#8217;t be edited, but evidently it can.    To do that, you can add lines or put # at the beginning of lines to disable them (comment them out).   But that atleast often isn&#8217;t necessary.  
 
I just *typed sudo rfkill unblock all*.    That will often remove the block.  
 
A hard block, however, may mean that the wireless switch is turned off.    At one point this worked for me.
 
 
 
**Restart the network controller**
 
(I&#8217;ve not had this work even once, but often it does.)
 
*sudo service network-manager restart*
 
 
**Turn on the wireless driver..  then turn on the Ethernet driver&#8230; then&#8230;..**
 
It&#8217;s magic.
 
Don&#8217;t everybody snort at once&#8230;  
 
It isn&#8217;t even that Linux works very differently from Windows.    Usually if your computer runs one Broadcom networking adapter, it runs two of them.   I don&#8217;t know if that&#8217;s because Broadcom pairs them at a discount to cheapy computer manufacturers, or what&#8230;   Did you notice above that both my Ethernet card and my wireless card are manufactured by Broadcom?   Well, Broadcom networking devices do this neat trick; they don&#8217;t want to both be enabled at once like the way the rest of the world works, so they turn each other off, and then they don&#8217;t turn back on.
 
It is so ridiculous, that with many computers, if you used the wireless, and then shut down the computer, when you boot it back up you find out you don&#8217;t even have ANY networking devices.  
 
Some people complain online that they have this interesting ritual of rebooting their computer three times every time they boot it up to get it to work.
 
There&#8217;s an easier way.
 
In the words of one web site, &#8220;f you have few drivers installed, system may auto-load different driver than the one you wanted to use. Manual (un)loading drivers can be done with *modprobe* tool.&#8221;
 
To use wired if you last used wireless, *even if it was a different brand&#8217;s wireless usb dongle*:
 
*sudo modprobe &#8211;r b43*
*sudo modprobe b44*   (assuming b44 is the name of your Ethernet driver, which it is in my case.)
 
To use wireless if you last used wired:
 
*sudo modprobe &#8211;r &#8211;b44*
*sudo modprobe b43*
 
To use wireless if you last used wireless:
*sudo modprobe b43*
 
To use wired if you last used wired*, just boot up the machine* &#8211; the drivers can actually figure that one out.
 
This works like magic.   Well, I guess when it works.  I have to do it, each and every time I boot up my machine, and I want to run wireless and/or didn&#8217;t last run Ethernet.  
 
Here&#8217;s his instructions, which are more general than mine:
 
To unload all known drivers (you can pick only one command, if you know which driver is in use) perform:
[Toggle line numbers]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/") 
[   1]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-cd292c2ceee979f3b581266868c524a1b2c2cb87_1") modprobe -r b43 bcma[   2]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-cd292c2ceee979f3b581266868c524a1b2c2cb87_2") modprobe -r brcmsmac bcma[   3]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-cd292c2ceee979f3b581266868c524a1b2c2cb87_3") modprobe -r wlTo load specific driver use **one** of the following commands:
[Toggle line numbers]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/") 
[   1]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-3bb6ed214cba8635e7669d5345679a011e9990d4_1") modprobe b43[   2]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-3bb6ed214cba8635e7669d5345679a011e9990d4_2") modprobe brcmsmac[   3]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-3bb6ed214cba8635e7669d5345679a011e9990d4_3") modprobe wlIt is possible to prevent system from auto-loading some drivers by blacklisting them. This can be done with the following command:
[Toggle line numbers]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/") 
[   1]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#CA-20c883e96f8ae1db16cf316e0f1db4b093cc43e1_1") echo "blacklist drivername" >> /etc/modprobe.d/blacklistIf you plan to use *wl*, you should blacklist *b43* and *brcmsmac* as well as *bcma*. Unfortunately *wl* does not use *bcma* bus driver, so this additional step is required.
(from [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/)  )   Note:  I subscribed to his mailing list with my original question, and they must be SOOOOO slow I never got a single response.)
 
To be sure, when I worked on a help desk helping students connect devices to the Internet last fall, and they had a full variety of operating systems and devices, it did often pay to disable the other network adapter.     Laptop didn&#8217;t care when it ran Windows XP.   Both adapters were always enabled.    And it seems online like 90% of the time this problem involves Broadcom devices.
 
 
**That may not fix everything.   **
 
For instance, I found this, concerning my own card; 
 
BCM4318 chipset: AP mode does not work because of packet loss in high transmission rates. Hard to debug & fix. 
 
Meaning what -  the thing is worthless at high speed?  I believe it works at an old speed standard to begin with .   Now, mind you, I want to be able to use the thing on breaks at work, on the bus, and when hospitalized&#8230;  and then it would be  real useful  if the thing can connect with the wireless router down the hall.     which it sometimes did.    Sitting three feet from the router it picks up three bars out of four &#8211; both with the internal card and with the brand new usb dongle thing.  
 
Sometimes you have to specifically disable IPv6, on the laptop and/or on the router.
 
Especially with an older adapter like this, make sure the card can connect to the router, or vice versa.
From [http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588](http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588)  
&#8220;If your wireless card see/not see the router and gets stuck in an endless "Trying to connect (Try 1/3)" loop the solution might be proper configuration of your router or wireless SSID device.
&#8220;For all Wireless cards in general, it is very important to also take into consideration the network devices you are using (Routers, Switches, Wireless Channels and Wireless Bands, etc..). With this information you will be able to evaluate better what the source of the problem could be when you arrive at a dead end. An example would be the Lenovo S10-2 which uses the **14e4:4315 rev 01** PCIID. Even after installing the correct driver the user would end up in a "trying to connect" loop. It would see the wireless SSID but when trying to connect to it, it would enter an reconnecting loop.
&#8220;The solution was that this particular wireless device did not support 40 Mhz channels nor does it support 802.11N. The router in that case was actually broadcasting with a forced 40 Mhz and on WiFi-N only. When the router was set to Auto mode and 20/40 Mhz Channel, the wireless card worked correctly. This is a case scenario that also repeats in other cases, so a proper evaluation of the network equipment would help a lot.&#8221;
One suggestion suggests **that Network Manager is buggy** and hard to use by nature and suggests installing an alternative called WICD or wicd-gtk instead.  I also saw NM..  
 
*sudo apt-get install wicd-gtk*
 
I might give it a try.   I definitely noticed the harder than it ought to be to use part.  
Below is a link to a discussion of how to connect your wireless devices through the terminal, manually. 
 
[http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588](http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588)    
  
That can definitely help when the network is there but your wireless device ain&#8217;t having an easy time seeing it, which happened to me last night.   I knew the name of my wireless router, and suddenly, voila, you wouldn&#8217;t believe what the thing could see&#8230;
 
Also, when I tried it, I found out &#8220;the interface doesn&#8217;t support scanning&#8221;.    Useless.  
 
If you are getting **b43-phy0 ERROR: Fatal DMA error / b43-phy0 warning: Forced PIO** do the following:
*sudo rmmod b43     **sudo modprobe b43 pio=0 qos=0  *If it works then add it to you RC files so it is executed every time you boot.  (I&#8217;ve no idea what it&#8217;s talking about)  You can change PIO to 1 if you need to.
 
 
This page has some advanced information that could apply to your machine.  [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/)     It isn&#8217;t at all clear to me what one is supposed to do with knowing what your PHY version is.   
 
In general, the information on this page is well over the heads of anyone who would need to know any of this information.  
 
Running *dmesg | grep b43* yielded different sorts of information:
 
b43-phy0: Broadcom 4318 WLAN found (core revision 9)
&#8220;             :  Found PHY: Analog 3, Type 2 (G), Revision 7
               : warning:  5 GHz band is unsupported on this PHY
               : Loading firmware version 666.2 (2011-02-23 01:15:07)
 
It sounds like it could be a good thing my router runs more than one band.  
 
*uname* &#8211;a provides my kernel version and my OS version.
 
*lspci &#8211;vnn | grep 43 &#8211;A7* yields the identity of my card, the 14e4:4319 number and revision, the subsystem, and the name of the kernel driver in use; it&#8217;s a fast path to this information.  
 
*lspci* yields names of devices but not their drivers.   
 
*lspci &#8211;vnn* yields a short version of names of devices, their resources and their drivers.

---

