---
title: "Problems when configuring wireless usb divice! please help!"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by -Stevey-Wonder-1990- on 2007-11-03
hi, i was following this howto

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

to try and set up my dlink usb adapter

however during setup i started to recieve error messages something like segmentation or something

them the computer froze and crashed at about set 12

i really dont know what to do? do i start from the start again or from as certain stage.  i tried to start at step 12 but this is what i recieve.

steven@steven-desktop:~$ sudo modprobe -v rt73
steven@steven-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

steven@steven-desktop:~$ sudo ifconfig wlan0 up
steven@steven-desktop:~$ sudo iwconfig wlan0 essid 2WIRE064
steven@steven-desktop:~$ sudo iwconfig wlan0 key **********
steven@steven-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:9a:00:ce:83
Sending on   LPF/wlan0/00:17:9a:00:ce:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
steven@steven-desktop:~$ sudo ifconfig wlan0 up
steven@steven-desktop:~$ sudo iwconfig wlan0 essid 2WIRE064
steven@steven-desktop:~$ sudo iwconfig wlan0 key 5019751438
steven@steven-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5415
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:9a:00:ce:83
Sending on   LPF/wlan0/00:17:9a:00:ce:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Please can you help

(as the computer froze and crashed i couldnt get a screenshot etc of my error messages)

---

### Post by -Stevey-Wonder-1990- on 2007-11-03
fogot to mention im using gusty 7.10 and a dlink dwl-g122 (i think) wirless usb adaptor

---

### Post by diepruis on 2007-11-04
> **-Stevey-Wonder-1990- said:**
> fogot to mention im using gusty 7.10 and a dlink dwl-g122 (i think) wirless usb adaptor

Did you properly blacklist all the drivers in the guide? What does your /etc/modprobe.d/blacklist file look like?

---

### Post by -Stevey-Wonder-1990- on 2007-11-04
ok, i will look that up.  I cant at the moment but as soon as i can i will copy and paste it here for you.  I also ran through the whole process again, and i have a full set of the output from the terminal which i will load up for you to have a look through (if its not much bother).  As a total newbie to linux and only 16 i really dont know what some of the output means.  If there are any specific problem parts that i noticed i will put them in here.

---

### Post by -Stevey-Wonder-1990- on 2007-11-04
ok heres the total output of my second run through (as attachment).

For some strange reason when i type in etc/modprobe.d/blacklist it says

no such file or directory.

---

### Post by -Stevey-Wonder-1990- on 2007-11-04
some code from the terminal which looks dodgy:

```
steven@steven-desktop:/usr/src$ sudo apt-cdrom add 
Using CD-ROM mount point /cdrom/ 
Unmounting CD-ROM 
Waiting for disc... 
Please insert a Disc in the drive and press enter 
Mounting CD-ROM... 
Identifying.. [b23710d0071ddbf904b10cfe355c13af-2] 
Scanning disc for index files.. 
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures 
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' 
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 00:53:09 BST using DSA key ID FBB75451 
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" 
Reading Package Indexes... Done 
Writing new source list 
Source list entries for this disc are: 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted 
Unmounting CD-ROM... 
Repeat this process for the rest of the CDs in your set. 
steven@steven-desktop:/usr/src$ sudo aptitude update 
Err http://security.ubuntu.com gutsy-security Release.gpg 
  Could not resolve ‘security.ubuntu.com’ 
Err http://security.ubuntu.com gutsy-security/universe Translation-en_GB 
  Could not resolve ‘security.ubuntu.com’ 
Err http://security.ubuntu.com gutsy-security/main Translation-en_GB 
  Could not resolve ‘security.ubuntu.com’ 
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_GB 
  Could not resolve ‘security.ubuntu.com’ 
Ign http://security.ubuntu.com gutsy-security Release 
Err http://gb.archive.ubuntu.com gutsy Release.gpg 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy/main Translation-en_GB 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy/universe Translation-en_GB 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates Release.gpg 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/universe Translation-en_GB 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/main Translation-en_GB 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/restricted Translation-en_GB 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Ign http://gb.archive.ubuntu.com gutsy Release 
Ign http://gb.archive.ubuntu.com gutsy-updates Release 
Ign http://gb.archive.ubuntu.com gutsy/main Packages 
Ign http://gb.archive.ubuntu.com gutsy/universe Packages 
Ign http://gb.archive.ubuntu.com gutsy-updates/universe Packages 
Ign http://gb.archive.ubuntu.com gutsy-updates/main Packages 
Ign http://gb.archive.ubuntu.com gutsy-updates/restricted Packages 
Err http://gb.archive.ubuntu.com gutsy/main Packages 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy/universe Packages 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/universe Packages 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/main Packages 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Err http://gb.archive.ubuntu.com gutsy-updates/restricted Packages 
  Could not resolve ‘gb.archive.ubuntu.com’ 
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB 
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB 
Ign http://security.ubuntu.com gutsy-security/universe Packages 
Ign http://security.ubuntu.com gutsy-security/main Packages 
Ign http://security.ubuntu.com gutsy-security/restricted Packages 
Err http://security.ubuntu.com gutsy-security/universe Packages 
  Could not resolve ‘security.ubuntu.com’ 
Err http://security.ubuntu.com gutsy-security/main Packages 
  Could not resolve ‘security.ubuntu.com’ 
Err http://security.ubuntu.com gutsy-security/restricted Packages 
  Could not resolve ‘security.ubuntu.com’ 
Reading package lists... Done 
steven@steven-desktop:/usr/src$ sudo aptitude install build-essential linux-headers- 'uname -r' 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initialising package states... Done 
Building tag database... Done      
Couldn't find any package whose name or description matched "uname -r" 

```

what i get:
```
Listening on LPF/wlan0/00:17:9a:00:ce:83 
Sending on   LPF/wlan0/00:17:9a:00:ce:83 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

---

### Post by diepruis on 2007-11-06
I'm sorry for the late reply, writing exams at the moment :( 

Your problem indeed lies in that stretch of output:

> **-Stevey-Wonder-1990- said:**
> some code from the terminal which looks dodgy:

<Snip - everything up to here is fine.>

> **-Stevey-Wonder-1990- said:**
> ```
steven@steven-desktop:/usr/src$ sudo aptitude install build-essential linux-headers- 'uname -r' 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initialising package states... Done 
Building tag database... Done      
Couldn't find any package whose name or description matched "uname -r" 

```


What you did wrong here is mistype the "linux-headers- 'uname -r'" part, it should look like this:

```

linux-headers-`uname -r`

```

Note that there was a space after "headers-" and that you typed single quotes instead of backticks around "uname -r". This caught me out a few times as well when I started learning the terminal. You can find the backtick under the tilde on most keyboards, to the left of "1".

You also made a mistake here:

> **-Stevey-Wonder-1990- said:**
> 
```

steven@steven-desktop:/usr/src$ cd usr/src/rt73-cvs-2007110307/Module 

```


You forgot the starting "/" before usr. After this, everything will give you and error as you're in the wrong directory. Fix those two errors and please try again, and post here as soon as you see an error output from the terminal.

Good luck :)

---

### Post by -Stevey-Wonder-1990- on 2007-11-07
well i went through it again and here's what i got:

```
steven@steven-desktop:/usr/src/rt73-cvs-2007110307/Module$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6075
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:9a:00:ce:83
Sending on   LPF/wlan0/00:17:9a:00:ce:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

any ideas?

---

### Post by diepruis on 2007-11-08
> **-Stevey-Wonder-1990- said:**
> any ideas?


Not really... what does

```

iwlist wlan0 scan

```

report?

---

### Post by seul on 2007-11-09
Stevey, I answered you [here]("http://ubuntuforums.org/showthread.php?t=604690") Hope it works for you, too.

---

