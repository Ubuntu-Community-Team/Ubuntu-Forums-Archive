---
title: "Linksys WUSB54GC Problems"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Darthape on 2008-06-27
I have the Linksys WUSB54GC usb card and I know that it should work out of the box with 8.04 but it doesn't. I believe that Ubuntu recognized that I had a wireless adapter because I can edit wireless networks but it does not show any networks or have any other function at all.

---

### Post by pytheas22 on 2008-06-27
Please post the output of:
```

iwconfig
lshw -C Network
lsusb
```

that will help us to figure out what's wrong.

---

### Post by jonofan on 2008-06-28
I have the same issue.

```
~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan3     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
~# lshw -C Network
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:41:dd:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:9a:77:30
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.54.103 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: 00:21:29:68:ad:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
```

~# lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 13b1:0020 Linksys 
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
```

---

### Post by jonofan on 2008-06-28
Have fixed this by using the XP driver on the WUSB54GC disc under ndiswrapper.

---

### Post by dragonfire2190 on 2008-07-01
Yeah same problem.

How do you do that - As stated above?

---

### Post by pytheas22 on 2008-07-01
> How do you do that - As stated above? 

Basically, you need to get the Windows drivers for your wireless card.  If they come as a .zip or .exe file, you need to extract it and find the file within with the extension .inf.  Copy the .inf file, as well as any files ending in .cat, .sys and .bin, to the Ubuntu system.

Then you do:
```

sudo apt-get install ndiswrapper* ndisgtk
sudo ndisgtk
```

A GUI will pop up and ask you where the .inf file is.  You find it, click ok, reboot and you should have a wireless connection.

Depending on your individual situation, however, it's not always as simple as this.  You should read the [community documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for a more complete guide to ndiswrapper.

Also remember that if your Ubuntu system is 64-bit, the Windows drivers that you load into ndiswrapper also need to be 64-bit.  This is a common source of confusion and frustration.

---

### Post by dragonfire2190 on 2008-07-01
Thank you

After a bit of confusion with the Hex key and passphrases I got it working and am now on wireless.

All praises to you. :):popcorn:

---

### Post by melp57 on 2008-07-01
> **pytheas22 said:**
> Basically, you need to get the Windows drivers for your wireless card.  If they come as a .zip or .exe file, you need to extract it and find the file within with the extension .inf.  Copy the .inf file, as well as any files ending in .cat, .sys and .bin, to the Ubuntu system.

Then you do:
```

sudo apt-get install ndiswrapper* ndisgtk
sudo ndisgtk
```

A GUI will pop up and ask you where the .inf file is.  You find it, click ok, reboot and you should have a wireless connection.

Depending on your individual situation, however, it's not always as simple as this.  You should read the [community documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for a more complete guide to ndiswrapper.

Also remember that if your Ubuntu system is 64-bit, the Windows drivers that you load into ndiswrapper also need to be 64-bit.  This is a common source of confusion and frustration.
this would work only if you have internet connection. I dont because my wireless card does not work......now what?  :)

---

### Post by pytheas22 on 2008-07-01
> this would work only if you have internet connection. I dont because my wireless card does not work......now what? 

Just a little extra work.  Conveniently, the ndiswrapper packages come on the Ubuntu live CD.  So make sure that your system is configured to use the live CD as a repository by going to System>Administration>Software Sources and checking the appropriate box under the "Installable from CD-ROM/DVD" section.  Close the dialogue and agree to reload the sources list when you're prompted.

Then you can simply use apt-get to install ndiswrapper:
```

sudo apt-get install ndiswrapper* ndisgtk
```

After that, install the Windows drivers for your card (which you should transfer to your Ubuntu computer using a USB driver or whatever you have available) with ndisgtk:
```

sudo ndisgtk
```

I wrote this quickly so if anything needs clarification please ask.

---

### Post by melp57 on 2008-07-01
> **pytheas22 said:**
> Just a little extra work.  Conveniently, the ndiswrapper packages come on the Ubuntu live CD.  So make sure that your system is configured to use the live CD as a repository by going to System>Administration>Software Sources and checking the appropriate box under the "Installable from CD-ROM/DVD" section.  Close the dialogue and agree to reload the sources list when you're prompted.

Then you can simply use apt-get to install ndiswrapper:
```

sudo apt-get install ndiswrapper* ndisgtk
```

After that, install the Windows drivers for your card (which you should transfer to your Ubuntu computer using a USB driver or whatever you have available) with ndisgtk:
```

sudo ndisgtk
```

I wrote this quickly so if anything needs clarification please ask.
Thanks for the reply, I will try and see if this works for me :)

---

### Post by rubing on 2008-07-12
I am running 8.04 xubuntu and am having similar problems.  It works out of the box intermittenly.  If I use the windows drivers via ndiswrapper it is better, but is still problematic (frequent crashing)

---

### Post by pytheas22 on 2008-07-13
> I am running 8.04 xubuntu and am having similar problems. It works out of the box intermittenly. If I use the windows drivers via ndiswrapper it is better, but is still problematic (frequent crashing)

The next time it crashes, please open a terminal (Applications>Accessories menu) and run the command:
```

dmesg
```

and please post the output here.  Hopefully it will provide a clue as to why the crashes are occurring.

Do the rest of you in this thread who are using ndiswrapper have problems as well?  I don't have this kind of wireless card myself.

---

