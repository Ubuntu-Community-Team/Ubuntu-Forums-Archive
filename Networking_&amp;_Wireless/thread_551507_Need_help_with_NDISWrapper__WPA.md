---
title: "Need help with NDISWrapper / WPA"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by ivan09193 on 2007-09-15
I have a TEW-423PI card with a Realtek chipset (that's a TRENDNet card) in a computer I'm installing Ubuntu 6.06 on.  While the card did work out of the box, it had no support for WPA encryption, which I know the card can use in Windows.  I tried using the Windows XP Drivers on the CD with NDISWraper and its graphical front end.  Although the drivers did install successfully, I still do not have any WPA support in the Gnome Network Manager Applet.  Is there any way of getting TEW-432PI cards working with WPA in Ubuntu 6.06?

---

### Post by wieman01 on 2007-09-15
The WIndows drivers might not support WPA. Try to get the latest version from the vendors website.

---

### Post by ivan09193 on 2007-09-15
I'm certain the Windows drivers support WPA, and they are the latest drivers from the vendor's site.

---

### Post by wieman01 on 2007-09-15
Then you could try the tutorial (see signature) or give WICD a go first. It does work for a lot of people:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by kevdog on 2007-09-15
Requirements
1.  The wpa_supplicant package.  If you have not installed it then:
```
sudo aptitude install wpasupplicant
```
2. A wireless driver that supports WPA.  I have no idea how to check this.  Most modern drivers do, the only exceptions I know about are some older Realtek drivers, Orinico, Prism drivers.
3. Access to wireless router -- For testing purposes I am assuming WPA(1) not WPA2.  TKIP cipher with PSK.

Ok, the next step we are going to do is to try to configure everything by hand manually.  Note that this is not the permanent solution.  Because you are having problems, this gives us a window to receive debugging statements and make adjustments as necessary.  So please dont think this is how its going to be done everytime!

Ok lets start:

Create a wpa_supplicant.conf file
```

gksu gedit /etc/wpa_supplicant.conf

```

Contents of the wpa_supplicant.conf file are the following:
This example is assuming WPA (not WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```

Next find your interface name (ie wlan0, eth1, etc).  In order to do this:
```

lshw -C network

```

Find your wireless section, and then look for logical name -- this is your interface name (An example below)
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

The following is an example of what to type at the command line to bring up your network with wpa manually.
Assumptions:
1. Interface name is wlan0
2. Wireless driver is ndiswrapper (known as wext).  (See man wpa_supplicant for alternative choices)

A lot of debugging output will be given (the whole purpose of this exercise). You  may get some errors on the first few commands -- dont worry about it -- these instructions are somewhat overkill.  Im concerned about any errors you get at the end.

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by wieman01 on 2007-09-15
**@ivan09193:**

Install "wpasupplicant" first and check if the WPA option appears in Network Manager after you have done so. Reboot if necessary. If that does not help, then follow the steps that Kevdog has outlined.

Dapper Drake does not come with "wpasupplicant" installed by default. I missed that point. It is a necessary package for WPA.

**@Kevdog:**

That is a WPA1 (TKIP) script. Could you also provide one for WPA2 (AES, RSN)? Thanks, mate.

---

### Post by ivan09193 on 2007-09-15
The command sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd looks for my SSID, can't find it and repeats the process.

The output of lshw -C network is the following:

tsarivan@tsarivan-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@02:06.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:30:d8:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b/g
       resources: ioport:c000-c0ff iomemory:ec010000-ec0103ff irq:201

I installed the Windows drivers (rtl8185) using the graphical frontend of NDISWrapper.  However, it shows me using the "rtl8180" driver.  Is there any way to fix this?

---

### Post by kevdog on 2007-09-15
Yes -- at least you are learning;

echo "blacklist rtl8180" | sudo tee -a /etc/modules

Reboot and then check lshw -C network to make sure your card is assigned the ndiswrapper driver

---

### Post by ivan09193 on 2007-09-15
Used echo "blacklist rtl8180" | sudo tee -a/etc/modules.  Upon reboot, checked lshw -C network to receive the same output as shown before.  It still uses the rtl8180 drivers.  Also, I went into /etc and added the line blacklist rtl8180 to modules~, went into /etc/modprobe.d and added blacklist rtl8180 to the blacklist file.  Again, the same result on reboot.  Still no WPA.

---

### Post by kevdog on 2007-09-15
Sorry, I know you did this already, but the blacklist statement was supposed to go into /etc/modprobe.d/blacklist instead of /etc/modules.  I would just open and edit the modules file and remove the blacklist statement

Ok, I see your problem

Also try this

sudo modprobe -r rtl810

And then reboot.

---

### Post by ivan09193 on 2007-09-15
Tried both sudo modprobe -r rtl810 and sudo modprobe -r rtl8180, both of which could not find such a module.  Removed the blacklist statements from modules, kept them in blacklist.  Still no result.

---

### Post by kevdog on 2007-09-15
This is really strange

Im looking to see what modules are in my kernel and am finding rtl8187 and rtl818x and rtl8150

To see what modules you have
sudo updatedb
locate rtl81

This should bring up all the modules.  You may have more than one kernel in the system.  To find out your kernel version - uname -r

Then look under the directories pertaining to your kernel.  Depending on the modules you found, I would try blacklist and modprobe -r the modules (Again this process is reversible so dont worry that you are going to break anything)

---

### Post by ivan09193 on 2007-09-15
I tried blacklisting two of the drivers I found when I used locate rtl81, r818x and r8185 which were in a directory having to do with wireless drivers.  Upon reboot, the boot process now hangs when it registers scsi devices.  What is happening?  I think I'll have to reinstall Ubuntu.

---

### Post by ivan09193 on 2007-09-15
I've reinstalled Ubuntu and installed ndiswrapper + gtk ndiswrapper + the Windows drivers for the card.  Again, I'm stuck at the same point I was before with the rtl8180 problem.  Is there any easy way to change the driver a card uses?

---

### Post by kevdog on 2007-09-16
Driver is hardware dependent, meaning unless you change the hardware.....

That's really strange.  Im sorry I cant give you any more input.  Have you tried just blacklisting the rt818x module only??

---

### Post by wieman01 on 2007-09-16
**@ivan09193:**

If I were you I would upgrade to Feisty and install WICD. It reportedly works for a lot of people and it might spare you the trouble of having to replace the driver. Dapper is a bit outdated, like it or not. Upgrading to Feisty might be the solution. :-)

---

### Post by ivan09193 on 2007-09-26
I upgraded to Feisty and installed wicd.  I also installed ndiswrapper and installed the driver for my card.  It recognized the card, and used the driver for it.  In wicd, I can see the network I want to connect to.  However, when I try to connect using WPA encryption, the connection proceeds up to the point of acquiring an IP address and times out.  It seems like I am really close to getting this, but I'm just not quite there yet.

---

### Post by kevdog on 2007-09-27
You need to ensure your driver supports WPA -- which I cant tell you if it does or not. You may need to google for it

Make sure you have installed the wpasupplicant package

Make sure essid on router is being broadcast.

Hmm I cant remember anything else off the top of my head.  If you cant get wicd to help you, we may have to go to a manual connection so we can debug.

Look in /opt/wicd/wicd.log and see if there are any messages that help debugging.  Also check dmesg to see if you see anything.

---

### Post by ivan09193 on 2007-09-29
Actually, I am using a hidden SSID on my router.  However, Wicd has an option for hidden SSIDs.  Does this make a difference?

---

### Post by kevdog on 2007-09-29
Broadcast your ssid for now -- just keep it simple until you get a working connection then you can change the settings.

---

### Post by Cuppa-Chino on 2007-09-30
ok... maybe a strange question but I will fire off...
 
thought I would install gutsy beta on laptop and worked fine except I cannot get a consistent wireless connection....

at every restart I need to hack in:

```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

```

I know I am missing something but what

---

### Post by atatistcheff on 2007-10-03
I FINALLY got WPA working with my Atheros card.  However, it's kind of a kludge and I want to get some advice on the best way to do this going forward.  I tried for hours editing the /etc/network/interfaces file following the instructions of another thread.  Nothing here worked.  Then I tried editing the /etc/wpa_supplicant.conf file as described in this thread.  Using this and the manual load steps I was able to finally get my laptop to authenticate to the access point.  

The problem is that this only works when I load everything via the commands in this manual example.  I've created a script that does this but it seems to me there should be a better way.  Here's the script that works:

#!/bin/sh
ifconfig ath0 down
ifconfig ath0 0.0.0.0
dhclient -r ath0
killall dhclient wpa_supplicant dhclient3
rm /var/run/dhclient.pid
wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd &
ip route flush dev ath0
ifconfig ath0 up
iwconfig ath0 mode Managed
dhclient ath0

Here are my questions:
1.  Is there a GUI to manage this configuration so I don't have to edit text files every time I want to connect to another access point? (the network GUI doesn't have anything in it regarding WPA)
2.  What's up with the /etc/network/interfaces file?  Why do some of the instructions say to edit this file and others say to edit /etc/wpa_supplicant.conf?
3.  Even if there's not a GUI, there must be a better way to make this work than my little script above.

Thanks!

---

