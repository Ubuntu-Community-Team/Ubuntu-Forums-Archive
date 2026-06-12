---
title: "yet another newbie with questions!!!"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by crazyforpurple on 2007-10-08
Hello, 

I have just bought a new Toshiba Satellite A135-S7404. I have installed Ubuntu version 7.1 Beta on the laptop and and now struggling ... (along with everyone else! :)) to get the wireless working. 

I have determined that I have an Atheros AR5006EG with the PCI ID 168c:001C. 

I Have used ndiswrapper to install the drivers according to the tutorials but when i go to set up the connection i am only offered wired or modem connection. 

in the terminal i get this message:

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

and when i go to restricted drivers manager i see that device is enabled and a green light is next to it. 

I ahve also searched the forums and see that many people have luck with madwifi, so  i downloaded them from there but have no idea how to install the tar.gz file. 

do i maybe have a conflict between drivers? if so how do i go about correcting this? how do i use madwifi to install drivers? whats all the talk of preparing the kernel?

please be gentle with me as i am very new to linux but really want to persevere with ubuntu as i HATE windows! any help and advice you could give  me would be greatly appreciated. 

Thanks in advance xxx

love lucy xxx

---

### Post by Lambert on 2007-10-08
It looks like you possible have 2 drivers loaded for this device.

Run the following commands and post the output.

```

sudo lshw -C network

sudo lsmod | grep ath

sudo lsmod | grep ndis

sudo modinfo madwifi


```

You won't have to compile or build the madwifi driver unless you want/need to use a newer version. There is a package you install called linux-restricted-modules-xxxxxx that has the madwifi driver part of it. With the output you gave above of ath_pci it's possible it's already installed.

---

### Post by crazyforpurple on 2007-10-09
firstly i want to thank you for your willingness to help me with this, i am thankful that you are doing so and hope that we can get this thing online with WIFI!  

first an update, last night i was worried that i had done something wrong when i installed the drivers using ndiswrapper so i actually re installed ubuntu and left it like that to start with. the ubuntu wiki on madwifi says that it should just work out of the box but it does not :( im thinking that maybe i need to uninstall the madwifi or de activate the drivers and try to use ndiswrapper again? let me know what i should do now after running these commands given by you. 

IO appologise for the length of these but i am just copying and pasting what i get back from the terminal as it doesnt mean a whole lot to me right now!:confused:

mommy@mommy-laptop:~$ sudo lshw -C network
[sudo] password for mommy:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:44:e8:ea
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s



mommy@mommy-laptop:~$ sudo lsmod | grep ath
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci



mommy@mommy-laptop:~$ sudo lsmod | grep ndis
mommy@mommy-laptop:~$ 


mommy@mommy-laptop:~$ sudo modinfo madwifi
modinfo: could not find module madwifi
mommy@mommy-laptop:~$ 


Please tell me this means something to you and that it means that i can fix my WIFI connection! Thank you for any and all your help xxx

lucy xx

---

### Post by crazyforpurple on 2007-10-09
i was just browsing through the ubuntu WIKI and came across this 

WifiDocs/Device/AR5006EG

Support for this card is not yet in a released version of madwifi (support coming just after the December 7th release). So you need to build your own madwifi drivers or use ndiswrapper. My card is the one that appears in Toshiba's A105-S2101 Satellite Series Laptop, and ndiswrapper performance left a lot to be desired. I built drivers using [WWW] the instructions from madwifi for Ubuntu. 

from this link: [https://help.ubuntu.com/community/WifiDocs/Device/AR5006EG?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/AR5006EG?highlight=%28WifiDocs%2FDevice%29)

with this info and the info that has come about from the commands that you gave me should i go ahead and follow the procedure given on the madwifi wiki or do i need to do anything else first? where are specific instructions for madwifi for ubuntu? and if i go ahead with this is it going to conflict with anything i already have in the kernel?

sorry for so many questions... but i am enjoying learning this new operatiung system even if it can be very frustrating at times ;)

thanks xx

love lucy xx

---

### Post by kevdog on 2007-10-09
Hmmm -- why dont you just go with ndiswrapper if you have access to the winxp drivers for your card, and then later if you want you can switch over to the madwifi drivers.  Unless you want to do some crazy things like aircrack, or packet injection, either way should give the same results.

---

### Post by crazyforpurple on 2007-10-09
i just went into my restricted device manager and it shows the driver there with a green light but it said it was not enabled, so i clicked on it to enable it, restarted the computer and its still cant see the wifi card, i have tried toggling the switch for the WIFI on and off to no avail! 

i am happy to try the ndiswrapper again but first so i need to do anything else that go back into the restricted drivers thingy and disable them again? do i have to blacklist or remove anything?  yesterday when i did ndiswrapper it saw the driver but not the card, could there have been a conflict? or should i just try different windows drivers?

as for the commands that lambert gave me i have now rerun them since i enabled the restricted drivers and i get this info:

mommy@mommy-laptop:~$ sudo lshw -C network
[sudo] password for mommy:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:44:e8:ea
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s



mommy@mommy-laptop:~$ sudo lsmod | grep ath
[sudo] password for mommy:
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci
mommy@mommy-laptop:~$ 



mommy@mommy-laptop:~$ sudo lsmod | grep ndis
mommy@mommy-laptop:~$ 


mommy@mommy-laptop:~$ sudo modinfo madwifi
modinfo: could not find module madwifi



im not sure how this differs from what i got when the restricted drivers were disabled but i hope it makes sense to you!

love lucy xx

---

### Post by kevdog on 2007-10-09
The restricted drivers (which are the madwifi drivers -- not sure what version) are loaded -- you can see that in the lsmod statement above.  However in the lshw statement your wireless device is coming back as unclaimed meaning these drivers "are not claiming" the device -- basically they dont support your card

All of this is just confirming what you already knew.

I would compile ndiswrapper from source and use the winxp driver.  Do you know how to compile from source???

---

### Post by crazyforpurple on 2007-10-09
thank you for explaining that to me.  

as for compiling ndiswrapper from source i am not sure that i know 100% how to do that (when i have done it previously i have started by using synaptic package manager?).

If you dont mind walking me through how to do this i would be very grateful... that way i can eliminate the fact that i may make an error making it easier to diagnose why if it still doesnt work once we have finished!

also before i go ahead should i do anything about these restricted drivers? and i have read things about preparing the kernal but again am not sure what that means!

thank you so much 

lucy xx

---

### Post by Lambert on 2007-10-09
See section five of this page.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Once you have it compiled you can go back up to section three and work down. When you get to the black list section, black list ath_pci, not the bcm43xx module.

---

### Post by kevdog on 2007-10-09
You can either uninstall the restricted drivers, or blacklist them so they are not loaded on startup, or do nothing.  Having drivers loaded into the kernel without the hardware using the drivers I dont think does anything.  Technically you should remove or inactivate them, but thats a textbook answer.  Give me second to pull up the ndiswrapper instructions.

---

### Post by crazyforpurple on 2007-10-09
thank you to both lambert and kevdog for your replies. 

i have bookmarked the page 
"How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line" for future reference one i have installed my drivers. 

i am now working my way through 

WifiDocs/Driver/Ndiswrapper page as suggested and was making great progress with step 5 until here.....

mommy@mommy-laptop:~$ cd /home/mommy/Desktop
mommy@mommy-laptop:~/Desktop$ tar xvfz ndiswrapper-148.tar.gz
tar: ndiswrapper-148.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mommy@mommy-laptop:~/Desktop$ 

can you tell me what this means and what i am doing wrong? if i remember correctly from when i used ndiswrapper before there was a problem with the xvfz part of the command and i had to type a slightly different command? 

what should i do now please?

thanks, 

lucy xxx

---

### Post by crazyforpurple on 2007-10-09
ok now i am very confused!!! 

i went to the ndiswrapper wiki and they had the following command:

tar -zxvf ndiswrapper-version.tar.gz

and i still get this in the terminal:

mommy@mommy-laptop:~/Desktop$ tar xvfz ndiswrapper-148.tar.gz
tar: ndiswrapper-148.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mommy@mommy-laptop:~/Desktop$ 
mommy@mommy-laptop:~/Desktop$ tar -zxvf ndiswrapper-version.tar.gz
tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mommy@mommy-laptop:~/Desktop$ 


i am now officially stuck! please help!

love lucy x

---

### Post by crazyforpurple on 2007-10-09
SCRAP MY LAST MESSAGES!!! ROOKIE MISTAKE!!! TOO MANY TYPOS TO MENTION!!!

i am now continuing happily through step 5! :)

---

### Post by crazyforpurple on 2007-10-10
ok so now i really DO need some help!!!

i have worked my way through step 5 and then back to the begining installing the windows drivers using ndiswrapper and ndiskgt and when i check to see if they have installed i get this:

mommy@mommy-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

even though i did follow the steps to blacklist the native atheros drivers. (can someone tell me how i can check this blacklist please?) it seems that it still has 2 drivers which may be conflicting? 

also when i run this command:

mommy@mommy-laptop:~$ lshw
WARNING: you should run this program as super-user.
mommy-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1509MB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        530  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          size: 200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe x86-64 constant_tsc up pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:38:44:e8:ea
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.105 latency=0 module=r8169 multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=57 maxlatency=4 mingnt=7 module=sdhci
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
mommy@mommy-laptop:~$ 
mommy@mommy-laptop:~$ 

it says the network is unclaimed??? and there is no driver listed by it.

also in the troubleshooting section it states:

If you cannot connect, make sure eth0 (or any other network interface that may be in use) is down/deactivated. do i ahve to do this? if i do deactivate eth0 will that remove my wired connection? im afraid to try it incase i end up with no internet access at all. 

and lastly, i am reading about telling the system to automatically load the module on start up, am i supposed to do this now even though i can get on the WIFI network? again i dont want to do things in the wrong order but i'm wondering if i need to do this first in order for it to be able to see it?

when i click on the network manager currently and click on configure, it still only gives me 2 options.... the wired option and modem. 

thanks for your help and time xxx

lucy xx

---

### Post by kevdog on 2007-10-10
Just a hint 

Dont be scared -- you are not going to break anything!!

Ok on to buiness

#1.  To bring down your wired interface
sudo ifdown eth0

#2. To bring up your wired interface
sudo ifup eth0

You might run into a problem if you are given a dynamic IP address by the router (Im not sure)
You might have to do the following
sudo ifdown eth0 <----Brings down interface
sudo dhclient -r eth0 <----Release the dynamic IP address assigned to eth0
sudo ifup eth0 <------ Brings up eth0 interface
sudo dhclient eth0 <---- Request new dynamic IP address to be assigned to eth0

Try with the simpler version first.  If it doesnt work then try the 4 step approach.

Onto ndiswrapper
ndiswrapper is simply a wrapper.  Once you wrap the windows driver (which it looks like you have done by checking ndiswrapper -l), you need to insert ndiswrapper as kernel module into the kernel.  This is done:
sudo modprobe ndiswrapper

If ever in the future you need to unload the module (say you wanted to change the windows driver or something)
sudo modprobe -r ndiswrapper <--- This unloads the ndiswrapper kernel module, however additional steps would be needed to remove the windows driver from inside ndiswrapper

Once you have loaded the ndiswrapper kernel module, check and see if the module has claimed the device:
lshw -C network

You should see in the output under the wireless portion, your device listed, and towards the bottom there should be something like driver=ndiswrapper.....

If you have this then you are in business -- you only need now to physically make the connection to your network, however you are done setting up the drivers for your wireless card

3. The ndiswrapper kernel module by default is not loaded at boot time.  To make it load at boot time you need to edit the /etc/modules file (gksu gedit /etc/modules) and then add ndiswrapper at the bottom of the file in a line all by itself.  A quicker way of doing this whole process would be to:
echo ndiswrapper | sudo tee -a /etc/modules

4. If you want to see what kernel modules are blocked or blacklisted from loading at boot, then peruse the /etc/modprobe.d/blacklist file. (more | /etc/modprobe.d/blacklist).  You can edit the file if you want (gksu gedit /etc/modprobe.d/blacklist) and either add or delete modules as you see fit.  I take it from your situation you hope to see ath_pci listed on a line by itself

Hope you learned something however Im sure you will run into a new series of problems next -- Good Luck!

---

### Post by crazyforpurple on 2007-10-10
THANK YOU THANK YOU THANK YOU!!!! 

my wireless card is installed and can see all the wireless networks in my area!!!! i cant tell you how excited i am and how very grateful i am to you for walking me through this step by step, thank you again xxx

yes i have learnt so much from this and have enjoyed every minute (well actually that would be a slight exaggeration.... its been very frustrating at times too!) but seriously i really have learnt a whole lot about the different ways that ubuntu installs things instead of windows... still not to say that i am going to be problem free from now on or not need help with my ubuntu jorney but its all one great learning curve. 

i am now off to try to connect to my WIFI network and then pray hard while i restart that it will just work each time!!!

thank you again xxxxxxxxxxxx

love lucy xxx

:D (doing a little happy dance)

---

### Post by crazyforpurple on 2007-10-10
I do need your help again!!!!

im sorry but im still having difficulty......

i can go through the motions connecting to the wireless network... it sees many of them in my neighbourhood.. i connect to mine via wep with a hex password and it says it connects, i have a little signal bar thingy in the top bar, but then it wont load any webpages???

i have followed the suggestions on this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-4a935665e4d7e4cc8ba4d40899e7001e1dcca587](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-4a935665e4d7e4cc8ba4d40899e7001e1dcca587)

and have the following information from my terminal:

mommy@mommy-laptop:~$ sudo invoke-rc.d networking restart
[sudo] password for mommy:
 * Reconfiguring network interfaces...                                   [ OK ] 
mommy@mommy-laptop:~$  sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:9e:55:c8:70
Sending on   LPF/wlan0/00:1b:9e:55:c8:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

mommy@mommy-laptop:~$   ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.027 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.026/0.026/0.027/0.005 ms


mommy@mommy-laptop:~$  ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:44:E8:EA  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe44:e8ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1855429 (1.7 MB)  TX bytes:397850 (388.5 KB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:55:C8:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72452 (70.7 KB)  TX bytes:15662 (15.2 KB)
          Interrupt:16 Memory:d8000000-d8010000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1B:9E:55:C8:70  
          inet addr:169.254.7.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:d8000000-d8010000 



mommy@mommy-laptop:~$   ping -c 4 169.254.7.167
PING 169.254.7.167 (169.254.7.167) 56(84) bytes of data.
64 bytes from 169.254.7.167: icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from 169.254.7.167: icmp_seq=2 ttl=64 time=0.025 ms
64 bytes from 169.254.7.167: icmp_seq=3 ttl=64 time=0.023 ms
64 bytes from 169.254.7.167: icmp_seq=4 ttl=64 time=0.025 ms

--- 169.254.7.167 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.023/0.025/0.030/0.006 ms


could it be a problem that my IP address starts 169 instead of 168?

mommy@mommy-laptop:~$   ping -c 4 216.239.57.99
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.

--- 216.239.57.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

following each of these steps it seems i can ping my router but not a website???

does this mean anything to you? what should i do now?

---

### Post by crazyforpurple on 2007-10-10
\\:D/   VERY VERY VERY HAPPY DANCE!!!

i am posting this with my WIFI connection!!!! 

i followed your link:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

i cant begin to say how grateful i am for your help xxxx
,love lucy xx

---

### Post by crazyforpurple on 2007-10-24
for anyone who is interested, I made a fresh install of gusty after it was released and I ahd to obviously go back in and install my wireless again and this time i documented what i did! 

I have made a new thread at 

[http://ubuntuforums.org/showthread.php?p=3622075#post3622075](http://ubuntuforums.org/showthread.php?p=3622075#post3622075)

with step by step instructions on how i got my wireless working on my toshiba satellite A135-S7404 and I hope it make sense to someone who needs help. 

I thank everyone who talked me through this the first time, your hekp is greatly appreciated xxx

love lucy xxx

---

