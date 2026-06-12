---
title: "MacBookPro11-1/Saucy (dual boot OS X) can't fix wifi"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by opageo on 2014-03-18
Hi All,

I have a late 2013 MacBook Pro 13" with Retina and I've been working on having it dual boot Ubuntu (and Mavericks). I started with 12.04 but couldn't get wifi working so I have deleted the Ubuntu partitions and started again, following this guide: 
[https://help.ubuntu.com/community/MacBookPro11-1/Saucy#wireless](https://help.ubuntu.com/community/MacBookPro11-1/Saucy#wireless)
Note: created bootable USB with Unetbootin and [64-bit Mac (AMD64) desktop image]("http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64+mac.iso") (non Mac) (not using rEFit or rEFInd)
When attempting to apply the wifi fix I get the following problem:

opageo@MacBookProII:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for opageo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source

Hardware info:
opageo@MacBookProII:~$ sudo lshw -C network
[sudo] password for opageo: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0600000-b0607fff memory:b0400000-b05fffff

02:00.0 Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570]
    Subsystem: Broadcom Corporation Device [14e4:1570]
    Flags: bus master, fast devsel, latency 0
    Memory at b0900000 (64-bit, non-prefetchable) [size=64K]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Memory at b0800000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>


03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0112]
    Flags: fast devsel
    Memory at b0600000 (64-bit, non-prefetchable) [disabled] [size=32K]
    Memory at b0400000 (64-bit, non-prefetchable) [disabled] [size=2M]
    Capabilities: <access denied>

I am new to ubuntu and terminal (been working on this problem for about a week now). Thanks in advance for any assistance

---

### Post by chili555 on 2014-03-18
Which Ubuntu version did you install?```
lsb_release -d
```Did you build a package index first?```
sudp apt-get update 
sudo apt-get upgrade
sudo apt-get install bcmwl-kernel-source
```Please see: [https://wikidevi.com/wiki/ASUS_PCE-AC66](https://wikidevi.com/wiki/ASUS_PCE-AC66)> 

ID: 14e4:43a0 (2 addl. devices)
Windows: PCI\VEN_14E4&DEV_43A0
...and:> should work with Broadcom's latest wl driver

---

### Post by opageo on 2014-03-18
Thanks for the quick response

opageo@MacBookProII:~$ lsb_release -d
Description:	Ubuntu 13.10
opageo@MacBookProII:~$ sudo apt-get update
[sudo] password for opageo: 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                              
  Could not resolve 'extras.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy InRelease                            
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                     
  
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates InRelease                    
  
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-backports InRelease
  
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy Release.gpg
  Could not resolve 'au.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates Release.gpg
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-backports Release.gpg
  Could not resolve 'au.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease)  


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease)  


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/saucy-security/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease](http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg)  Could not resolve 'extras.ubuntu.com'


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.
opageo@MacBookProII:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
opageo@MacBookProII:~$ sudo apt-get install bcml-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcml-kernel-source
opageo@MacBookProII:~$

---

### Post by opageo on 2014-03-18
Reviewing wikidevi... now

---

### Post by chili555 on 2014-03-18
May I assume you are connected to the internet with a temporary wired ethernet connection?

---

### Post by opageo on 2014-03-18
No, I'm afraid not. I am accessing the internet via another MacBook with working wifi. The MacBook Pro I'm installing Ubuntu on does not have an ethernet port so I transfer files via USB

---

### Post by chili555 on 2014-03-18
Do you still have the install USB? Insert it and drill down to pool > restricted > b > bcmwl and drag bcmwl-kernel-source to your desktop. Do the same with pool > main > d >dkms and drag dkms to you desktop. Then install:```
cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb
```Without an internet connection, apt-get is useless.

Off for the evening; I'll check in tomorrow.

---

### Post by opageo on 2014-03-18
Ok, so I followed wikidev... and subsequent links to here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and downloaded the 64bit driver. Opened the zip and immediately felt way out of my depth. I'm guessing I run the code in the makefile? but I've never done this so will go away and research for a bit.

---

### Post by chili555 on 2014-03-18
> **opageo said:**
> Ok, so I followed wikidev... and subsequent links to here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and downloaded the 64bit driver. Opened the zip and immediately felt way out of my depth. I'm guessing I run the code in the makefile? but I've never done this so will go away and research for a bit.Noooo! Just read and follow post #7 above.

---

### Post by opageo on 2014-03-18
> **chili555 said:**
> Do you still have the install USB? Insert it and drill down to pool > restricted > b > bcmwl and drag bcmwl-kernel-source to your desktop. Do the same with pool > main > d >dkms and drag dkms to you desktop. Then install:```
cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb
```Without an internet connection, apt-get is useless.

Off for the evening; I'll check in tomorrow.

Thanks Chili555, that worked. Can now see wireless networks and have connected. Let me know if you need any outputs posted.

---

### Post by chili555 on 2014-03-19
Awesome! Glad it's working. I would appreciate one other data point. > Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [[COLOR="#FF0000"]14e4:43a0[/COLOR]] (rev 03)This is a relatively new device and the searchers will appreciate just a bit more information concerning the driver version needed to get it working. Please run and post:```
sudo dpkg -s bcmwl-kernel-source | grep Version
```Searchers, please note that an earlier version of the driver than opageo reports may not drive this device.

For comparison, my 13.10 installation includes 6.30.223.141+bdcom-0ubuntu1.

---

### Post by SudoOni on 2014-11-19
<snip>

---

### Post by chili555 on 2014-11-19
> **SudoOni said:**
> <snip>This is a complicated and slightly dangerous way to go about the process. First, with a temporary internet connection, ethernet or similar, help your system find the package first:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```If you have no internet connectivity, simply drag and drop the pool>main>d>dkms>dkms_whatever.deb to your own desktop; no need to mess with /root and suffer any unintended consequences of /root no longer being owned by root! 

Do the same with restricted>bcmwl>bcmwl-kernel-source_whatever.deb. 

Then open a terminal and install both:```
sudo dpkg -i ~/Desktop/*.deb
```

---

### Post by coffeecat on 2014-11-19
@chili555, thanks for taking the trouble to help the person who posted what is a questionable procedure. I've edited both yours and the quoted post.

@SudoOni, Welcome to the forum. Please do not take it personally when you see that the entirety of your first post here has been removed. We have to think of the many others, including newcomers to Ubuntu and Linux, who browse threads here looking for information, and who could irretrievably damage their systems if they followed your procedure. Please take note of chili555's excellent and knowledgeable advice.

---

