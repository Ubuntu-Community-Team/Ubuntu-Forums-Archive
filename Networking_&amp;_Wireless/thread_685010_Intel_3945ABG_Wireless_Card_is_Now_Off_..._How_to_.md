---
title: "Intel 3945ABG Wireless Card is Now Off ... How to Turn it Back On"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by MSwal28462 on 2008-02-01
I've been running 7.10 since November and "lovin it".  However, two days ago my internal Intel 3945ABG appears to have become "turned off".  I can see it:

mark@Mark-Swallow:~$ lspci|grep Network
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

but it is not recognized during boot up as two days ago it was recognized as ETH1 and now that is gone:

mark@Mark-Swallow:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

mark@Mark-Swallow:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:C4:0C:EC  
          inet addr:172.16.0.134  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::216:d3ff:fec4:cec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6227218 (5.9 MB)  TX bytes:1835011 (1.7 MB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6090 (5.9 KB)  TX bytes:6090 (5.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.201.1  Bcast:192.168.201.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.227.1  Bcast:192.168.227.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

How do I get this card turned back on?

Mark

---

### Post by MSwal28462 on 2008-02-01
I've tried to follow the directions on this site (but put in 3945 instead):  [http://ubuntuforums.org/showthread.php?p=4244341](http://ubuntuforums.org/showthread.php?p=4244341) but with no luck, as I get this error on trying to load the IPW3945 module according to the install file with this TAR file below I get the following error:

 sudo ./load debug=0
./load: 5: Syntax error: "(" unexpected

Here are the instructions I'm trying to follow:

2. QUICK INSTALL STEPS
-----------------------------------------------

The following provides steps that can be used to manually install and 
load the driver.  

Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net).  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.2.16.tgz
	% cd ieee80211-1.2.16
	% make 
	# make install   <--- You may need to be root
	% cd ..

If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information.

Once the ieee80211 subsystem is installed, we build the ipw3945.ko module:

	% tar xzvf ipw3945-1.2.2.tgz
	% cd ipw3945-1.2.2
	% make

Now we install the firmware files (first finding where to install them):

	% wget [http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz](http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz) .
	% DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)
	% tar xzvf ipw3945-ucode-1.14.2.tgz 
	% less ipw3945-ucode-1.14.2/LICENSE.ipw3945-ucode
	# cp ipw3945-ucode-1.14.2/ipw3945.ucode $DIR

NOTE:  'DIR' above typically works out to /lib/firmware.

Now we obtain the regulatory daemon:

	% wget [http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz](http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz) .
	% tar xzvf ipw3945d-1.7.22.tgz
	% less ipw3945d-1.7.22/LICENSE.ipw3945d

Depending on your architecture perform one of the following	

For 32-bit systems:

	# cp ipw3945d-1.7.22/x86/ipw3945d /sbin

or for 64-bit systems:

	# cp ipw3945d-1.7.22/x86_64/ipw3945d /sbin

And now we can try to load the module, first clearing the kernel log:

	# ./load debug=0

---

### Post by MSwal28462 on 2008-02-04
I have been searching like crazy for the answer to this problem.  I'm very embarrassed to say that there's this little switch on the front of my PC that when switched to on, reactivated the wireless card.

I'm highly embarrassed, but I decided to post this anyway so that if someone runs into this you'll know to check for this switch .... I didn't even know I had it until i read about it in another post.

Mark

---

