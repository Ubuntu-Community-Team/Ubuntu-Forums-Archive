---
title: "Just installed Ubuntu, how do I connect to the internet?"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Felliph3 on 2008-05-17
I tried going into Network under system and entered the network name but nothing. Back when i was trying to install it and was running on the LiveCD, my wireless driver would be under propietary drivers and i clicked "enable" and it said i needed to restart. But as a liveCD, it doesn't save anything. I think i need to install the "B43" driver for my Broadcom driver. However that icon on the taskbar doesnt pop up now that Linux is installed. Any help?

---

### Post by localzuk on 2008-05-17
Restricted drivers are available under System -> Administration -> Hardware Drivers. Does the B43 driver appear in there?

---

### Post by Felliph3 on 2008-05-17
It did when I was running the LiveCD but now that its installed, nothing shows up in there.

---

### Post by fmartinez on 2008-05-17
> **Felliph3 said:**
> It did when I was running the LiveCD but now that its installed, nothing shows up in there.

In the terminal type 
$dmesg

and see if your card recognized on start up. 
Also check 
$ifconfig -a 
this will show your network devices. 
You also might want to post the specs of your system to get a better understanding of what we're working with.

---

### Post by Felliph3 on 2008-05-17
ok i will try that now. The pc is an Acer Aspire 5000 series with AMD Turion 64 bit,running windows XP SP2 1.60 Ghz and 896MB of ram and I have Ubuntu. It is a laptop too btw. Thanks for the help.

---

### Post by Felliph3 on 2008-05-17
This is what I got:

felliph3@Laptop:~$ mesg
is y
felliph3@Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:bf:f0:01  
          inet addr:192.163.0.1  Bcast:192.163.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73100 (71.3 KB)  TX bytes:73100 (71.3 KB)

felliph3@Laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:bf:f0:01  
          inet addr:192.163.0.1  Bcast:192.163.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73100 (71.3 KB)  TX bytes:73100 (71.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:24:fd:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-24-FD-74-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Im not sure how to read all that even though I do understand some parts of it and from what I can see the ethernet port is working but the wireless is on loopback? Any help would be appreciated.

---

### Post by Ayuthia on 2008-05-17
Let's confirm your wireless card.  Can you post the results of lspci -nn from the Terminal?

---

### Post by Felliph3 on 2008-05-17
Here:

felliph3@Laptop:~$ lspci -nm
00:00.0 "0600" "1039" "0760" -r03 "" ""
00:01.0 "0604" "1039" "0002" "" ""
00:02.0 "0601" "1039" "0963" -r25 "" ""
00:02.1 "0c05" "1039" "0016" "" ""
00:02.5 "0101" "1039" "5513" -p80 "1025" "0083"
00:02.6 "0703" "1039" "7013" -ra0 "1025" "0083"
00:02.7 "0401" "1039" "7012" -ra0 "1025" "0083"
00:03.0 "0c03" "1039" "7001" -r0f -p10 "1025" "0083"
00:03.1 "0c03" "1039" "7001" -r0f -p10 "1025" "0083"
00:03.2 "0c03" "1039" "7002" -p20 "1025" "0083"
00:04.0 "0200" "1039" "0900" -r91 "1025" "0083"
00:06.0 "0607" "104c" "ac50" -r02 "1025" "0083"
00:0b.0 "0280" "14e4" "4318" -r02 "1468" "0312"
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
01:00.0 "0300" "1039" "6330" "1025" "0083"

---

### Post by Ayuthia on 2008-05-17
I am sure that some might be confused with your results. :)  You mistyped a character (you typed lspci -nm instead of lspci -nn).

Anyway, this is your wireless card:
00:0b.0 "0280" "14e4" "4318" -r02 "1468" "0312"

It is a Broadcom 4318 rev 02.  I have not seen too many people that have been too successful in using the b43 driver in Ubuntu Hardy, but you can try to install it.  You can try this [link]("http://ubuntuforums.org/showthread.php?t=779754").  It provides instructions on you to install the b43 driver, but if you want to go the NDISwrapper route (the other way to get your card to work) there is a link to a guide that has helped a lot of people.

---

### Post by Felliph3 on 2008-05-17
Yea man, i already been to that link haha. Im still working on it. However i have tried this that i learned from your link
A friend of mine suggested id try sudo apt-get so i did but it didnt work.

felliph3@Laptop:~$ sudo apt-get install b43 -fwcutter
E: Command line option 'w' [from -fwcutter] is not known.

felliph3@Laptop:~$ sudo aptitude install b43 -fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "b43"
Couldn't find any package whose name or description matched "b43"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
felliph3@Laptop:~$

---

### Post by Felliph3 on 2008-05-17
oh and i know that there is a space after b43 but it didnt change the results, i tried that too and got the same results

---

### Post by Ayuthia on 2008-05-17
> **Felliph3 said:**
> oh and i know that there is a space after b43 but it didnt change the results, i tried that too and got the same resultsHave you added your CD to the repositories:
```
sudo apt-cdrom add
sudo apt-get update
```

---

### Post by Felliph3 on 2008-05-17
Heres pretty much all the commands:

felliph3@Laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
felliph3@Laptop:~$ sudo apt-cdrom add
[sudo] password for felliph3: 
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [6c2e1c01c6884ef40fd349693334a953-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)'
Copying package lists...gpgv: Signature made Tue 22 Apr 2008 09:03:24 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
felliph3@Laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                           
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US          
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US            
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US          
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                   
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US        
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US  
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US    
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US  
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                    
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US         
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US   
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US     
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US   
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done                                                
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
felliph3@Laptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.8kB of archives.
After this operation, 102kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 95678 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--09:51:23--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
felliph3@Laptop:~$ sudo -cdrom add
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
felliph3@Laptop:~$ sudo aptitude update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Reading package lists... Done
felliph3@Laptop:~$ sudo aptitude install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up b43-fwcutter (1:011-1) ...
--09:52:40--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-1) ...
--09:52:41--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
felliph3@Laptop:~$

---

### Post by Ayuthia on 2008-05-17
According to your post, you don't have an internet connection.  However, you now have the firmware cutter installed.  You will need to find someplace where you can download the firmware.  The firmware that you need are:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Once you have them downloaded, you will need to copy those files into your home directory.  Once that is done, you will need to open up the Terminal and do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

---

### Post by Felliph3 on 2008-05-18
Well Ayuthia, all i can say is THANKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:guitar:


You rock dude! I got it to work!Im online on linux now!!. Basically the broadcom winrar file that you sent me the link was corrupt, i downloaded only to later find out the file was corrupted. SO i googled it and downloaded it from somewhere else. Then i dropped em both under home/felliph3 and i entered the lines that you said and everything extracted fine and on the network icon i clicked enable roaming mode and boom! It showed me the available networks.

THanks a lot bro, if you ever come across anyone that needs this B43 driver and has no connection, tell them to download and save the files on a hardrive on the pc, go on linux and transfer those files to home/user and run those lines! 


YOuve been a great help, i mean it, thanks a bunch!

---

### Post by Felliph3 on 2008-05-18
Idk what happened but its not working now? I was online yesterday and i think my network went down for 3 secs(it does this every few hours) and i couldnt connect again, the networks werent showin up, it was just like it was before. i unisntalled the fles and installed em back and still nothing. Is it supposed to be on roaming mode? Also how do I turn my wireless adapter on or off?What shortcut key? Before I would just press the button that it has in front of the pc

---

### Post by Felliph3 on 2008-05-18
weird, its working now, it wasnt 1 hour ago. It will probably come back though.

---

### Post by Syndacate on 2008-08-22
> **Ayuthia said:**
> According to your post, you don't have an internet connection.  However, you now have the firmware cutter installed.  You will need to find someplace where you can download the firmware.  The firmware that you need are:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Once you have them downloaded, you will need to copy those files into your home directory.  Once that is done, you will need to open up the Terminal and do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

He doesn't have fwcutter installed.

It doesn't come by default, and he doesn't have internet on his.

He also just confirmed it for me on AIM that b43-fwcutter isn't installed (or if it is the path variable isn't set to its location).  He doesn't have fwcutter installed.  I'll look for the deb file for it.

EDIT:  PS:  if you read his terminal output again, there was an error installing it (probably because he wasn't connected to the internet and there's no other local repos for him to install off of).

EDIT2:  I just downloaded the b43-fwcutter via synaptic and then pulled the .deb file out of my comp - put it up on my server for him to download.  Now he'll try installing that, then executing the commands you told him to.

EDIT3:  It failed, I thought the data was supposed to be in the .deb archive, but it tried downloading it.  The deb standard contains a control archive and a data archive.  Though I guess not all of them?  Never really questioned how they work, usually either compile from source or use aptitude...

---

### Post by Syndacate on 2008-08-22
I give up.  The actual OS he was using was gOS, but it should work very similar to Ubuntu since it was heavily based off of it.

gOS is too "finished" - there's no global c library (glibc), there's no "make" installed - and if you don't have internet, trying to compile this all from source can be a big pain in the ***.

Guess it still has a far way to go...

---

