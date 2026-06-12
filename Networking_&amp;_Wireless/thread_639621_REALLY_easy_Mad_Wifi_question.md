---
title: "REALLY easy Mad Wifi question"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by mblind on 2007-12-13
Hello,
 I replaced the Dell 3945 wifi card  with a GIGABYTE WI01GT Atheros Mini PCI-Express card on my Dell Latitude D830. 

Here is my simple question. I want remove the Atheros Restricted driver and install the Latest Mad WiFi driver. Any help please!!!

---

### Post by Junglizer on 2007-12-13
I don't know anything about the Atheros Restricted drivers, but...

Here's the rundown on how I would get the madwifi drivers working, I believe they are in the package tree but I've never done it that way, and the following method should work regardless of the OS. This is compiling from source and installation/configuration is all done from the command line.

Download the current release of the madwifi drivers [http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz"), thats the source.

Extract them and enter the newly created directory.
```

tar xvf madwifi-0.9.3.3.tar.gz
cd madwifi-0.9.3.3/

```
There should be a README or an INSTALL file, file which you can read using the less command.
```

less README

```
Pressing "q" quits from the less text viewer.
However, you can just do the following inside of the madwifi directory:
```

make clean
make
make install

```
The make process, the compile, takes about 5-10 minutes based on your system specs.
Once you've completed the 3 previous steps you can remove the directory, as all the contents have been installed in the proper locations on your system.
```

cd ..
rm -rf madwifi-0.9.3.3/

```
Using the drivers/utils:
You should now run
```

iwconfig

```
You will probably see a wifi0 device and an ath0 device. It may work right at this point, but I would recommend you start from scratch so you can see how to do this in the future.
```

wlanconfig ath0 destroy

```
This destroys the device association. We can recreate it using the following command, keep in mind that you may have to change this a bit for your system, but 9/10 times it will work just fine for most people:
```

wlanconfig ath0 create wlandev wifi0 wlanmode sta

```
We're creating an 'ath0' device to interface with the 'wifi0' kind of "front-end" if you will and we are putting it in 'sta' mode, which is the most common type. Specifically "client-server" or rather you connecting to an AP.

Now you'll want to find which AP's to connect to, so we scan for availble ones:
```

iwlist ath0 scan | more

```
Chances are pretty good taht you'll find your home AP in the list, we'll call it "homeAP" for the sake of this. So we associate with that AP.
```

iwconfig ath0 essid "homeAP"

```
Now we get a network address using DHCP.
```

dhclient ath0

```
Run ifconfig or iwconfig again to see that you correctly retrived an IP address.

You may have to edit /etc/resolv.conf based on your settings.
But that's the gist of it.

---

### Post by beorn! on 2007-12-13
i thought the package was called madwifi-source, but I am not finding it in my synaptic. My advice is to open synaptic package manager, click on the search button, and search for description "driver" navigate through til' you find atheros wireless driver. right click uninstall... 

Probably want to download the new driver first, and check the dependencies,  if wireless is your only network connection. Else you should just be able to open a terminal and do sudo apt-get install madwifi-source afterward.

---

### Post by Junglizer on 2007-12-13
> **beorn! said:**
> i thought the package was called madwifi-source, but I am not finding it in my synaptic. My advice is to open synaptic package manager, click on the search button, and search for description "driver" navigate through til' you find atheros wireless driver. right click uninstall... 

Probably want to download the new driver first, and check the dependencies,  if wireless is your only network connection. Else you should just be able to open a terminal and do sudo apt-get install madwifi-source afterward.

Yeah that might work, I really can't say, I run Slackware, which doesn't even have a package manager. So most of my responses just deal with compiling from source instead of using bins. I know this can be difficult for a lot of new users, but like I said in my original post it should work the majority of the time regardless of the distrobution.

---

### Post by mblind on 2007-12-13
uh, ok.. install worked. but now I am REALLY having a big issue.. My Ubuntu is not booting correctly.

after login loads part of the desktop.. but never totally completes the process!!! HELP!

---

### Post by Junglizer on 2007-12-13
What seems to be the issues durring boot up?

---

### Post by mblind on 2007-12-13
huh, Now everything is booting fine.. Uh, weird..

I do have a wifi problem.. I can connect to access points that have no PW..

But, if there is a PW I am unable to connect. (WEP)

---

### Post by Junglizer on 2007-12-13
Yeah I didn't include that bit, what I posted was some stuff I'd written a while back as a PM. This should be avalible under the documentation on the Madwifi site, or try ```
man iwconfig
```

---

### Post by mblind on 2007-12-13
Uh what do I do in there? I have Network Manager installed. Do I need to configure something else?

sorry, Just confused.

---

### Post by mblind on 2007-12-13
Ugh... It's look like I am still NOT using the mad wifi driver.. I need to disable the atheros Rescricted driver.. Yes?

laptop:~$ lsmod | grep ath_
ath_rate_sample        13056  1 
ath_pci                96160  0 
wlan                  204996  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               191696  3 ath_rate_sample,ath_pci
laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wifi0
       version: 01
       serial: 00:1a:4d:34:66:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.87.242.64 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:17:bd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes

---

### Post by Junglizer on 2007-12-13
> **mblind said:**
> Uh what do I do in there? I have Network Manager installed. Do I need to configure something else?

sorry, Just confused.

I don't use the gui to configure anything, not even the gui. I have no idea what options are in the Network Manager, or what it even looks like.  You can do everything right from the command line, so thats usually what I do, and what most of those configuration instructions are for, mine, or the ones on the Madwifi site.

---

### Post by xeth_delta on 2007-12-13
If you want to use a gui for configuring wifi, may I suggest wicd instead of network manager? You can find binaries and source code at [https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573"), wicd;s website is: [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/"). While using wicd, remember to place the passwords / pass phrases between quotes.

* I think wicd might already be included in the ubuntu repositories, check there first.

If you happen to hit a bug in the madwifi drivers, in which the connection is dropped and error messages are present in dmesg, use the following from a terminal:
```
iwpriv wlan0 bgscan 0
```.
This workaround seems to work for most of the cases.

Xeth

[EDIT] see *

---

### Post by EZ2NV on 2007-12-14
I'm having problems installing madwifi!  Whenever I try to issue the 'make' command in Terminal, I get the following:

Checking requirements... ok.
Checking kernel configuration... FAILED
Please enable wireless extensions.
make: *** [configcheck] Error 1

Now, I am, admittedly very new to the wonderful world of Linux.  So if anyone could please help me!  If I could just get my wireless card up and running!  How do I enable wireless extensions?

---

### Post by EZ2NV on 2007-12-14
EDIT

I fixed it!  I ended up using ndiswrapper.  You can find directions here:
[http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48)

---

### Post by Junglizer on 2007-12-14
Ndiswrapper is lame, but I'm glad you got it working, it should be sufficent for your needs. Granted, no one even responded to my Aironet 350 RF Mon post. :'(

---

### Post by GSF1200S on 2007-12-14
> **mblind said:**
> Ugh... It's look like I am still NOT using the mad wifi driver.. I need to disable the atheros Rescricted driver.. Yes?

laptop:~$ lsmod | grep ath_
ath_rate_sample        13056  1 
ath_pci                96160  0 
wlan                  204996  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               191696  3 ath_rate_sample,ath_pci
laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wifi0
       version: 01
       serial: 00:1a:4d:34:66:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.87.242.64 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:17:bd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes

Can I ask you *why* you want to not use the restricted manager? That driver is giving me 12mb/s and I have the same exact card. Now thats not 54MBps, but then my ISP doesnt offer anything over 11MBps, so it works for me. Im not sure if the madwifi drivers from the site are any faster- in fact they may be the same ones!

Open up synaptic and search for restricted- im using Adept and KDE, but you should be able to see by my screenshot what youre looking for. You need to remove that, but be advised: the proprietary ati and nvidia common kernels are bundled with these. If you remove this package, be sure its only removing things you dont need. If youve already installed nvidia drivers from the website, you no longer need this anyways (not sure about ati). However, anytime you update xorg.conf or the kernel, youll need to recompile both the madwifi drivers and reinstall the video driver- and since you wont have the repo driver, make sure you have a copy of the madwifi drivers on hand so you can recompile them and get back online! Ask if you have any more questions...

**EDIT** I dont know how I missed you having fixed it with ndiswrapper, but I did. I could never get ndiswrapper to work, of course that was in the days of edgy.  Well, if you do roll over to madwifi, you can use the above. If not, at least you got it fixed...

---

### Post by Junglizer on 2007-12-14
> **GSF1200S said:**
> Can I ask you *why* you want to not use the restricted manager? That driver is giving me 12mb/s and I have the same exact card. Now thats not 54MBps, but then my ISP doesnt offer anything over 11MBps, so it works for me. Im not sure if the madwifi drivers from the site are any faster- in fact they may be the same ones!


I don't believe that the speed restriction is soley the reason not to use these drivers, it falls under the same category as NDIS since you are not using a driver that has full firmware access  you miss out on some of the cards functionallity, rfmon mode, powersaving, channel hopping and the like. As I mentioned before this is not something the average user needs to ever worry about if all they want is an internet connection, but once you get into network monitoring and network programing this is key and restricted drivers and NDIS just won't do.

---

### Post by mblind on 2007-12-15
I reinstalled Ubuntu.. now things work.. Still not using MadWifi driver. Oh well..

---

