---
title: "Problems with ipw3945 and ieee80211"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by caesar753 on 2007-05-25
Hi all, 
i'm trying to let a wireless connection work with an Intel wireless card, i tried everything, but nothing.
The problem is the sequent:

i downloaded and installed from Desktop the subsystem ieee80211 (i did first make and then sudo make install from ~/Desktop/ieee80211 directory) and it went well at all, then i tried to make the ipw3845 drivers, but this gave me this error:

```

root@antonio:~# cd /home/antonio/Desktop/ipw3945-1.2.0
root@antonio:/home/antonio/Desktop/ipw3945-1.2.0# make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  

Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1


```
I didn't know what this sentence means
> 
WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)
 
and I don't know how to let ipw3945 understand where my ieee80211 is.
I tried also to give the command IEEE80211_IGNORE_DUPLICATE=y but the make output gave me this error:

```

antonio@antonio:~/Desktop/ipw3945-1.2.0$ make IEEE80211_IGNORE_DUPLICATE=y
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.17-11-generic      /lib/modules/2.6.17-11-generic/build

You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1
antonio@antonio:~/Desktop/ipw3945-1.2.0$ 


```

I tried also to give manually the path of the ieee subsystem, trying every directory which is named ieee... but it doesn't work at all.
Now what do I have to do? I really don't know how to say to the ipw3945 drivers where to find my ieee subsystem, please HELP ME...

---

### Post by chili555 on 2007-05-25
What about the ipw3945 built in to the Edgy kernel did not work for you? It works perfectly for most all of us, including WPA encryption, monitor mode, kismet and everything you could want in a wireless card.

It should be as simple as:
#install linux-restricted-modules
#go to System -> Administration -> Restricted Drivers Manager and enable the 3945 driver
#command *sudo iwconfig eth1 <essid>* and *sudo iwconfig eth1 key <your_key>* (if you use WEP) and *sudo dhclient eth1*

---

### Post by caesar753 on 2007-05-26
This is another problem: in fact I read that this this package should be installed before installing the ipw driver and I tried to install the linux-restricted-modules for the kernel (2.6.11-17-generic) but it tells me that I have first to install the nvidia-kernel-common package.
I don't understand why i have to do this, because the video card is ATI and not NVIDIA, but i try to install this package but then it tells me "nvidia-kernel-common is broken or obsolete" or something like this and doesn't let me install.
How can I resolve this problem?
The computer system specifications are these:

Intel Centrino Duo
Ati Mobility Radeon X1600
1GB RAM

P.S.:i'm not using now feisty fawn but edgy eft distribution, so i don't have the restricted driver manager, and so do i have to install manually the ipw3945 drivers and then let then run manually?

Thanks...

---

### Post by chili555 on 2007-05-26
I have no idea why restricted-modules depends on nvidia-kernel-common. On my Centrino Duo, ATI X1400, ipw3945, it's installed and if I try to remove it, it wants to remove linux-restricted-modules! 

I would try:```
sudo apt-get install linux-restricted-modules-common
```and accept any dependencies it offers. Or try:```
sudo apt-get install linux-restricted-modules-`uname -r`
```Those are backticks, the symbol to the left of 1 on your keyboard.

Without the restricted driver manager, you should be able to *sudo modprobe ipw3945* and then configure your interface to connect.

---

### Post by caesar753 on 2007-05-26
Ok, this is very strange, linux-restricted-modules-common are installed and i'm able to load ipw3945 modules with the command *modprobe* etc but... the card is not detected!!!!
In fact i try to go to the section **System->Administration->Network** but it shows me only the Wired Connection through Ethernet and the Dialup modem connection, there is no trace of the wireless connection.
What command should i give to let the system detect the wireles card?
Ah, i was forgetting that the wireless led and, i think, also the wireless card are turned on by the key combination Fn+F2 but it doesn't affect any effect, while in Windows it lets the wireless led turn on and the wireless connection start; i tried also to give this command
```
echo 1>/proc/acpi/asus/wled
```
following this post and its solution: *[http://ubuntuforums.org/showthread.php?t=427222&highlight=intel+ipw+wireless+card](http://ubuntuforums.org/showthread.php?t=427222&highlight=intel+ipw+wireless+card)*
(the laptop is an asus A6000 serie) but it didn't do anything, do you thing that the wireless card is not recognized because it is not turned on? How can i enable the key combination, if this doesn't let me turn on the wireless card?
 Thanks...

---

### Post by chili555 on 2007-05-29
Please try:```
echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
```

---

### Post by tmunro55 on 2007-07-23
Hi all,

   I am using Feisty Fawn, and ipw3945.1.2.1. I am having the exact same problems as caesar753. I used make and make install for ieee80211 (1.2.18) and there were no errors. My hardware is Dell Inspiron 6400. ipw3945 did not work right out of the box. the odd thing is, it looks like it aught to be working. The wireless light is on, ifconfig and iwconfig both show proper configurations:

tim@whistlestop:~/wireless$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:B4:A8:61  
          inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb4:a861/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2269016 (2.1 MiB)  TX bytes:389351 (380.2 KiB)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:22:38:27  
          inet addr:192.168.1.203  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe22:3827/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:172 dropped:176 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19401 (18.9 KiB)  TX bytes:2447 (2.3 KiB)
          Interrupt:16 Base address:0x6000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2396 (2.3 KiB)  TX bytes:2396 (2.3 KiB)

tim@whistlestop:~/wireless$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"DFU-RAO"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:12:17:0F:06:09   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-44 dBm  Noise level=-44 dBm
          Rx invalid nwid:0  Rx invalid crypt:134  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

    When I disable eth0 (land line) I have no connectivity. Pinging my gateway gives me destination unreachable.

tim@whistlestop:~/wireless$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.203 icmp_seq=2 Destination Host Unreachable
From 192.168.1.203 icmp_seq=3 Destination Host Unreachable
From 192.168.1.203 icmp_seq=4 Destination Host Unreachable

    Any help would be greatly appreciated.

--
Tim

---

### Post by tmunro55 on 2007-07-25
OK, this has been resolved. There were two issues. One is that I had both interfaces running. Not sure if that is appropriate or not. Two is that I need to configure the wireless with iwconfig everytime I boot up. I have scripted it but would like it to be automatic. Any thoughts on this?

---

### Post by BC7333 on 2007-08-14
Have the same card and resolved with wicd and kernel upgrade.

Details here: [http://ubuntuforums.org/showthread.php?t=514792](http://ubuntuforums.org/showthread.php?t=514792)

---

