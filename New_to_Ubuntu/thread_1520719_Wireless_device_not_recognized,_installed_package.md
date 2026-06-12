---
title: "Wireless device not recognized, installed package"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Rhodophyta on 2010-06-29
EDIT: Please see my last post further down the thread--I think I am almost there, I just need to figure out this last part.

Hello, I am new to Linux, but I try my very best to learn things by trial and error, and extensive reading. However, I am unable to resolve a problem with my wireless card (Atheros AR5001). After a clean install, no wireless networks could be detected. First, I went to the Harware Manager, but only two drivers are listed for my graphics driver.
Next,I replaced network manager with wicd. Then I installed the following package: ```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```, thinking it would include drivers for my device. Apparently Ubuntu **does** recognize my driver, but it thinks that it is disabled. I only have one wireless switch on my notebook, and it is blue (definitely turned on!):
```
tara@tara-laptop:~$ sudo lshw -c network
[sudo] password for tara: 
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:4f:f1:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:5e:b4:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
```
I am in my house about 3 feet away from the wireless router, and my husband is connected to our network, but my computer simply isn't detecting any networks.
This thread looked quite promising :[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
But I got stuck at step #2: "From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines." Because I couldn't see the other 52 lines to delete all the #s (absolute beginner :P) and I didn't want to really screw things up!
Mahalo for your help. I am really excited to switch over to Linux--this is my only hiccup and I've spent a full day trying to resolve it. The first time I really screwed something up and had to reinstall, so I'm nervous trying to play around too much.

---

### Post by matt-fender on 2010-06-29
I have the 5001 in my netbook too!, mine worked straight out of the box, what encryption type if your wireless network?

Is the WIFI adaptor seen in [HTML]lspci[/HTML]When you right click the network icon on the top panel, is the wireless enabled?

also try this:  ```
sudo ifconfig wlan0 up
```

---

### Post by Bucky Ball on 2010-06-29
You need to be using MadWifi for Atheros. ;)

If you haven't already, plug in an ethernet cable and get your updates. That might just fix everything. Do not under ANY circumstances start a lengthy battle with Ndiswrapper unless last resort and only viable option. Atheros is friendly and shouldn't be too much of a problem.

Also, make sure you are matching the details of your router (ESSID, security, DNS addresses) in whatever network software you are using. As I say, MadWifi = Atheros, but you definitely need the firmware which should be installed when you update. 

Relax, take note, and take care. Rule of thumb: Backup any file before you change it then you can just reinstall the working one if you screw up. You'll learn to love it!

---

### Post by Rhodophyta on 2010-06-30
When I tried sudo ifconfig wlan0 up I got Unknown error 132. Also, I definitely updated everything as soon as I installed.

I went to try to install madwifi, and the link that says Madwifi.net/Downloads Howto.Install.Madwifi gives me a 403 error. But it sounds like just what I need. The link I posted in my first post does have some instructions for madwifi, but the directions were just not dumbed down enough for me! When I got to ```
sudo nano /etc/apt/sources.list
``` I couldn't figure out how to delete all of the # before the dev, beacuse it wouldn't scroll down. I feel pretty silly asking for clarification on that.

My network uses WPA2-Personal and AES for encryption. I tried to look for a hidden network in wicd, but it's definitely not there. I'm pretty sure my wireless is enabled since the blue light is on, but I can't be 100% certain because wicd doesn't seem to have the same interface as network-manager, and I don't see an option to toggle it.

I guess now all I need is a little clarification on installing madwifi? I searched for it in the ubuntu software center, but it's not there.

---

### Post by Rhodophyta on 2010-06-30
I have installed madwifi using the instructions here: [http://swiss.ubuntuforums.org/showthread.php?p=9492116](http://swiss.ubuntuforums.org/showthread.php?p=9492116)

I have also installed linux-backports-modules-wireless-lucid-generic and linux-backports-modules-headers-lucid-generic from the synaptic package manager.

I finally found the Alternate Atheros "madwifi" driver in the hardware drivers, and enabled it. BUT still no wireless networks detected! Am I out of luck? Any ideas?

---

### Post by anewguy on 2010-06-30
See:

[http://madwifi.org/]("http://madwifi.org/")

Also, contrary to some opinions, ndiswrapper is still a very valuable tool.  Use the ndisgtk GUI'd front end to it and you save a lot of typing and it takes care of a lot of things automatically that you would otherwise have to do in the command line.  Not all wireless adapters have a Linux driver.  Some users cannot hard wire a connection to try to enable a  restricted driver.  But most adapters do have Windows drivers, and guess what ndiswrapper allows you to use?

I'm not advocating ndiswrapper over a Linux driver, but there are still many,many users out there who either can't afford a new adapter or see no reason to get one just to have a  native driver when they can use ndiswrapper and the Windows driver.  Please, don't give people a bad taste for ndiswrapper.  Myself and lots of other users have no choice but to use it, and it works very well.

---

### Post by Bucky Ball on 2010-06-30
> **Bucky Ball said:**
>  Do not under ANY circumstances start a lengthy battle with Ndiswrapper **unless last resort and only viable option.** 

Quite clearly I am not trying to put people off, just stating the obvious and I stand by it, and not to give people a nasty taste. If it is the only viable option (the right one for your card) go for it! If there is an alternative, use it, but as you say, for some cards there isn't. 

Many newer users have jumped the gun and wrestled for hours, days, weeks, attempting to get ndiswrapper working because they read about it somewhere. It can be a nightmare and can also put people off. Forum members can give advice to use ndiswrapper when it's not appropriate. 

For some, when they fail to get it working they then need to unravel it to get back to square one and install the appropriate driver. Enough to send a new user back to Windows. That is all. Goodnight. ;)

---

### Post by anewguy on 2010-06-30
Those users (and a lot are Broadcom card users) sometimes do jump the gun.  However, it's only a nightmare if (1) you don't use ndisgtk and (2) you don't follow instructions clearly.

The majority of the cases I have seen are due to the user trying something first then posting back that things don't work with ndiswrapper, when indeed they aren't starting with a clean network driver slate.

Like I said - people should use a native driver if it's available.

Hope you understand I'm not arguing with you - I've just had great luck with ndiswrapper and have walked many users through it simply and with no problems.  It should always be mentioned as a viable alternative (with ndisgtk) when no native driver is available.

Have a good one - I'll let you get back to helping the OP.

Dave ;)

---

### Post by Bucky Ball on 2010-06-30
> **anewguy said:**
> 
The majority of the cases I have seen are due to the user trying something first then posting back that things don't work with ndiswrapper, when indeed they aren't starting with a clean network driver slate.


+1. Good luck.

---

### Post by matt-fender on 2010-06-30
This may sound like a silly question but i'm pretty sure you're on a laptop right?

Are you 100% sure the wireless switch is ON?

I know with my Acer i can turn the wireless off which only disables the radio (ability to see wireless routers)

---

### Post by Rhodophyta on 2010-06-30
I **swear** the wireless switch was turned on yesterday when I posted, but after installing the packages and madwifi driver, the switch is orange and won't turn on! (The part about the blue light is in my first post). I went ahead and installed the windows driver with ndiswrapper. Here is the output of my lshw -C Network:

```
netathw : driver installed
	device (168C:001C) present (alternate driver: ath5k)
tara@tara-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:4f:f1:dd
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.4 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:5e:b4:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.55+,12/14/2009,7.7.0.456 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:23 memory:c2000000-c200ffff
tara@tara-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for tara
```:
I have the following blacklisted: 
```
#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci
blacklist ath_hal 
```

Before I installed ndiswrapper, I disabled the madwifi Atheros driver and restarted. It is (and was) completely deactivated. Still can't get the orange light to change to blue and still no networks found.

Should I move this to the support subforum? Or start a new thread there? I don't want to breach etiquette :)
Edit: Followed the instructions here, except for step 7. I'm thinking I should figure out why my wireless switch won't turn on now before I proceed!

Edit: SORRY FOR ALL THE EDITS! I ran system testing and noticed this:
```
Detecting your network controller(s):

nVidia Corporation MCP77 Ethernet (rev a2)
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

Is this correct?
```
Is the first one a competing driver? Should I blacklist it?

---

### Post by matt-fender on 2010-06-30
The first one is your ethernet connection, it "shouldn't" make a difference. Do you have much to lose? It really could be worth you re-installing and using ndiswrapper with ndisgtk, off a clean slate?

---

