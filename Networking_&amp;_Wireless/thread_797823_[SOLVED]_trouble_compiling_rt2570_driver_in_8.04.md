---
title: "[SOLVED] trouble compiling rt2570 driver in 8.04"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by ncumming on 2008-05-17
Hi -

I just did a fresh install of 8.04 on my machine and as expected my D-Link DWL-G122 Rev B1 is not working. I tried downloading and installing the latest rt2570 tarball from serialmonkey and i get the following error when i try to compile:

make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory. Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

I tried running apt-get install build-essential with the 8.04 alt install cd in my drive and i get:
E: Couldn't find package build-essential

I'm following the good info from these posts [http://ubuntuforums.org/showthread.php?t=739139](http://ubuntuforums.org/showthread.php?t=739139) and [http://ubuntuforums.org/showthread.php?t=778228&highlight=rt2570+hardy](http://ubuntuforums.org/showthread.php?t=778228&highlight=rt2570+hardy) 
...but don't seem to be getting very far.

Can anyone help?

---

### Post by chili555 on 2008-05-17
Before you tried to get *build-essential*, did you open up Synaptic and go to Settings -> Repositories and enable installing from the CD?

The first link you referred us to clearly says:> Since Ubuntu 7.10, stable drivers for rt2570 have been included with the release--in other words, you shouldn't need to do anything to get your device workingAs well, the 'latest' tarball is about two years old, or in Linux years, old enough to retire.

Finally, there is evidently a better rt2500 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```I suggest trying the built-in before compiling an antique.

---

### Post by ncumming on 2008-05-17
I did read that the rt2570 drivers are supposed to be included...but like in the referenced post the drivers don't seem to work for my adapter.  As a matter of fact, i get almost exactly the same results from running lsusb, iwconfig, ifconfig, and iwlist wlan0 scan as in the original post. I had a similar problem with 7.10, and the serial monkey driver worked for me then.


I enabled all of the repositories on the CD and re-ran install build-essential.  This time 9 packages were installed.  However, I get the same result trying to compile the rt2570 driver.


When I run 

sudo apt-get install linux-backports-modules-hardy-generic

I get 
E:  couldn't find package linux-backports-modules-hardy-generic


I should probably note that without the wireless adapter working i don't have a working internet connection on the machine - i'm posting from another laptop.

I should also note that synaptic is acting funny - after i finish configuring software sources and exit the package manager, synaptic seems to keep running in the background - it won't close.  I try opening it again and exiting and the window goes away but the status icon in the taskbar continues to say the package manager is running.

---

### Post by chili555 on 2008-05-18
Here is what I did to get a compilation without errors or warnings:```
wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
tar zxvf rt2570-cvs-daily.tar.gz
cd rt2570-cvs-2008051809/Module
sudo make
```Of course I had build-essential, kernel headers and kernel source previously installed. I did not continue on to *make install* since I do not have the device. Once you have this done, you should be able to:```
sudo modprobe rt2570
```and configure your device the usual way.

Please let us know.> I should also note that synaptic is acting funny - after i finish configuring software sources and exit the package manager, synaptic seems to keep running in the background - it won't close. I try opening it again and exiting and the window goes away but the status icon in the taskbar continues to say the package manager is running.It's looking for updates which it will never find until you are on line, which, hopefully, will be in just a few moments!

---

### Post by ncumming on 2008-05-18
Unfortunately I'm still having the same problem.  Maybe I don't have kernel source installed?  I'm not sure...  I went ahead and completely re-installed 8.04 and got through it with no errors to make absolutely sure that it wasn't my install that is causing the problems.  I'm posting below the terminal info from my session trying to get this thing working, along with the results of lsusb, iwconfig, ifconfig, and iwlist wlan0 scan.  I was just guessing on the commands for installing kernal source - it probably wasn't right since it obviously didn't work.  Kernel headers seems to be installed though.

Thanks for your help...this is my fourth complete re-install of 8.04 and going on my third week trying to get this to work and i'm at my wits end!


```
nick@officemachine:~$ sudo apt-get install build-essential
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8701kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 112543 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-16.30_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.2.3-1ubuntu3_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-16.30) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu3) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu3) ...
Setting up build-essential (11.3ubuntu1) ...

nick@officemachine:~$ sudo apt-get install linux-headers
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-16 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
nick@officemachine:~$ sudo apt-get install linux-headers-2.6.24-16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nick@officemachine:~$ sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-source
nick@officemachine:~$ cd ~/rt*
nick@officemachine:~/rt2570-cvs-2008051714$ cd Module
nick@officemachine:~/rt2570-cvs-2008051714/Module$ make
make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
nick@officemachine:~/rt2570-cvs-2008051714/Module$ lsusb
Bus 005 Device 004: ID 0951:1607 Kingston Technology 
Bus 005 Device 003: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 005 Device 002: ID 046d:08c9 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
nick@officemachine:~/rt2570-cvs-2008051714/Module$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Cummings Home Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:24:07:9A:8D   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=27/100  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nick@officemachine:~/rt2570-cvs-2008051714/Module$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108313 (105.7 KB)  TX bytes:108313 (105.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:eb:00:d0  
          inet addr:10.0.1.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:feeb:d0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5264 (5.1 KB)  TX bytes:7230 (7.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-95-EB-00-D0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nick@officemachine:~/rt2570-cvs-2008051714/Module$ iwlist wlan0 scan
wlan0     No scan results


```

---

### Post by chili555 on 2008-05-18
> I was just guessing on the commands for installing kernal source Try this one:```
sudo apt-get install linux-source
```Like build-essential, it will pull in whatever else is needed.> wlan0     Link encap:Ethernet  HWaddr 00:11:95:eb:00:d0  
          inet addr:10.0.1.5
          RX bytes:5264 (5.1 KB)  TX bytes:7230 (7.0 KB)
Well, you have an IP address and are connected. What kind of trouble are you having? The only thing I see that's a bit concerning is in iwconfig:> wlan0     IEEE 802.11g  ESSID:"Cummings Home Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:24:07:9A:8D   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality=27/100  Signal level=-76 dBmThe link quality is 27/100; which could be one of two things, you are quite a distance from the router or your module is not reporting correctly. Can you walk that machine right next to the router and run iwconfig again? Does the quality improve? 

I also notice it reports a bit-rate of 9 Mb/s, which is a bit unusual.  You might see if you can help it with:```
sudo iwconfig wlan0 rate auto
```

Can you increase the transmit power in your router?

---

### Post by ncumming on 2008-05-18
When i try to install kernel source I still get "E:  couldn't find package linux-source"  I double checked my sources.list file to make sure all of the cdrom repositories are active and it looks right.  In synaptic i've disabled all repositories except the cdrom sources (which are all active) to keep from getting errors since i have no internet connection.

As far as what kind of trouble I'm having... When I open network manager no networks appear even though there are several open networks broadcasting SSIDs in my area.  When I type in the SSID for my network and enter my WEP key, it seems to connect to the network but i can't send or receive anything.  The adapter itself has two lights - one that is always on when it has a "link" with the router and one that flashes as it is sending and receiving data.  The "link" light is on, as it should be, but the "data" light is not.  Occasionally - when i start network manager for instance, the light flashes once.

I am a little far from my router but close enough that there shouldn't be a problem - i get a very strong signal (~95%) on my macbook sitting right beside the machine i'm working on.  The machine i'm working on is a large desktop machine and moving it isn't a very attractive option unless absolutely necessary.

My router is an apple airport express, and i don't know of a way to boost the signal strength any further...when i originally configured it i set it at the maximum level.

Worth noting... Before i re-installed 8.04 i tried installing the windows driver for the adapter using ndiswrapper - which worked for me back when i was using dapper.  I got the same results when i did that though as i'm getting with the built-in driver.  

Another note...I do dual-boot the machine with XP, and the wireless adapter works fine in XP, so it doesn't seem to be a hardware problem.
:confused:

---

### Post by chili555 on 2008-05-18
I apologize in advance. You are dealing with an anti-Network Manager zealot.

Network Manager is very useful for selecting from among several networks, say at the coffee shop, university or library. Does this sound like the way you will use your computer? I don't think so. So, why, oh why is NM installed by default on desktop machines? I dunno.

I suggest you open System -> Administration -> Network and disable roaming, which relinquishes control of networking to you, where it belongs and not with NM.

Then *sudo gedit /etc/network/interfaces* to make it look like:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Cummings Home Network"
wireless-key <your_key>
```If your key is ascii (rare), precede it with **s:**. If your encryption method, in the router is Shared Key, follow the key with 'restricted.' Then restart networking:```
sudo /etc/init.d/networking restart
```Did you connect?

The linux-source is evidently not on the CD; you can get the version matching your running kernel at packages.ubuntu.com which seems to be down at the moment.

---

### Post by ncumming on 2008-05-18
> **chili555 said:**
> 
I suggest you open System -> Administration -> Network and disable roaming .

You know its funny you mention that, because i've always had to disable roaming mode in the past to get my connection to work.  However, in NM where the "enable roaming" checkbox used to be it says "Enable this connection"  I thought perhaps roaming mode was done away with in the 8.04 upgrade.  

Anyway I tried unchecking the box "enable this connection," then making the edits in the interface file and restarting networking.  Still no luck...  Here's the terminal info:
```
nick@officemachine:~/rt2570-cvs-2008051714/Module$ sudo gedit /etc/network/interfaces
nick@officemachine:~/rt2570-cvs-2008051714/Module$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                            
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:95:eb:00:d0
Sending on   LPF/wlan0/00:11:95:eb:00:d0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

and here's my interfaces file 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Cummings Home Network"
wireless-key s:<mykey>
```

---

### Post by chili555 on 2008-05-18
You are certain the key is ascii? Does it contain letters higher than f? Any symbols? If not, it may be hex, that is, no **s:** is needed. Valid key lengths are 5 (ASCII) and 10 (Hex) for 64-bit, 13 (ASCII) and 26 (Hex) for 128-bit WEP encryption.

---

### Post by ncumming on 2008-05-18
Yes, it's a 13 digit ascii code.  I set it myself using a combination of words and numbers that i would remember, instead of having to write it down.  For instance, it contains the letter "s"

---

### Post by chili555 on 2008-05-18
Excellent. Could you please try amending [I]/etc/network/interfaces
[/I] and add the word restricted:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Cummings Home Network"
wireless-key s:<mykey> **restricted**
```Then restart networking and see if you connect. If not, I'd like to see the las 10 lines of:```
dmesg | grep authenticat
```No ethernet connected, right?

---

### Post by ncumming on 2008-05-18
No change after adding *restricted*.  *dmesg | grep authenticat* did not produce any output to the terminal.  Does it go to a log file or something?  I also tried *dmesg | grep authenticate* in case authenticat was a typo, and tried both variants with sudo.  In all cases, i got no output...not even an error.

I have no ethernet connection on this machine right now, just the wireless (probably mistake #1 for a desktop).

---

### Post by chili555 on 2008-05-18
I was hoping for any verbage related to *authenticate, authenticated or authentication* like this from my machine:```
[  650.410821] eth1: RX authentication from 00:0c:41:19:58:77 (alg=1 transaction=2 status=0)
[  650.411928] eth1: RX authentication from 00:0c:41:19:58:77 (alg=1 transaction=4 status=0)
[  650.411934] eth1: authenticated
```Does:```
dmesg | grep wlan0
``` look interesting? No need to post hundreds of lines of text if it really doesn't look suspicious. Would you please try a reboot, just for insurance/grins/my neuroses? Then try to ping your router:```
ping -c3 10.0.1.1
```Is that your router?

---

### Post by ncumming on 2008-05-18
Here are the results of grep wlan0 and the ping...10.0.1.1 is my router, i also tried to ping one of my other machines just for kicks...no luck - noone wants to talk to my computer!


```
nick@officemachine:~$ dmesg | grep wlan0
[   57.154649] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  160.162231] ADDRCONF(NETDEV_UP): wlan0: link is not ready
nick@officemachine:~$ ping -c3 10.0.1.1
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
From 169.254.8.13 icmp_seq=1 Destination Host Unreachable
From 169.254.8.13 icmp_seq=2 Destination Host Unreachable
From 169.254.8.13 icmp_seq=3 Destination Host Unreachable

--- 10.0.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
nick@officemachine:~$ ping -c3 10.0.1.4
PING 10.0.1.4 (10.0.1.4) 56(84) bytes of data.
From 169.254.8.13 icmp_seq=1 Destination Host Unreachable
From 169.254.8.13 icmp_seq=2 Destination Host Unreachable
From 169.254.8.13 icmp_seq=3 Destination Host Unreachable

--- 10.0.1.4 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3

```

Went ahead and rebooted (again) just to make sure - i've actually been through several reboot cycles and booted over to windows to convince myself that there is nothing wrong with the adapter.  

One other funny thing i've noticed is that, when I had my adapter working with previous versions of ubuntu, the lights on the adapter would flash while the system was booting.  Now, the one light that does come on doesn't come on until I'm logged on and the system is up and running.

---

### Post by ncumming on 2008-05-18
...one other data point - i went ahead and loaded the network status applet into my task bar.  when i double click on the network icon, and click "configure" with wlan0 selected, I get an error saying "the interface does not exist"

---

### Post by acad1 on 2008-05-19
I have the same device and it is recognised as rausb0.
I am using Network Manager and also have Rutilt installed, annd have no problems connecting wirelessly with 8.04. I also installed the rt2570 driver. Just wondering if "sudo ifconfig rausb0 up" will help!

---

### Post by ncumming on 2008-05-19
thanks...I'll give that a try when i get home from work...i'll try anything at this point.  

As far as rutilt goes...would you recommend removing network manager or keeping them both?  Presumably i can install rutilt without an internet connection on the machine?

---

### Post by acad1 on 2008-05-19
You will be able to download the rutilt file, save it, and then add it to your desktop, and then install it from there. I don't have the link at the moment, but will get back to you with it in about an hour from now. I have both NWM and Rutilt installed and working side by side. I did not have to set up anything in Rutilt after installation, but it does give information on the wireless connection - signal strength etc. Hope you wwill be able to get the device working soon!

[http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/r/rutilt/rutilt_0.15-0ubuntu5_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/r/rutilt/rutilt_0.15-0ubuntu5_i386.deb)

If you can save the file which you can download from this link,by usb stick, and then install it onto the Desktop of the Ubuntu machine, and then double-click it to install it.

---

### Post by ncumming on 2008-05-19
no luck with the rausb command - get a "no such device" error, but then again i don't have the rt2570 driver installed because i can't compile it.

---

### Post by acad1 on 2008-05-20
[http://ubuntuforums.org/showthread.php?t=739139](http://ubuntuforums.org/showthread.php?t=739139) Post#8

May I suggest that you try to install the rt2570 driver using the method shown in the above post, but use the "rt2570-cvs-daily.tar.gz" and not the link shown on Post#8.
This method certainly worked for me. Were you able to install "build-essential" OK?

---

### Post by ncumming on 2008-05-20
That was the original how-to that i had been following (referenced in the first post).  Very helpful and worked for me when running 7.10 but would not compile in 8.04.  

Anyway i think i may have found the problem.  I had installed 8.04 with the alternate install CD.  Last night i downloaded the live CD, reinstalled 8.04 using the live CD, and it now the adapter is working sporatically without even loading the rt2570 driver.  I noticed that the system seems to be using an rt2500 driver, thus it works a little but not as well as i think it would if it was using the rt2570 driver.  So i'm going to try installing the rt2570 driver tonight and see if it works.  I'm guessing that there were "issues" with the alternate install CD - even though the error check showed no issues...somehow the version of Ubuntu that gets installed using the alternate install disk is different than what gets installed with the live CD...i'm thinking that's what led to my errors compiling the driver as well.

How frustrating is that?  After all of this pulling my hair out it turns out that there was nothing wrong with what i was doing...the distribution was just broken.:confused:

---

### Post by acad1 on 2008-05-20
Great! I hope that you have solved the problem and the re-install from the live CD works. Please let us know the results.Good Luck!

---

### Post by ncumming on 2008-05-20
Success!!!

---

### Post by acad1 on 2008-05-21
I am pleased that you were able to get up and running in the end, after the new install.
Thanks should go to pytheas22 who guided me through the installation initially.

---

### Post by VitalBodies on 2008-05-23
So is this to say the 64-bit desktop edition will not work with the wUSB56gv4 that uses the ra2570 driver? 

I have been trying for days to get this work with no luck. I bought this wireless wlan because I read it works well with Linux.

---

### Post by ncumming on 2008-05-23
not sure... i have 32 bit system.  I haven't tried the driver in a 64 bit architecture.

the root cause of the problem ended up being the real time kernel installed as part of the ubuntu studio package.

---

### Post by VitalBodies on 2008-05-23
> **ncumming said:**
> not sure... i have 32 bit system.  I haven't tried the driver in a 64 bit architecture.

the root cause of the problem ended up being the real time kernel installed as part of the ubuntu studio package.

I have really liked Ubuntu software wise but this has been grueling hardware wise. From trying to use the Atheros wlan to and ATI X1650 now to this ra2570 driver. I am not sure I uderstand fully what you are saying but should I be questioning the fact I am using UbuntuStudio? Like would this be resolved if I switch to Ubuntu? Is that what you did?

I just downloaded and burned both the Ubuntu server and desktop edition. Will be interesting to see if this helps with hardware...
EDIT: I tried the live CD and could install the driver. I did not get it to work but that might be because I could not reboot....
So what steps did you use once you had a clean install of Ubuntu?

---

### Post by ncumming on 2008-05-24
Well, in your earlier post you said you have a 64 bit system, if that's the case then the ubuntu that you are running is fundamentally different than what i'm running (I have a 32 bit system).  It may make a difference or it may not...I'm not sure.

As far as ubuntu studio vs. standard ubuntu - ubuntu studio relies on a somewhat modified kernel (rt or real-time) in order to achieve the lowest possible latency when recording.  However, using GRUB you can set up your machine so that when you boot, you can choose either the generic kernel or the low-latency version.  When I run the generic kernel, my adapter works fine once i replaced the "built-in" driver that ubuntu loads by default with the rt2570 driver from serialmonkey.  However it does not work at all when i boot using the low latency kernel.

So the short answer is yes - using the standard ubuntu distribution instead of ubuntu studio may work for you. You may also be able to use GRUB to select between the rt and generic kernel (there are lots of how-tos in the forums and community documentation for configuring GRUB) depending on whether you want the low latency for audio recording or you want your wireless adapter to work.  But all of that is caveated by the fact that things may be different if you are using a 64 bit system, i have no way of knowing and you probably won't know until you try.

Make sense?

---

### Post by ncumming on 2008-05-24
Sorry i hadn't totally read your post - yes i had to reboot for my driver to load.  The how-to's don't necessarily tell you that but after loading the driver until i rebooted the adapter didn't really work right.

EDIT:

Here is the post I followed:

[http://ubuntuforums.org/showthread.php?t=739139](http://ubuntuforums.org/showthread.php?t=739139) Post#8

However, i used the rt2570 driver instead of the rt2500 driver, and my adapter is a usb adapter (which typically shows up as rausb0) not a PCI adapter (usually shows up as wlan0) and accordingly had to make the following changes:

FROM

sudo modprobe rt2500
ifconfig wlan0 up

TO:

sudo modprobe rt2570
ifconfig rausb0 up

---

### Post by VitalBodies on 2008-05-24
> **ncumming said:**
> Sorry i hadn't totally read your post - yes i had to reboot for my driver to load.  The how-to's don't necessarily tell you that but after loading the driver until i rebooted the adapter didn't really work right.

EDIT:

Here is the post I followed:

[http://ubuntuforums.org/showthread.php?t=739139](http://ubuntuforums.org/showthread.php?t=739139) Post#8

However, i used the rt2570 driver instead of the rt2500 driver, and my adapter is a usb adapter (which typically shows up as rausb0) not a PCI adapter (usually shows up as wlan0) and accordingly had to make the following changes:

FROM

sudo modprobe rt2500
ifconfig wlan0 up

TO:

sudo modprobe rt2570
ifconfig rausb0 up

Here is what I did:
```
Download to desktop: http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
Extract the driver (right click on its icon on your desktop and select "Extract Here.")
sudo apt-get install build-essential
cd ~/Desktop/rt2570-cvs-**2008052414**/Module #**(should = driver)**
make
sudo make install
sudo modprobe rt2570
ifconfig rausb0 up
```

It all went well to here:
sudo modprobe rt2570 #No command line response? 
ifconfig rausb0 up #ERROR while getting interface flags: No such device

A reboot and I get wlan0.
I am connecting sporadically using driver rt2500usb on wlan0...
From super fast to super slow...
  

NOTE: I am on 64-bit Ubuntu NOT on UbuntuStudio as I switched. 
I need my hardware to work and I am to new to struggle with it all. 

I did not blacklist anything is that the mistake?
Are these the blacklist commands? 
sudo -s
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist 

Additionally, how does one un-blacklist if one needs to go back to the driver they were using?

---

### Post by ncumming on 2008-05-24
> 
I did not blacklist anything is that the mistake?
Are these the blacklist commands?
sudo -s
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist


That's right, if you don't blacklist the linux drivers pre-installed in ubuntu it won't work.  The drivers will conflict with each other and you will get the sporatic performance that you are seeing.  There are two ways to blacklist drivers - one way is to use the echo command as you noted.  When you do that, essentially what you are doing is adding the driver names to a file called "blacklist."  The other way you can accomplish this is by typing:

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add the drivers you want to disable to the blacklist file.  All of this is contained in the how-to...

---

### Post by VitalBodies on 2008-05-24
> **ncumming said:**
> That's right, if you don't blacklist the linux drivers pre-installed in ubuntu it won't work.  The drivers will conflict with each other and you will get the sporatic performance that you are seeing.  There are two ways to blacklist drivers - one way is to use the echo command as you noted.  When you do that, essentially what you are doing is adding the driver names to a file called "blacklist."  The other way you can accomplish this is by typing:

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add the drivers you want to disable to the blacklist file.  All of this is contained in the how-to...

Tried blacklisting the rt2500 drivers but that did not help and I could not seem to get back to just having either the 2500 or the 2570 rather than the mix of the two. 

Reloaded Ubuntu to get a clean start again. 

Now that I can add SEE the blacklist file that helps.

---

### Post by VitalBodies on 2008-05-25
**SHORTENED INSTRUCTIONS:** 
Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
Extract the driver (right click on its icon on your desktop and select "Extract Here.")
sudo apt-get install build-essential
cd ~/Desktop/rt2570-cvs-**2008052414**/Module **(must = Folder Name)**
make
sudo make install
sudo gedit /etc/modprobe.d/blacklist 
#Added these entries to the blacklist to replace rt2500usb with rt2570usb: 
blacklist rt2500usb
blacklist RT2500USB

sudo modprobe rt2570
sudo ifconfig rausb0 up
REBOOTED then set networking to manual (used my routers setting SSID etc) rather than roaming and REBOOTED
sudo ifconfig rausb0 up
REBOOTED
Connected!

NOTE: You should keep these instructions on hand on your computer, as you will not be able to connect to get them...

NOTES: 
lshw -C network
Gets this:
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:12:17:83:ff:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=RT2500USB WLAN

Somehow I would have expected wireless=RT2570USB WLAN???

[COLOR="Red"]Thank you so much for your help and support![/COLOR] Do we know why the to default drivers do not work for us?

---

### Post by acad1 on 2008-05-26
Guess what guys,
I have just downloaded and installed the latest updates for 8.04 and these include a new kernel 2.6.24-17-generic. On re-start the D-link USB device does not work, so I should think that a re-install of the rt2570 driver is necessary!

---

### Post by chili555 on 2008-05-26
Correct. If you compiled it against 2.6.24-16, it doesn't exist in 2.6.24-17. Welcome to the world of compiling from source!

---

### Post by acad1 on 2008-05-26
You are so right chilli555!
I have just re-installed the rt2570 driver as in the shortened instructions in post #34 and am up and running again. I have so much to learn yet but it's great fun!

---

### Post by VitalBodies on 2008-05-26
So what does this tell us? 
[LIST]
[*]That we need to download the daily build of the driver before each update? This could help if it depends on the new kernel. 
[*]That we need to rebuild the driver after each update? Apparently yes I just needed to. 
[*]That we need to sudo apt-get install build-essential so we can rebuild the driver? Or is this now included in updates? This was included on mine. 
[*]Other: What do you think?
[/LIST]
The challenge here is when the driver fails one can not get online!
EDIT: 
**SHORT REINSTALL INSTRUCTIONS:**
1.) Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
--> If you did not do this before updating the kernel you still might be fine. 
--> Use the latest driver you have. 
2.) Extract the driver (right click on its icon on your desktop and select "Extract Here.")
3.) cd ~/Desktop/[COLOR="Red"]rt2570-cvs-2008052612[/COLOR]/Module [COLOR="Red"]#(must = Folder Name)[/COLOR]
4.) make
5.) sudo make install
6.) sudo modprobe rt2570
7.) sudo ifconfig rausb0 up
8.) Bring up the program RutilT and connect as needed...
9.) You should be Connected!

NOTE: You should keep these instructions on hand on your computer, as you will not be able to connect to get them...

---

### Post by acad1 on 2008-05-26
I used an old build of the rt2570 driver dated 3 May which was in the Waste Basket - (rt2570-cvs-2008050309)
The rebuild only needs to be done after a kernel update.
I did not "sudo apt-get install build essential" to rebuils the driver.
I did not blacklist any drivers, and on re-boot, the wireless connection was working.

"cat /etc/modprobe.d/ralink" shows   "alias rausb0 rt2570"

---

### Post by VitalBodies on 2008-05-26
> **acad1 said:**
> I used an old build of the rt2570 driver dated 3 May which was in the Waste Basket - (rt2570-cvs-2008050309)
The rebuild only needs to be done after a kernel update.
I did not "sudo apt-get install build essential" to rebuils the driver.
I did not blacklist any drivers, and on re-boot, the wireless connection was working.

"cat /etc/modprobe.d/ralink" shows   "alias rausb0 rt2570"

Thanks. I got the same from cat /etc/modprobe.d/ralink. 
I added a page here: 
[http://ubuntuforums.org/showthread.php?p=5048329#post5048329](http://ubuntuforums.org/showthread.php?p=5048329#post5048329)
For those that do not want to wade through this long thread. 
I must say I struggled for days to get my wireless setup and I hope we can save others from that fate. I still do not know what the problem is with the default driver. It would be better if that worked or we could make that work so we do not have to re-install all the time...

---

### Post by VitalBodies on 2008-05-26
Do you think we just need to upgrade the firmware?
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

These devices are said to work out of the box:
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

They use the Ralink RT2561 and RT2571 chipsets.

---

### Post by sefs on 2009-09-07
Hi I am having trouble here.

My setup

Ubuntu 8.10

Serialmonkey drivers.

cat /proc/version
```

Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Aug 18 16:25:45 UTC 2009

```

/etc/modprobe.d/ralink
```

alias wlan* rt73
alias ra0 rt2500
alias rausb0 rt2570

```

/etc/modprobe.d/blacklist
```

blacklist rt73
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt61pci
blacklist rt73usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
# blacklist rt2570
blacklist islsm_usb
blacklist islsm_device
blacklist islsm
blacklist ndiswrapper

```

iwconfig
```

rausb0    RT2500USB WLAN  ESSID:"myssid"  Nickname:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:BF:BA:79:82   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-36 dBm  Noise level:-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5958 (5.9 KB)  TX bytes:5958 (5.9 KB)

rausb0    Link encap:Ethernet  HWaddr 00:14:85:11:cf:33  
          inet6 addr: fe80::214:85ff:fe11:cf33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:627518 (627.5 KB)  TX bytes:26342 (26.3 KB)

rausb0:avahi Link encap:Ethernet  HWaddr 00:14:85:11:cf:33  
          inet addr:169.254.5.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep

#=====================================================================================================
# LOOPBACK LAN INTERFACE
#=====================================================================================================
auto lo
iface lo inet loopback
#
#
#=====================================================================================================
# WIRED LAN INTERFACE
#=====================================================================================================
#map eth0
#auto eth0
#iface eth0 inet dhcp
#
#
#
#==============================================================================$
# WIRELESS LAN INTERFACE
#==============================================================================$
map rausb0
auto rausb0
iface rausb0 inet dhcp
	pre-up ifconfig rausb0 down
       	pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
    	pre-up iwconfig rausb0 essid "myssid"
    	pre-up iwconfig rausb0 channel auto
    	pre-up iwconfig rausb0 mode Managed
    	pre-up iwpriv rausb0 auth 4
    	pre-up iwpriv rausb0 enc 4
    	pre-up iwpriv rausb0 wpapsk dafjasfuiiadllfdaufoajuajfldajfa
	pre-up ifconfig rausb0 up

```

The problem I am experiencing is that it just does not pick up dhcp.  If I try a static ip it still does not connect.

---

### Post by highfructose327 on 2009-09-07
sefs 

have you tried using the rt2500usb module instead of the rt2570 ?  I would try to comment out the rt2500usb in the blacklist and edit the alias for rausb to ```
 alias rausb0 rt2500usb
``` might be a long shot. This is just what came to mind when I looked at the info you have posted.

---

