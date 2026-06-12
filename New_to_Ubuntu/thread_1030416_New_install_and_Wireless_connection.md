---
title: "New install and Wireless connection"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by durhamite on 2009-01-04
Hey all.  I am brand new to Linux and Ubuntu and did a fresh dual boot install on yesterday.  After it installed I was all set, connecting to the internet and browsing and life was great.  I did some updates in the update manager and now, I can't connect to the internet via wireless connection and I can't find network manager.  I am not sure if network manager was there to start with or not but is is not there now.  I have been surfing the web and found a few solutions but most were over my head.  Any help would be great.  I am also trying to figure out what this Beryl thing is about and how to install it.  I am using a Gatway laptop with built in wireless adapter.  I know the drivers are there and should work because it was working before I did the update.  If you have a solution, please make them as simple as possible.  I can navigate the gui but when it comes to the terminal and the file structure, I am a lost.

Thanks!

---

### Post by melojo on 2009-01-04
goto applications>accessories>terminal and enter these below and post the output

```


lspci
sudo lshw -C network
ifconfig

```

What version of ubuntu 8.04 or 8.10

This will give us more info.

---

### Post by durhamite on 2009-01-04
Ubuntu 8.10 with updates.

this is what i get when i run those commands.

brian@brian-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

brian@brian-laptop:~$ sudo -C network

sudo: illegal option `-C'

usage: sudo -h | -K | -k | -L | -l | -V | -v

usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]

            {-i | -s | <command>}

usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

brian@brian-laptop:~$

---

### Post by melojo on 2009-01-04
sorry the second command should be

sudo lshw -C network

---

### Post by durhamite on 2009-01-04
I though I saw an error in there. Now, I did this before and saw that wireless was disabled.  This raised a red flag with me but I didn't know how to enable it.  Here is the results.

brian@brian-laptop:~$ sudo lshw -C network
[sudo] password for brian: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:eb:99:ef
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:5f:27:63
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:20:0b:01:e0:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
brian@brian-laptop:~$

---

### Post by melojo on 2009-01-04
if you are using intrepid
open up a terminal again and type this

```


sudo apt-get install linux-backports-modules-intrepid-generic


```

reboot

---

### Post by durhamite on 2009-01-04
I am not sure what intrepid is.  I ran the command and it installed something.  But it looks like nothing happened. I am going to reboot now.

Shouldn't I be able to see the network manager somewhere?

---

### Post by melojo on 2009-01-04
intrepid in ubuntu 8.10

---

### Post by durhamite on 2009-01-04
yes, I am running intrepid 8.10.  I rebooted and still no network manager. No wireless connection. Do not pass go, do not collect 200 dollars.

when i ran that command, it looked like it was instlling something and it was successfull. (i closed be box before i cut and paste the info. sorry)

---

### Post by melojo on 2009-01-04
can you post the output of

```

ifconfig
iwlist scan


```

Also if you have another Ethernet that is plugged in it won't let your wireless work

---

### Post by durhamite on 2009-01-04
here you go.

brian@brian-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:eb:99:ef  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:feeb:99ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2718435 (2.7 MB)  TX bytes:399441 (399.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5f:27:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-5F-27-63-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

brian@brian-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by melojo on 2009-01-04
open a terminal again and type

lsmod 

Then look for a module that says

iwl3945

If no module type

sudo modprobe iwl3945

see if you have wireless

---

### Post by melojo on 2009-01-04
also restart the network

open a terminal and type

[/code]
sudo /etc/init.d/networking restart

[/code]

---

### Post by durhamite on 2009-01-04
the module wasn't there. added the command and restarted the network and the computer and now the mod is there. Still no wireless connection or network manager.  when i go to the network connection icon in the taskbar, i have two connections eth and lo.  I am connected with a cable right now.

---

### Post by melojo on 2009-01-04
Sorry I don't have any answer for you.  Some one else will have to chime in that had the same problem as you or maybe one of the seasoned individuals can help you.

---

### Post by durhamite on 2009-01-04
thanks for your help!

---

### Post by durhamite on 2009-01-04
I got it to work. Not sure why it is working now but it did.

i did Alt + F2, typed in nm-applet, i got a message saying that a keyring was not letting the application run and it needed permission, granted permission and now my wireless is working again.  I still don't have the network manager in the system---admin list and if I reboot, i have to do those steps again.  But for now, I am working. I hope this helps someone else because this was driving me crazy.

---

### Post by CoCoKnots on 2009-01-04
Hi Melojo,
I think I messed up here. Like Durhamite, I lost my wireless after the last update this weekend. I noticed we have the same Pro/Wireless 3945 ABG card & assumed the Terminal Command you offered would work for me as well... 
Code:

sudo apt-get install linux-backports-modules-intrepid-generic

I replaced the '-intrepid-' with '-hardy-' & rebooted my system. I now have no-mic & receive a "No volume control GStreamer plugins and/or devices found." when I try to open the volume control. How can I un-do the damage I've done?

---

### Post by melojo on 2009-01-04
sudo apt-get remove linux-backports-modules-hardy-generic

Then

sudo apt-get update

see what happens

---

### Post by melojo on 2009-01-04
> **durhamite said:**
> I got it to work. Not sure why it is working now but it did.

i did Alt + F2, typed in nm-applet, i got a message saying that a keyring was not letting the application run and it needed permission, granted permission and now my wireless is working again.  I still don't have the network manager in the system---admin list and if I reboot, i have to do those steps again.  But for now, I am working. I hope this helps someone else because this was driving me crazy.

You can add those commands to 
/etc/rc.local just above the exit line

should load at boot.

---

### Post by CoCoKnots on 2009-01-04
> **melojo said:**
> sudo apt-get remove linux-backports-modules-hardy-generic

Then

sudo apt-get update

see what happens

Afterwards I re-booted system... Nothing changed.

---

### Post by melojo on 2009-01-04
try

```


sudo apt-get autoremove


```

---

