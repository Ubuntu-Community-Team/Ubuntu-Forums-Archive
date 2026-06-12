---
title: "Wireless Problem Advent Milano Ubuntu Lucid"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Ymurti on 2010-06-03
Please I need help!

I am an absolute Beginner and I can not connect through wireless although through wire I can connect.:(

My ubuntu is 10.04 LTS Lucid 
and the Kernel is  2.6.32-22-generic

My netbook is an Advent Milano Elite

---

### Post by zipperback on 2010-06-03
Open a terminal window and provide us the output from the following commands.

```

lspci
lsusb
ifconfig
iwconfig

```

Also please tell us any error messages that you might be getting in addition to the above requested information.

- zipperback
:popcorn:

---

### Post by zipperback on 2010-06-03
To open a terminal window you click on Applications -> Accessories -> Terminal.

- zipperback
:popcorn:

---

### Post by Ymurti on 2010-06-04
Dear Zipperback,

Thank You for your kindness,

Here it is the result, 

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:3831 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfg

eth0      Link encap:Ethernet  HWaddr 00:03:0d:ef:60:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16472 (16.4 KB)  TX bytes:16472 (16.4 KB)

iwconfig  

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ramjet_1953 on 2010-06-04
It looks like you need to patch the kernel to get this wireless chipset to work.

Check out this thread for information:

[http://ubuntuforums.org/showthread.php?t=1313132&highlight=1001ha](http://ubuntuforums.org/showthread.php?t=1313132&highlight=1001ha)

Regards,
Roger :)

---

### Post by anewguy on 2010-06-04
See this thread:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1490123]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1490123")

In particular, pay attention to the post that has the 4 commands in it, including the "touch".

Any problems or questions, please post back!

Dave ;)

---

### Post by Ymurti on 2010-06-04
Dear ramjet_1953 and anewguy,

Thank you for yor post but I got lost in the jargon and the links that are in it. Please bear in mind I am a Absolute beginner.  

Yours,

Ymurti

---

### Post by anewguy on 2010-06-04
Okay, in the thread I mentioned it wants you to do the following, which I will explain how to do:

```
as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
```

Step-by-step, here we go:

- open a terminal window (applications/accessories/terminal)

- type:

sudo mkdir -p /etc/Wireless/RT2860STA/ <press enter>

This creates a new folder called Wireless in the /etc system folder, and creates another folder called RT2860STA within that folder.

-type:

sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat <press enter>

This creates a file called RT2860STA.dat in the newly created folder.  Note that the file is empty.


- type:

sudo service network-manager restart <press enter>

This will restart network manager, so it will find the newly created folders and file, and should now show your wireless working.  Click on the network manager icon in the upper tray and be sure "Enable Wireless" is checked.

You can now close the terminal window:

- type:

exit <press enter>


Dave ;)

---

### Post by Ymurti on 2010-06-04
I tried and I got this reply:

mkdir: invalid option -- '/'
Try 'mkdir --help' for more information.

---

### Post by anewguy on 2010-06-04
I don't know what you may have done wrong, but just copy and paste the following into a terminal window:

sudo mkdir -p /etc/Wireless/RT2860STA/

I just did it on my PC to be sure the syntax was correct. Sometimes when command lines are given you are better off just copying and pasting them (of course removing the <press enter>) instead of trying to type them again.  Case and spacing are very important in Linux.

Let me know what happens.  After you get this to run ok, be sure to go back to my previous post and keep doing the things listed there after the mkdir.

Dave ;)

---

### Post by Ymurti on 2010-06-05
Dear Dave,

I copied and pasted as you told and I go this:

[sudo] password for yajnamurti:

Then I tried to type the password that I normally use to log in in Ubuntu, I noticed that when I was typing the password the cursor did not move, not registering the words that I was typing. Even though I pressed enter and it came to the initial point:

yajnamurti@yajnamurti-netbook:~$

---

### Post by Ymurti on 2010-06-05
Dear Dave,

You are great, It is working the Wireless!!!!

I continued doing the whole process and miracle, the Wireless that I was struggling with for long time is working.

Thank You very much!

Ys  yajnamurti das

---

### Post by anewguy on 2010-06-05
You're welcome!  I'm glad it's working for you, and welcome to the wonderful world of Ubuntu!

Dave ;)

---

### Post by niffuss on 2010-08-27
hi i have same problem and tried all the above and when i get to sudo service network-manager restart/

it states that it is not upstart command ? 

i am a newbie and the problem with my laptop started when my screen smashed, i attached external monitor and replaced harddrive, reinstalled win xp & just tried ubuntu(better than xp) i got drivers and installed them all, it connects to internet via cable but not wireless?  my laptop is a advent milano netbook laptop n270 atom

can any1 please help its been two weeks and endless searching on google but nothing to help?

:(

---

