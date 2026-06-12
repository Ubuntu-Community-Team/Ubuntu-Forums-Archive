---
title: "Ralink wireless network Scaning"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Saghaulor on 2008-01-11
I successfully installed the Railink wireless utility, and was using it with much success for several days. 

I'm not sure what I did, but now when I scan for networks, the utility freezes and doesn't do anything. I have to use the system monitor to kill the process because it will not respond to anything.

Any ideas? 

Should I uninstall and try to reinstall?

Thank you in advance.

-Stephen

---

### Post by PriceChild on 2008-01-11
thread moved aproved and bumped

---

### Post by pytheas22 on 2008-01-11
```
I successfully installed the Railink wireless utility
```

Do you mean that you're using Rutilt?

If so, I think that it's meant to work only with the ralink drivers from serialmonkey, [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) .  By default Ubuntu (at least in Gutsy) uses a newer version of the ralink drivers (called mac80211 or something; I don't know the details) that are supposed to work through Network Manager.  The serialmonkey drivers will NOT work properly with Network Manager, in my experience, and conversely the mac80211 drivers will not work reliably with rutilt.  That's been my experience using the rt73 and rt2570 drivers, at least.

So if you want to use Rutilt instead of Network Manager, make sure you're using the serialmonkey drivers--download the appropriate one, compile it, modprobe it and blacklist the mac80211 modules.

And I'll also note that the mac80211 rt73 driver for me was very unreliable, crashing arbitrarily.  So until Ubuntu ships with ralink drivers that actually work all the time, serialmonkey is probably still the way to go.

---

### Post by Saghaulor on 2008-01-13
> **pytheas22 said:**
> ```
I successfully installed the Railink wireless utility
```

Do you mean that you're using Rutilt?

If so, I think that it's meant to work only with the ralink drivers from serialmonkey, [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) .  By default Ubuntu (at least in Gutsy) uses a newer version of the ralink drivers (called mac80211 or something; I don't know the details) that are supposed to work through Network Manager.  The serialmonkey drivers will NOT work properly with Network Manager, in my experience, and conversely the mac80211 drivers will not work reliably with rutilt.  That's been my experience using the rt73 and rt2570 drivers, at least.

So if you want to use Rutilt instead of Network Manager, make sure you're using the serialmonkey drivers--download the appropriate one, compile it, modprobe it and blacklist the mac80211 modules.

And I'll also note that the mac80211 rt73 driver for me was very unreliable, crashing arbitrarily.  So until Ubuntu ships with ralink drivers that actually work all the time, serialmonkey is probably still the way to go.

I'm using Gutsy, and when I run synaptic, I installed the rt2570 source and the Rutilt. After that the wireless card worked fine. Only recently has this problem surfaced.I seemed to have resolved the scan freeze problem, however, I still can't connect to networks wireless now. 

Also, I'm quite a noob, so please dumb down your directions for me.

Thank you.

-Stephen

---

### Post by pytheas22 on 2008-01-14
Yeah, it sounds like you're using the ralink drivers that ship with Gutsy, which are not that stable.

Step by step, here's what to do to get the good drivers:

1. get what you need to compile stuff (if you don't have it already):

```

sudo apt-get build-essential
```

2. download the rt2570 driver from serialmonkey with this link: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) 

3. that file should appear on your desktop (assuming that that's where you save your downloads to).  Unpack it by right clicking on it and selecting "Extract Here"

4. in a terminal, change to the folder that you just created by unpacking the rt2570 tarball.  The exact name of the file will depend on the date I think, but the code will be similar to:
```

cd /home/YOUR-USER-NAME/Desktop/rt2570-cvs-2008---some-other-numbers---
```

remember that you can just start to type the filename and press tab, and it will automatically select the rest of it for you

5. change to the Module directory inside the rt2570-cvs... folder:

```
cd Module
```

6. compile the driver:

```
make
```

it will possibly give you a warning about the module being "much too big;" you can ignore that

7. install the driver:

```
sudo make install
```

8. blacklist the unstable default ralink drivers:

in a terminal, type:

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the following lines to that file:

```
#mac80211 ralink modules are not stable
blacklist rt2x00usb
blacklist rt61pci
blacklist rt73usb
blacklist rt2x00pci
blacklist rt2400pci
blacklist rt2x00lib
blacklist rt2500usb
blacklist rt2500pci
```

9. insert your new rt2570 module into modprobe:

```
sudo modprobe rt2570
```

10. bring up the interface:

```
sudo ifconfig rausb0 up
```

11. now try running Rutilt, and hopefully everything will work!

```
sudo rutilt
```

Keep posting if you have trouble.  Good luck.

---

### Post by Saghaulor on 2008-01-15
Should I remove the rt2570 source and rutilt app from synaptic before running the directions you specified?

---

### Post by pytheas22 on 2008-01-15
No, it shouldn't make a difference.  Rutilt is just an application to manage wireless connections (built by the serialmonkey people especially for their drivers, although it's supposed to work with any drivers); it doesn't have anything to do with the drivers themselves.  And the rt2570 source code in Synaptic is just the same thing available from the serialmonkey website, but I think it's a little out of date, so you're better off using the latest version direct from the site.  But having it downloaded from Synaptic won't interfere with also having it from the site, so you can delete it if you want but it's not necessary.

Sorry for being so verbose; good luck building the driver!

---

### Post by Saghaulor on 2008-01-25
When I try to doe the "sudo apt-get build essential" command I receive the following message:

"stephen@ubuntu:~$ sudo apt-get build essential
[sudo] password for stephen:
E: Invalid operation build
stephen@ubuntu:~$" 

Now, I went through and did the rest of the steps. I believe without any other errors. I was able to use the RUTILT utility to connect to my wlan, but after sever minutes I lost connectivity. Then after a reboot I receive this message when I try to run RUTILT:

"Critical error :
Can't find any wireless network interface.
Code : -3"

I don't know what went wrong, but I would like to get this running again. What does the first message mean? How can I point RUTILT back to my rt2570?

Thank you in advance.

---

### Post by rustybronco on 2008-01-25
> **Saghaulor said:**
> When I try to doe the "sudo apt-get build essential" command I receive the following message:

"stephen@ubuntu:~$ **sudo apt-get build essential**
[sudo] password for stephen:
E: Invalid operation build
stephen@ubuntu:~$" 

 that would be **sudo apt-get install build-essential** you're missing the dash and install.

---

### Post by pytheas22 on 2008-01-26
Yes, you were just missing the dash and "install" (sorry, my mistake) in the sudo apt-get install build-essential command.  But if the rest of the steps worked, then it didn't matter (you apparently already had the build-essential package installed).

As for your error with Rutilt, it sounds like the device is just not up, or possibly the module is not loaded.  Try running the commands:
```

sudo modprobe rt73
sudo ifconfig wlan0 up
```

before starting Rutilt.  That should solve the problem.  If it doesn't, run Rutilt from the command line and post the output.  If it does, you could write a script to automatically bring your interface up and make it connect every time you boot your computer (Rutilt has command line options to autoconnect; read its man page for those).

And I don't know why the connection would drop after a few minutes; it could just have been a burp on your wlan or something.  Try connecting again and see what happens.

---

### Post by Saghaulor on 2008-01-28
I got to step #10 and received the following message.

"*** Update /etc/modprobe.d/ralink alias for rausb0
stephen@ubuntu:~/Desktop/rt2570-cvs-2008011719/Module$ sudo modprobe rt2570
stephen@ubuntu:~/Desktop/rt2570-cvs-2008011719/Module$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
stephen@ubuntu:~/Desktop/rt2570-cvs-2008011719/Module$"

Um, what now?

---

### Post by Saghaulor on 2008-01-28
> **pytheas22 said:**
> Yes, you were just missing the dash and "install" (sorry, my mistake) in the sudo apt-get install build-essential command.  But if the rest of the steps worked, then it didn't matter (you apparently already had the build-essential package installed).

As for your error with Rutilt, it sounds like the device is just not up, or possibly the module is not loaded.  Try running the commands:
```

sudo modprobe rt73
sudo ifconfig wlan0 up
```

before starting Rutilt.  That should solve the problem.  If it doesn't, run Rutilt from the command line and post the output.  If it does, you could write a script to automatically bring your interface up and make it connect every time you boot your computer (Rutilt has command line options to autoconnect; read its man page for those).

And I don't know why the connection would drop after a few minutes; it could just have been a burp on your wlan or something.  Try connecting again and see what happens.

I performed the above commands only to receive the following messages.
"stephen@ubuntu:~/Desktop/rt2570-cvs-2008011719/Module$ sudo modprobe rt73
FATAL: Module rt73 not found.
stephen@ubuntu:~/Desktop/rt2570-cvs-2008011719/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device"

---

### Post by Saghaulor on 2008-01-28
Also, here is my results from trying to run RUTILT from terminal.

"stephen@ubuntu:/$ rutilt
Can't find any wireless network interface.
Code : -3"

---

### Post by Saghaulor on 2008-02-04
I decided to rebuild my system as I wasn't getting anywhere.

I tried installing the rt2570 source and rutilt from synaptic. It worked until I turned my machine off. Then it would lock up when scanning for an available network.

So I tried your steps again.

Here are my results.

stephen@stephen-laptop:~$ sudo apt-get build-essential
[sudo] password for stephen:
E: Invalid operation build-essential
stephen@stephen-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 3150kB/7157kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-libc-dev 2.6.22-14.51 [653kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [2497kB]
Media change: please insert the disc labeled                 
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
in the drive '/cdrom/' and press enter

Fetched 3150kB in 1m51s (28.3kB/s)                                             
Selecting previously deselected package linux-libc-dev.
(Reading database ... 90091 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.51_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_amd64.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.51) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
stephen@stephen-laptop:~$ cd /home/stephen/rt*
stephen@stephen-laptop:~/rt2570-cvs-2008020417$ cd Module
stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_main.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/mlme.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_bulk.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/connect.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/sync.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_init.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtmp_tkip.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/wpa.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtmp_wep.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_info.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/assoc.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/auth.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/auth_rsp.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/md5.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_io.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/sanity.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rtusb_data.o
  CC [M]  /home/stephen/rt2570-cvs-2008020417/Module/rt2x00debug.o
  LD [M]  /home/stephen/rt2570-cvs-2008020417/Module/rt2570.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/stephen/rt2570-cvs-2008020417/Module/rt2570.mod.o
  LD [M]  /home/stephen/rt2570-cvs-2008020417/Module/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo make install
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/stephen/rt2570-cvs-2008020417/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/stephen/rt2570-cvs-2008020417/Module/rt2570.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for stephen:
stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo modprobe rt2570
[B]stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device[/B]
stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo rutilt


Here is what I received after using the ifconfig and iwconfig commands.

stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo iwconfig
[sudo] password for stephen:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:2B:EE:57  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe2b:ee57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5431413 (5.1 MB)  TX bytes:399984 (390.6 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:82:5F:C3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-82-5F-C3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


stephen@stephen-laptop:~/rt2570-cvs-2008020417/Module$ sudo rutilt

I am still having trouble getting this device to work. If it helps, I'm using the AMD64 version of Gutsy. 

Please help, I do not want to have to install Windows and dual boot just so that I can use my wireless.

Your assistance is appreciated.

---

