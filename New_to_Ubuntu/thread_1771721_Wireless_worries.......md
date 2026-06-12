---
title: "Wireless worries......"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by razorlight on 2011-05-30
Hi, I'm a newbie!!,
   
  I am wrecking my brain trying to figure out how come I cant get my wireless network running.
  First off here's the basics:-
   
  I'm using a fairly old compaq presario C550EM
  operating system is the latest version of ubuntu. 11.04.
   
  I followed the help on the os and this is what it showed me.
   
  paul@paul-Presario-C500-GF848EA-ABU:~$ nm-tool
   
  NetworkManager Tool
   
  State: disconnected
   
  - Device: eth0 -----------------------------------------------------------------
    Type:              Wired
    Driver:            8139too
    State:             unavailable
    Default:           no
    HW Address:        00:16:D4:C2:3F:9D
   
    Capabilities:
      Carrier Detect:  yes
      Speed:           10 Mb/s
   
    Wired Properties
      Carrier:         off
   
   
  paul@paul-Presario-C500-GF848EA-ABU:~$ sudo lshw -C network.
  [sudo] password for paul:
  paul@paul-Presario-C500-GF848EA-ABU:~$ sudo lshw -C network
    *-network UNCLAIMED     
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:06:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:40400000-40403fff
    *-network
         description: Ethernet interface
         product: RTL-8139/8139C/8139C+
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 8
         bus info: pci@0000:08:08.0
         logical name: eth0
         version: 10
         serial: 00:16:d4:c2:3f:9d
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
         resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
   
  **I installed the suggested driver:-....I.E. As shown in additional drivers.**

  This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.
   
  the nm-tool showed the same whether the driver was uninstalled/deacttivated or acti vated for the                   broadcom, but. One other thing puzzles me why does it say NETWORK unclaimed?  
   
  If I go to networking on the toolbar at the top of the screen networking is enabled, but there is nothing to enable wireless networking, I cannot use the wireless button on the laptop, it doesnt do anything, suggesting that the driver installed or uninstalled had no effect.
   
  So  anyway I decided to reactivate the driver... and it couldnt do it, does the additional driver wizard have to be connected to the internet to reactivate a driver?  I got this....
   
  SystemError: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb) Could not resolve 'gb.archive.ubuntu.com'
  

I checked on the hp/Compaq website and they say the installed card/s are either:-
   
  **_Supported Devices and Features_**
Broadcom 802.11b/g WLAN Broadcom 802.11a/b/g WLAN Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter


or


**_Supported Devices and Features_**
Intel Wireless WiFi Link 4965 Intel PRO/Wireless 3945 Network Connection  Intel PRO/Wireless 2915 Network Connection Intel PRO/Wireless 2200  Network Connection.


Does this mean the additional drivers wizard is attempting to use a slightly different driver?


How can i detect what is the correct driver for my wlan card? I'm a pc technician who got brave so bear with me, only used to dealing with windows..


And its about time someone made a gui friendly  alternative to windows so thanks to everyone who puts in time on ubuntu so that muppets like me can have fun. lol.

---

### Post by dFlyer on 2011-05-30
Not sure if this will help you, but what I end up doing is starting synaptic and under quick filter type bcm which displays bcmwl-kernel-source. If its checked as installed just right click it and mark it for reinstallation. Once it's re-installed. Just reboot. Hopefully it works.

---

### Post by razorlight on 2011-05-30
Hi dflyer, haha, i wondered what synaptics did, (duh), as i said i'm a newbie, I tried what you suggested, and thought i could just X out of the program, and it asked me if i wanted to discard changes, i cancelled that and tried the button at the top of the screen..RELOAD, that tried to connect to the inernet. Was it trying to downlad the driver again?

I noticed that the boxes werent ticked next to the broadcom drivers does that mean they arent there?  I ticked them thinking it might apply them?

anyway sorry to say it didnt work,.

help...

---

### Post by dFlyer on 2011-05-30
You might want to make sure your hard wired to the internet first. Then run synaptic. Once you find bcmwl-kernel-source if it installed just right click the file and Mark for Reinstallation. This will download the file if it's not already in /var/cache/apt/archive. Then click apply this will remove and reinstall the program. A quick look, other than bcmwl-kernel-source there are no other bcm files installed. Remember you do need to reboot after you apply changes.

---

### Post by razorlight on 2011-05-30
thanks gary,  /var/cache/apt/archive.? I wouldnt even know where to start looking for that. off out now to find a hard wired source, Can you tell me of a site you'd recomend for studying ubuntu/linux from absolute basic? I havent got a clue what i'm doing really,its kind of learn as i make a mistake at the minute, lol.

---

### Post by wep940 on 2011-05-30
You can also do the following:

- temporarily hard wire a connection between your router and your PC
- open a terminal window (applications/accessories/terminal if prior to 11.04, if 11.04 using unity, move the cursor to the left until the menu pops out, click on the "+" and a selection of things will appear on your screen, scroll down in the middle section until you find terminal)

- type:

sudo apt-get update <press enter>

- click on system/administration/additional drivers (I *think* that would be in that same middle menu if you are using Unity - I had to fall back to 10.10 for now so I don't have Unity).

This should run for a little while and if it finds a driver it will install it.  When it finishes, look at the screen to see if it shows 1 or more drivers for your wireless - I'd choose the STA driver first with your adapter.

- physically disconnect the hard wire cable

- try your wireless again - you'll probably need to check to be sure "Enable Networking" and "Enable Wireless" are checked.

---

### Post by dFlyer on 2011-05-30
> **razorlight said:**
> thanks gary,  /var/cache/apt/archive.? I wouldnt even know where to start looking for that. off out now to find a hard wired source, Can you tell me of a site you'd recomend for studying ubuntu/linux from absolute basic? I havent got a clue what i'm doing really,its kind of learn as i make a mistake at the minute, lol.

The above directory is where apt saves it downlaoded files. Something you really don't need to know for now. This is a good link for Ubuntu basics:

[http://linux.about.com/od/ubuntu_doc/a/ubudg24t1.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t1.htm)

Just remember to take it slow and have fun. One learns by mistakes, so remember help is available when you ask.

---

### Post by grahammechanical on 2011-05-30
When lshw -C network says Unclaimed it means that there is no driver loaded. The other states are Claimed = Driver loaded but not functioning. Enabled = Loaded. so check the connection settings to the router. Disabled = exactly what it says.

Here is a link to the trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Remember, it sometimes takes a reboot for changes to settings to produce a result.

Do you set the network manager icon? If so, click on it. Do you see a list of wireless networks? Is there a tick mark against Enable Networking and Enable Wireless? Clicking on those lines to put ad and remove the tick mark acts like a on/off switch. If you switch the router off and on it will send out a broadcast that might stimulate a response from network manager.

Regards.

---

### Post by razorlight on 2011-05-30
Hi graham, been at this for about 6hrs now, i dont have an option to enable wireless...so cant see any wireless connections, I have reinstalled the STA driver for the broadcom 4311, it appears listed in the aditional drivers, and in synaptics, i cant power on my wireless card with the wifi button, physically took out the wifi card to check the spec matches with the driver loaded, checked in terminal again, not listing as having a driver as in blurb above...evem tried running dnsiwrapper and cocked it up, bit beyond me at the moment.....off now to bang my head on a wall and maybe go back to windows...zzzzz anyhelp appreciated.

thanks for the links fella's.

---

### Post by wep940 on 2011-06-04
It's possible you may need to blacklist some default Broadcom modules.  If you could, open a terminal window and post back the results of:

lsmod <press enter>

This will list the kernel modules that have been loaded, so we can see if some of the other Broadcom modules are loaded - if so, we need to blacklist those.

---

