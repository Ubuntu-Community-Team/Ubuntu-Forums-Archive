---
title: "Wireless Help WiMax 6050"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by halozander on 2011-01-26
Hi, I have been trying to get my wireless driver worked out for two days now. I am a new to Linux. Right now I am dual booting Win7 and Ubuntu 10.04. My chipset is an Intel WiMax 6050. I have tried everything I have read in documentation and forums, but so far no good. 

I have read that the drivers are included in the kernel, so I tried this
sudo apt-get install linux-backports-moudules-wireless-lucid-genericthat didn't work

I tried dl the driver separately here [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz)
and followed this 

sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn

that didn't work. 

Anyways, thanks for the help ahead of time. I really want to say goodbye to windows!

---

### Post by wep940 on 2011-01-26
> **halozander said:**
> Hi, I have been trying to get my wireless driver worked out for two days now. I am a new to Linux. Right now I am dual booting Win7 and Ubuntu 10.04. My chipset is an Intel WiMax 6050. I have tried everything I have read in documentation and forums, but so far no good. 
 
I have read that the drivers are included in the kernel, so I tried this
sudo apt-get install linux-backports-moudules-wireless-lucid-genericthat didn't work
 
I tried dl the driver separately here [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz)
and followed this 
 
sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
 
that didn't work. 
 
Anyways, thanks for the help ahead of time. I really want to say goodbye to windows!
 
After following the linux iwlwifi installation did you reboot?  I'm not sure how things work as far a firmware loading, but I would try a reboot - it might pick up the hardware and load the firmware.

---

### Post by halozander on 2011-01-26
Reboot doesn't work.
lshw -C network command output:

 *-network DISABLED      
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 5f
       serial: 00:23:15:63:20:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f4c00000-f4c01fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:fe:f0:7c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=138.67.79.155 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:32 memory:f3820000-f3823fff ioport:b000(size=256) memory:f3800000-f381ffff(prefetchable)


iwconfig command output:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by halozander on 2011-01-26
Eh I gave up. Burned 10.10 onto a disk and reinstalled with "third party software". Now the wireless works.
maybe this will help someone.

---

### Post by outskut on 2011-03-07
I got an external wireless adapter for my netbook that was running this wifi card, but with Ubuntu 10.04 I finally got it working by following the following thread:
[http://ubuntuforums.org/showthread.php?t=1645370](http://ubuntuforums.org/showthread.php?t=1645370)

The sequence of operations was:

From this site:
[http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)
Download the newest version of the 6050 Images - for Intel Centrino Advanced-N + WiMAX 6250 and Wireless-N + WiMax 6150
(alternate direct link: [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz))
Then browse to the downloads folder and expand iwlwifi-6050-ucode-41.28.5.1.tgz

Once that's done, in a terminal window execute the following commands in sequence:

cd ~/Downloads/iwlwifi-6050-ucode-41.28.5.1
sudo cp iwlwifi-6050-5.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
sudo modprobe iwlagn
sudo apt-get install linux-backports-modules-wireless-lucid-generic

That did if for me.  I just promised myself I'd update this thread when I figured it out.

---

### Post by NFAD on 2011-04-16
Thank you very much!!!

;)

---

