---
title: "BCM4318 still not working"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Quotidian on 2007-08-18
Hello;

I followed this thread: [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177) , however, I have not have any success with my BCM4318 NIC.  

I have tried using bcm43xx, before attempting ndiswrapper.  I have tried using both wlan0 and eth1 as an alias via sudo kwrite /etc/modprobe.d/ndiswrapper.

However, when I tried the additional step listed, "modprobe ndiswrapper" and "echo ndiswrapper >> /etc/modules", I received a bash error telling me permission was denied - even when I used sudo.  

When it tries to connect to my router's open access point, it fails at 28%, which is when it attempts to configure.

I am running Ubuntu Feisty Fawn with KDE on a Dell Latitude D810.  

Would anyone have any idea how to get this card running?  : )

Thank you!

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"05B404117336"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:FF:31:2B
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


lshw:

>   *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:d2:5b:08
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5751-v3.29a ip=192.168.1.47 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfcf0000-dfcfffff irq:16
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 02
       serial: 00:0e:9b:d5:75:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 latency=64 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:dfbfe000-dfbfffff irq:18


---

### Post by Jamie Jackson on 2007-08-19
> **Quotidian said:**
> 
...
However, when I tried the additional step listed, "modprobe ndiswrapper" and "echo ndiswrapper >> /etc/modules", I received a bash error telling me permission was denied - even when I used sudo.  

"sudo modprobe ndiswrapper" gives you permission denied errors?

Also, what happens when you do: ```
echo 'ndiswrapper' | sudo tee -a /etc/modules
``` ..Which is the same sorta thing as "ndiswrapper >> /etc/modules" -- they both just add the line "ndiswrapper" to that file.
> 
When it tries to connect to my router's open access point, it fails at 28%, which is when it attempts to configure.

Where are you getting that "28%" from, by the way?

---

### Post by Quotidian on 2007-08-20
Thank you for your reply!  

Using sudo -s fixed the permission denied errors, and since then, the wifi light has been on.  It also changed the wlan0 to eth1 automatically.  

However, it still won't connect.  It can see my wireless network, but, when it attempts to connect, a little bubble pops up saying "Activating Wireless Network Connection" and notifies me of the progress. This is where the 28% number originated from.  Underneath where it lists the ESSID of my wireless netwok, and (eth1), it mentions the activation stage is "configuring device".  It never goes any further than this, and eventually times out.  

I have since tried sudo dhclient eth1, based on the advice given in another person's thread, as well as restarting my networking... but... nothing so far has worked.  

Perhaps it is as simple as manually configuring my connection... however, I am really quite new to Linux in general, and have no idea what this entails, or how to do so.

Hopefully that clarifies everything?  If you need anymore information, please let me know.  

Thank you once again!

---

### Post by Jamie Jackson on 2007-08-20
Maybe KDE's NetworkManager works a little differently than Gnome's, but could you clarify one thing?

The little icon on the status panel, from which the "little bubble pops up:" When you right click that icon and go to "About," does it mention something like "NetworkManager Applet 0.6.4"?

If not, could you describe how your experience differs?

This is a drawn out way of confirming that we're both on the same sheet of music (i.e., both looking at a variant of NetworkManager).

---

### Post by Quotidian on 2007-08-20
Thank you for the prompt reply. : )

The "About KNetworkManager" yielded that it is version 0.1, and that KDE is version 3.5.6.

---

### Post by notoriousdbp on 2007-08-20
Try installing wicd and using that instead of knetworkmanager

---

### Post by Jamie Jackson on 2007-08-20
> **Quotidian said:**
> Thank you for the prompt reply. : )

The "About KNetworkManager" yielded that it is version 0.1, and that KDE is version 3.5.6.

Okay, just checking. 

First, I can't vouch for that driver, but let's assume that it's workable, for the time being.

Start with "ndiswrapper -l" and stop if there are problems

If not, some of the following might be redundant, but I don't think doing these things twice will cause problems.

Do the following, one line at a time:
```

sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

If that doesn't work, try a reboot, and see where that gets you.

(Note: I'm getting this information from my own howto, found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").)

---

### Post by Quotidian on 2007-08-21
notorious: 
Being new to Ubuntu, I'd rather try to make KNetwork Manager work, than try to figure out where to get and install wicd, since it isn't listed in my package manager.  I tried googling for it, but I couldn't seem to find anything that wasn't too daunting or confusing for my level of experience.  Of course, if you could point me in the right direction to a user friendly how-to, it would be much appreciated. : )  

Jamie:  
The driver works fine on my windows partition, and I used the same driver (recovered from  a driver CD provided when I purchased the laptop) for ndiswrapper.  However, the original driver size was a 52 mb .exe file, so, I only extracted the bcmwl5.inf and bcmwl5.sys files.  Would I need the rest?  It was mostly self-installing files and the like, and nothing else really seemed useful.

ndiswrapper -l yielded:

```
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

However, the code you provided me to try did not work (although I did not have any errors) - even after a reboot.

---

### Post by Jamie Jackson on 2007-08-21
Yes, you just need the INF and SYS files.

However, a driver that works in Windows won't necessarily work with ndiswrapper/Linux. There are known transmission problems with some BCM4318 drivers in Linux that prevent successful connection to an AP. Definitely start with a driver that is known to work with ndiswrapper/Linux, such as the one (I'm guessing) in the 4318 tutorial you're following, or the 4318 part of [my howto]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

---

### Post by Quotidian on 2007-08-21
Without reinstalling Ubuntu, how can I remove my previous driver, so that I can install the one from your thread?

---

### Post by Jamie Jackson on 2007-08-21
I know there's an elegant way to replace the driver in a couple lines, but I don't know it exactly. This is overkill (to say the least), but it should go by quickly:

Edit: Don't run more than one line at a time, run each command individually.

```

sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper

#only if this file doesn't have 'blacklist bcm43xx' in it already
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

wget http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip
unzip Driverv3100640.zip; cp Driver/WinXP/* ./

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

#only if this file contains more than 2 lines, currently
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

sudo ndiswrapper -m

#only if this file doesn't have ndiswrapper in it already
echo 'ndiswrapper' | sudo tee -a /etc/modules

#only if this file doesn't have 'ENABLED=0' in it already
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

sudo /etc/dbus-1/event.d/25NetworkManager restart

#now reboot, to test that it's working after reboot

```

---

### Post by Quotidian on 2007-08-21
I hate to say it, but, that didn't work either... :(

---

### Post by misfitpierce on 2007-08-21
simple input...

sudo apt-get install bcm43xx-fwcutter

Click yes to extract firmware it will install then close terminal and wait a few min it should turn on... If not reboot.

---

### Post by Quotidian on 2007-08-21
misfitpierce:

Thank you for the suggestion, but that also did not work.  Upon install, I received this error  (I still rebooted and tried my wireless though... with no results):

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 112 not upgraded.
Need to get 25.6kB of archives.
After unpacking 119kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/universe bcm43xx-fwcutter 1:006-1 [25.6kB]
Fetched 25.6kB in 1s (17.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 77519 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--21:24:41--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:24:42 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Jamie Jackson on 2007-08-21
I've tried the ndiswrapper method and the backported native driver method--both times successfully--but I've yet to try the fwcutter method. I'll do that now...

Edit: Yeah, I see the problem. It's documented [here]("https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/127624").

---

### Post by Jamie Jackson on 2007-08-21
Well, if you're in the mood for an entirely different tack, this ought to remove my stuff, and install the backported native driver. (At the expense of some throughput degradation.)

Edit: Again, be sure to run one command at a time. Also, I got the native driver info [here]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated"), FYI.
```

# REMOVING MY STUFF
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/default/wpasupplicant

# open the next file, and remove the 'blacklist bcm43xx' line
gksudo gedit /etc/modprobe.d/blacklist

# INSTALLING THE NATIVE DRIVER STUFF
wget http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

Are you connected? If not, reboot.

At this point, I was connected at 1Mb/s. Issuing the following, while connected, should increase your throughput by 10 or 15x.

```

sudo iwconfig eth1 rate 36M

```

I don't yet know how how to make the "36M" stick, though.

---

### Post by Quotidian on 2007-08-22
Hooray!  That worked.  Thanks again for all the patience and help.  : )

---

### Post by kevdog on 2007-08-22
Jamie

Are you using network manager or some other networking GUI to manager your interfaces??

Im just trying to figure out a method for you to get:
```
sudo iwconfig eth1 rate 36M
```

to be permanent for you!!

---

### Post by Jamie Jackson on 2007-08-22
Hiya, kevdog,

Yeah, he's using KNetworkManager, and I'm using NetworkManager (Gnome).

That would be great if you figured out a way to make that rate stick.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-08-22
> **Quotidian said:**
> Hooray!  That worked.  Thanks again for all the patience and help.  : )

No prob, I'm glad you got it going! BTW, you didn't have to even reboot for it to work, did you? I don't think I did, but I don't remember. (I might codify these instructions, so I want to know for sure.)

---

### Post by Quotidian on 2007-08-22
Jamie:
I had to reboot, as my wireless connection didn't even show up in the knetwork manager.  I found that the extra step you gave me wasn't even necessary. Again, thank you for all the help!  (I'm really quite thrilled wireless is working, finally.)  : )

---

### Post by Jamie Jackson on 2007-08-22
Which step wasn't necessary? You mean the iwconfig step?

YMMV, but before that step, I was running at a significantly reduced rate. It wasn't too noticeable on the Internet, in general, but I went to YouTube to really put the wireless through the ringer. I noticed that videos would play for 10 seconds then stop... forever. Then I went through some benchmarking tests to diagnose the problem.

If YouTube is running at an acceptable speed, without buffering delays, then I would agree that you'll likely be happy as a clam without ever touching the rate. However, if that's not the case, then keep that iwconfig step in your toolbox...

---

### Post by siralphred on 2007-08-22
follow this thread...its pretty easy

---

### Post by Jamie Jackson on 2007-08-22
> **siralphred said:**
> follow this thread...its pretty easy

Did you forget a link or something?

---

### Post by Quotidian on 2007-08-22
> **Jamie Jackson said:**
> Which step wasn't necessary? You mean the iwconfig step?

Indeed,  Even on intensive sites like Youtube, I'm not experiencing anything different than normal with the card (using my experience of it on my windows.partition).

---

