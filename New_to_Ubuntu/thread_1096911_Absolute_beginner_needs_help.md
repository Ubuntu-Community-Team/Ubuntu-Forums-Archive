---
title: "Absolute beginner needs help"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Rhetoric Camel on 2009-03-15
Hi I've just installed Ubuntu 8.10 onto my computer out of curiosity of this Linux that so many people rave about. I'm interested in learning and seeing what it's about although I see that games, autodesk maya, and photoshop aren't things that can be used in linux, and I use them all the time, so I can't give up windows just yet unfortunately.

Anyway my question, I can't get the internet working, wireless internet. I have a BUFFALO WLI2-PCI-G54S Wireless card in my computer and using a Linksys WRT54GS router, with Charter Communications as my provider, here in Plattsburgh, NY. I thought it was supposed to pick up the connection automatically, maybe I just misread everything or maybe it's easier than I think. Any help on getting the internet up and running in Ubuntu would be greatly appreciated. It's kind of a pain rebooting just to get to the internet to ask a quick question.

Thanks for any help,
Mike

---

### Post by red_hawk on 2009-03-15
Try going to System -> Preferences -> Network Connections.  Then click on the "Wireless" tab and click on "Add".  There you should be able to add you wireless settings. It will automatically reconnect on standby or login.

---

### Post by Rhetoric Camel on 2009-03-15
see thats what I thought to, but it wouldn't connect after I added it like that. It's a protected connection so I have to put in a password and it doesn't ask for it unless I go into the Edit tab and make adjustments in there. Which settings should I have to add anyway?

---

### Post by red_hawk on 2009-03-15
I would not know about any support issues with your hardware, but I have found that a quick reinstall always helps.  =)

---

### Post by Rhetoric Camel on 2009-03-15
here are a few questions, what am I supposed to put in for SSID, BSSID, Security Type, and under the IPv4 Settings? 

Maybe I'm just not technologically smart enough to do this.... it's supposed to detect the connection upon start up and just connect right? hmmm I wonder why this didn't work for me.

---

### Post by leonardo_neo on 2009-03-15
I think you are going too deep.......:-k

On your taskbar you must see an icon which shows which shows about wireless connections. When you select view available networks, then it shows all the the available networks around you. When you select your network, it simply asks for the login password. That is how is should go?

---

### Post by rasmus91 on 2009-03-15
> On your taskbar you must see an icon which shows which shows about wireless connections. When you select view available networks, then it shows all the the available networks around you. When you select your network, it simply asks for the login password. That is how is should go?
yep
You just gotta left click on the icon that looks like two screens/monitors and select which network to connect to.

---

### Post by Rhetoric Camel on 2009-03-15
see that was the problem it didn't detect any network so I went to create a new one and that's where I got lost, I just uninstalled Ubuntu and will reinstall and hopefully that will make a difference.

---

### Post by ed89 on 2009-03-15
Just a comment regarding the Photoshop-issue: Give GIMP a try! It's good stuff, and included in Ubuntu under Applications > Graphics > GIMP Image Editor.

As for your wireless: I had the same problem when I first installed Ubuntu 8.10. The network didn't show up in the list of available networks.. I reinstalled Ubuntu and - I don't know what happened - now it's working :)

Good luck.

---

### Post by lkraemer on 2009-03-15
Mike,
You say you can't give up Windows, so you must have the windows drivers
for your wireless Buffalo card.  Look at your Windows Control Panel and
find out which driver is being used by Windows.  It might be bcmwl5.inf
or something similar.  Then search for that driver to find out what
folder it is in.  Copy that folder to a USB Memory Stick, then copy that
same folder to your Ubuntu install.  Now you are ready to start.
Boot Ubuntu and open a Terminal Window.

I wouldn't re-install anything.............No need to go through that
hassle.  Ubuntu isn't Windows.....thank goodness....it just works....

Open a terminal window:
```

lshw -C network
ndiswrapper -l

```
Then post the output displayed by both.

If there are drivers loaded, as shown by ndiswrapper -l, open a
Terminal window and remove all by:
```

sudo ndiswrapper -r b43
sudo ndiswrapper -r b44
......
......

```
These are examples only, your may be different.

If there are no drivers loaded open a Terminal window and do:
```

sudo ndiswrapper -i /path/to/bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

```
If you have an open router do the following in a Terminal Window:
```

iwconfig

```
This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below. Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi. Insert your
essid (UPPERCASE or lowercase specific)
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```
You should be able to surf, even though your LED for Wifi isn't "ON".


ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

You may have to blacklist some drivers, but hopefully not at this point.

lkraemer

---

### Post by Rhetoric Camel on 2009-03-15
> **lkraemer said:**
> Mike,


thank you for your help I will give it a shot later, I've just spend 3 hours screwing around with this and I'm a bit frustrated to even reboot yet again to load Ubuntu and try this, I will give it a shot but not at the moment, I need a break from getting no where.

Edit: The file is in the system32 folder, do I copy that entire folder to my USB drive or do I just copy the specific file?

---

### Post by Rhetoric Camel on 2009-03-15
so yeah I really don't think I know what I'm doing at all, don't know where to install the driver and don't know if you want to install the entire windows>system32>drivers folder, or just the BCMWL5.sys file.



lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:7c:a8:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.4-1 latency=0 module=e1000e multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:16:01:28:24:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 5
       logical name: pan0
       serial: 26:84:f5:b5:d3:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rhetoriccamel@ubuntu:~$

rhetoriccamel@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

don't know if this is helpful

---

### Post by lkraemer on 2009-03-15
Mike,
Are you running 8.04 LTS or 8.10?  32 Bit or 64 Bit?

Looks like you have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller

There are two ways to go.......
Use ndiswrapper and the Windows Drivers for your Broadcom Wifi Card
or use the Broadcom Firmware.

There is a posting on this site I ran across that has the URL for
the Firmware and also has instructions.
[http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

You might want to try it first.  I typically use ndiswrapper, but I am
of the old school.

lkraemer

---

### Post by Rhetoric Camel on 2009-03-15
I'm running 8.10 32bit. Thanks for the reply will look into it.

---

### Post by Bryantos on 2009-03-15
> **Rhetoric Camel said:**
> here are a few questions, what am I supposed to put in for SSID, BSSID, Security Type, and under the IPv4 Settings?

Just to help you better understand networking, I will define the following for you. ;)

**SSID**: This is simply the name of your wireless network. This is *typically* set when you are setting up the router. If you did not change the name, then it remains the default name depending on the manufacturer of the router. For example, those wireless networks you see named linksys, dlink, etc.

**BSSID**: Never heard this term before, but its basically the MAC address on your router. As far as I know, this *shouldn't* be needed and picked up automatically in the background using the ARP protocol. 

**Security Type**: The type of *encryption* you put as security on your router. All of the encryption happens in the background, but if this is enabled, which it sounds like it is in your case if you're entering a password to connect to your *wireless access point* (or WAP for short), then you simply enter the password you need to connect to your router and select the type of *encryption* you have set on your router. Typical algorithms, or types of security, for routers are WEP (DO NOT USE WEP!), WPA, and WPA2.

**IPv4**: This could mean a lot of things under the network settings. I'm pretty sure its asking for the IP adress of your router and not your public IP. Usually the defualt is 192.168.0.1 or 192.168.1.1.

I know its long, but I hope it helps you understand some aspects of networking.

Good luck! :D

---

### Post by Rhetoric Camel on 2009-03-15
my router is WEP never messed with the setting just because I didn't know what would happen if I changed it so I left it the way it was, what does it affect? Sorry for all the questions I appreciate the help and patience. I know a little about networking but obviously am stuck here, like I said it's becoming a pain to switch between windows and Ubuntu to try things and my printers not working so I can't print things out. Didn't think just setting up the internet connection would be so painful, hopefully it gets better if and when I get this up and running. I do like the way it's set up.

---

### Post by lisati on 2009-03-15
> **Rhetoric Camel said:**
> thank you for your help I will give it a shot later, I've just spend 3 hours screwing around with this and I'm a bit frustrated to even reboot yet again to load Ubuntu and try this, I will give it a shot but not at the moment, I need a break from getting no where.

Edit: The file is in the system32 folder, do I copy that entire folder to my USB drive or do I just copy the specific file?

I don't think you need to do anything drastic like copy the ENTIRE system32 folder - that's one of the main places where Windows keeps its files, most of which will be irrelavent to Ubuntu

---

### Post by chrisod on 2009-03-15
The first thing I would do is open the wireless connection and try to connect again. If you can get online without encryption we know the wireless driver is working ok and it may just be an encryption configuration issue.

---

### Post by Rhetoric Camel on 2009-03-16
ok so absolutely nothing is going as planned, I tried the [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/) and brought the file into Ubuntu on a flash drive, but I was unable to extract them to /lib/firmware said I didn't have permission because I'm not the owner.

I also got ndiswrapper-1.54.tar.gz on my flash drive and I have no clue how to install ndiswrapper so that has been unsuccessful

---

### Post by lkraemer on 2009-03-16
Mike,
You can do the following:

Copy both the b43-all-fw.tar.gz and ndiswrapper-1.50.tar.gz
to a folder on Ubuntu.   Let's call it tempfiles.

Now in a Terminal window do:
```

cd /
pwd
locate b43-all-fw.tar.gz

```
Your path to b43-all-fw.tar.gz should be:
/home/login_name/tempfiles/
Now do:
```

cd /home/login_name/tempfiles
ls -alt
chown login_name:login_name b43-all-fw.tar.gz

```
you should see the file b43-all-fw.tar.gz

```

tar zxvf b43-all-fw.tar.gz
cp *.fw /lib/firmware

```
this should extract your firmware files, and then copy them to
/lib/firmware

Mine look like this:
[larry@localhost b43]$ ls -alt
total 176
drwxrwxr-x 5 larry larry  4096 Mar 16  2009 ../
drwxrwxr-x 2 larry larry  4096 Mar 16 18:00 ./
-rw-rw-r-- 1 larry larry 22088 Mar 16 17:59 ucode5.fw
-rw-rw-r-- 1 larry larry 20080 Mar 16 17:59 ucode4.fw
-rw-rw-r-- 1 larry larry 24424 Mar 16 17:59 ucode13.fw
-rw-rw-r-- 1 larry larry 26600 Mar 16 17:59 ucode11.fw
-rw-rw-r-- 1 larry larry  1320 Mar 16 17:59 pcm5.fw
-rw-rw-r-- 1 larry larry  1320 Mar 16 17:59 pcm4.fw
-rw-rw-r-- 1 larry larry  2052 Mar 16 17:59 lp0initvals13.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:59 lp0bsinitvals13.fw
-rw-rw-r-- 1 larry larry  1858 Mar 16 17:59 b0g0initvals5.fw
-rw-rw-r-- 1 larry larry  2680 Mar 16 17:59 b0g0initvals4.fw
-rw-rw-r-- 1 larry larry  2056 Mar 16 17:59 b0g0initvals13.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:58 b0g0bsinitvals5.fw
-rw-rw-r-- 1 larry larry    18 Mar 16 17:58 b0g0bsinitvals4.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:58 b0g0bsinitvals13.fw
-rw-rw-r-- 1 larry larry  1858 Mar 16 17:58 a0g1initvals5.fw
-rw-rw-r-- 1 larry larry  2056 Mar 16 17:58 a0g1initvals13.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:58 a0g1bsinitvals5.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:58 a0g1bsinitvals13.fw
-rw-rw-r-- 1 larry larry  1858 Mar 16 17:58 a0g0initvals5.fw
-rw-rw-r-- 1 larry larry  2680 Mar 16 17:58 a0g0initvals4.fw
-rw-rw-r-- 1 larry larry   158 Mar 16 17:58 a0g0bsinitvals5.fw
-rw-rw-r-- 1 larry larry    18 Mar 16 17:58 a0g0bsinitvals4.fw
[larry@localhost b43]$
Notice my permissions for each file are 664.  You may need to change
yours with the chmod command.  man chmod will give you the details.

At this point I would recommend you go to /home/login_name/tempfiles
and clean it up from the GUI.  I could lead you through the delete
process, but the GUI is the easy way. 

Back to a Terminal ........for ndiswrapper.....
```

cd /
pwd
locate ndiswrapper-1.50.tar.gz
cd /home/login_name/tempfiles
ls -alt
chown login_name:login_name ndiswrapper-1.50.tar.gz
tar zxvf ndiswrapper-1.50.tar.gz

```
This will extract ndiswrapper and you can follow the instructions for
the install.

Once again I would recommend going to the GUI to delete the files and cleanup everything when you are done.

lkraemer

---

### Post by brnetonboy on 2009-03-16
Regarding the games, Linux definitely has good games. You should try Battle for Wesnoth, for starters.

---

