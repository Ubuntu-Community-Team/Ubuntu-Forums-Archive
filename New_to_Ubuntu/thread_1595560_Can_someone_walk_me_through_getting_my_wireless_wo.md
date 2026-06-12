---
title: "Can someone walk me through getting my wireless working?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by edco76 on 2010-10-13
I just upgraded to 10.10 and everything is great except my wireless doesnt work now. I am using a RaLink RT2860 on an AMD 64 Gateway Laptop. I have searched and it appears there are some known issues but to be honest all the solutions are going right over my head. 

iwconfig output

> [noparse]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/noparse]

Would really appreciate some help. Im wired now but I gotta go to work tomorrow and REALLY need my wireless.

---

### Post by macem29 on 2010-10-13
While I'm far from an expert I've been messing with my wireless too...have you tried looking to see if
there's a restricted driver available for you? system/amin/Hardware Drivers...anything listed? you may have to activate it if so

there's a buttload  of wifi threads on the go here, many get ignored, many dealing with the same issue I guess, so I suppose that's why...good luck and keep reading

---

### Post by edco76 on 2010-10-13
> **macem29 said:**
> While I'm far from an expert I've been messing with my wireless too...have you tried looking to see if
there's a restricted driver available for you? system/amin/Hardware Drivers...anything listed? you may have to activate it if so

there's a buttload  of wifi threads on the go here, many get ignored, many dealing with the same issue I guess, so I suppose that's why...good luck and keep reading
Thanks. No luck with the driver tho.

---

### Post by macem29 on 2010-10-13
terminal this and post the output: lspci

maybe someone smarter than me will check in to help, this will identify the hardware

---

### Post by edco76 on 2010-10-13
> **macem29 said:**
> terminal this and post the output: lspci

maybe someone smarter than me will check in to help, this will identify the hardware
```
cook@cook-M-2623U:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Gateway 2000 Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
03:00.0 Network controller: RaLink RT2860
06:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
06:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
cook@cook-M-2623U:~$ 

```

---

### Post by cap10Ibraim on 2010-10-13
when you boot your computer try the older kernel from grub menu

---

### Post by Hippytaff on 2010-10-13
There is a known issue with RaLink RT2860 driver - there isn't a linux one...you need to look into using Ndiswrapper to use the windows driver.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by edco76 on 2010-10-13
> **Hippytaff said:**
> There is a known issue with RaLink RT2860 driver - there isn't a linux one...you need to look into using Ndiswrapper to use the windows driver.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Cool. I installed the Ndiswrapper through the Ubuntu Software Center. So now I just DL the windows driver for the RaLink RT2860 and install it using Ndiswrapper, right?

---

### Post by Hippytaff on 2010-10-13
Thats the theory...you might need to blacklist some drivers if they start to conflict. Try this forst though and then we'll take it from there.

---

### Post by edco76 on 2010-10-13
OK. Downloaded the windows driver from RaLinks site. Got this message on install

> Not a valid driver .inf file.

---

### Post by Hippytaff on 2010-10-13
You installed it with Ndiswrapper?

---

### Post by edco76 on 2010-10-13
> **Hippytaff said:**
> You installed it with Ndiswrapper?
Tried to. Installed this file

IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe

Got an error message

"Not a valid driver .inf file."

After reading a little bit it looks like you cant just use the Windows Driver. You have to have an "extracted" Ndiswrapper driver. Which I cant find. Found some torrents but they dont have any seeds.

---

### Post by Hippytaff on 2010-10-13
Might be worth using the ndiswrapper gui - ndisgtk
 
sudo apt-get ndsigtk
 
then point that at the driver.

---

### Post by Hippytaff on 2010-10-13
you have to right click on the .exe and select "Extract Here" then there should be a bunch of files, then find the .inf file. Then from there you can install the ndiswrapper

---

### Post by macem29 on 2010-10-13
> **edco76 said:**
> Tried to. Installed this file

IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe

Got an error message

"Not a valid driver .inf file."

After reading a little bit it looks like you cant just use the Windows Driver. You have to have an "extracted" Ndiswrapper driver. Which I cant find. Found some torrents but they dont have any seeds.

that .exe sounds like a windows installer for the driver, the driver itself will have .inf extension

---

### Post by Hippytaff on 2010-10-13
> **Hippytaff said:**
> you have to right click on the .exe and select "Extract Here" then there should be a bunch of files, then find the .inf file. Then from there you can install the ndiswrapper
 
see above

---

### Post by edco76 on 2010-10-13
k. well I somehow crashed everything lol. Re-installed Ubuntu and starting over. DLing the windows driver now.

---

### Post by edco76 on 2010-10-13
When I try to extract the driver I get this

Archive:  /home/cook/Downloads/IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe
[/home/cook/Downloads/IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/cook/Downloads/IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe or
          /home/cook/Downloads/IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe.zip, and cannot find /home/cook/Downloads/IS_AP_STA_RT2860_D-3.1.8.0_VA-3.1.8.0_W7-3.1.8.0_RU-4.0.1.0_AU-4.0.1.0_072910_1.5.9.0WP_Free.exe.ZIP, period.

---

### Post by edco76 on 2010-10-13
Also looks like RaLink has Linux Drivers

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I just dont know how to install them.

---

### Post by cariboo on 2010-10-13
> **edco76 said:**
> I just upgraded to 10.10 and everything is great except my wireless doesnt work now. I am using a RaLink RT2860 on an AMD 64 Gateway Laptop. I have searched and it appears there are some known issues but to be honest all the solutions are going right over my head. 

iwconfig output



Would really appreciate some help. Im wired now but I gotta go to work tomorrow and REALLY need my wireless.

It look like your wireless device is working, have you tried associating it with your router/ap using the following command?

```
sudo iwconfig wlan0 essid "<routeressid>"
```

for example in my case the command would look like this

```
sudo iwconfig wlan0 essid "bad things can happen"
```

---

### Post by edco76 on 2010-10-13
> **cariboo907 said:**
> It look like your wireless device is working, have you tried associating it with your router/ap using the following command?

```
sudo iwconfig wlan0 essid "<routeressid>"
```for example in my case the command would look like this

```
sudo iwconfig wlan0 essid "bad things can happen"
```
I dont know my "routeressid"

---

### Post by edco76 on 2010-10-13
Dont know if this helps or not but I got this to.

```
cook@cook-M-2623U:~$ sudo lshw -C network
[sudo] password for cook: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:e0:b8:e9:dd:78
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:f0400000-f0403fff ioport:a000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:17:c4:2f:09:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0300000-f030ffff
cook@cook-M-2623U:~$ 



```

---

### Post by Hippytaff on 2010-10-13
Looks like your wireless might be disabled?

---

### Post by edco76 on 2010-10-13
> **Hippytaff said:**
> Looks like your wireless might be disabled?
Yeah. How do I enable it?

My switch and light are both on and when I right click my network icon, enable wireless is checked.

---

### Post by edco76 on 2010-10-13
Man. This really sux. I have to have wireless at work tomorrow. I got like 2 hours to get this fixed or I guess I will be buying a Windows disk. Cant believe they screwed something like this up. It worked just fine in Lucid. Never had any problems.

---

### Post by cap10Ibraim on 2010-10-13
did you try to boot your older kernel ?

---

### Post by edco76 on 2010-10-13
Fixed

Dunno how but this worked

[http://ubuntuforums.org/showthread.php?t=1547195](http://ubuntuforums.org/showthread.php?t=1547195)

Just changed the commands to rt2860sta instead of 2870. Rebooted and works fine.

---

### Post by AndyM3 on 2010-10-13
> **edco76 said:**
> Fixed

Dunno how but this worked

[http://ubuntuforums.org/showthread.php?t=1547195](http://ubuntuforums.org/showthread.php?t=1547195)

Just changed the commands to rt2869sta instead of 2870. Rebooted and works fine.

You might want to mark the thread as solved, so others that have the same problem can easily see that you found a solution. ;) It's under "thread tools".

---

### Post by edco76 on 2010-10-13
> **AndyM3 said:**
> You might want to mark the thread as solved, so others that have the same problem can easily see that you found a solution. ;) It's under "thread tools".
Done!

---

### Post by Hippytaff on 2010-10-13
Excellent... Happy days!

---

