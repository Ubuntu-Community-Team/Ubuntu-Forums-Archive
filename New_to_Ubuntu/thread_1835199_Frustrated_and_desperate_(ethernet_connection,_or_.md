---
title: "Frustrated and desperate (ethernet connection, or lack thereof)"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by ultravioletfrog on 2011-08-28
Hey all,

I am a college freshman who just moved in to my dorm. I used Ubuntu at home and loved it, so when picking out a computer for college, I wanted to have a machine built for Linux use so I could fully embrace the open-source movement.

After doing some research, I settled on a [ZaReason Strata 5330]("http://zareason.com/shop/Strata-5330.html").

There's one big issue, though... it doesn't detect an ethernet connection, which is required for internet connection in my dorm. With classes starting soon, this is a huge problem. I'm starting to regret not just getting an overpriced Windows or Mac machine like everybody else.

I've tried three different ethernet cords and my computer never detects a connection. I've had to tether from my phone using a really sketchy app. It's incredibly inconvenient, and I can't even browse websites using https.

If anybody could give me any direction whatsoever, I'd really appreciate it! Thanks so much for your time and help!

---

### Post by papibe on 2011-08-28
Could you post the result of these commands?
```
$ sudo lshw -C network

$ sudo lspci -nn | grep -i eth

$ ifconfig

$ rount -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

BTW: Welcome!

---

### Post by ultravioletfrog on 2011-08-28
Here they are. Note that I'm tethering while running these... not sure if that affects anything or not. Thanks for the welcome!
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e0:b9:a5:42:4d:a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:94400000-9440ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:92404000-92404fff memory:92400000-92403fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: easytether0
       serial: 02:00:54:74:68:72
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=192.168.117.2 link=yes multicast=yes port=twisted pair speed=10Mbit/s
```
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
```
```
easytether0 Link encap:Ethernet  HWaddr 02:00:54:74:68:72  
          inet addr:192.168.117.2  Bcast:192.168.117.255  Mask:255.255.255.0
          inet6 addr: fe80::54ff:fe74:6872/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:5744725 (5.7 MB)  TX bytes:998457 (998.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4460 (4.4 KB)  TX bytes:4460 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:42:4d:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```
No command 'rount' found, did you mean:
 Command 'mount' from package 'mount' (main)
 Command 'mount' from package 'loop-aes-utils' (universe)
rount: command not found
```
```
Server:        8.8.8.8
Address:    8.8.8.8#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156
```
```
; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51556
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        284    IN    A    91.189.94.156

;; AUTHORITY SECTION:
ubuntu.com.        128678    IN    NS    ns3.canonical.com.
ubuntu.com.        128678    IN    NS    ns1.canonical.com.
ubuntu.com.        128678    IN    NS    ns2.canonical.com.

;; ADDITIONAL SECTION:
ns3.canonical.com.    133995    IN    A    209.6.3.210
ns1.canonical.com.    133995    IN    A    91.189.94.173
ns2.canonical.com.    149182    IN    A    91.189.94.219

;; Query time: 1136 msec
;; SERVER: 8.8.4.4#53(8.8.4.4)
;; WHEN: Sun Aug 28 22:26:23 2011
;; MSG SIZE  rcvd: 156
```

---

### Post by papibe on 2011-08-28
Sorry about that, it is:
```
$ route -n
```

---

### Post by ultravioletfrog on 2011-08-28
```
Kernel IP routing table
Destination     Gateway         Genmatsk         Flags Metric Ref    Use Iface
192.168.117.0   0.0.0.0         255.255.255.0   U     1      0        0 easytether0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 easytether0
0.0.0.0         192.168.117.1   0.0.0.0         UG    0      0        0 easytether0
```

I feel like easytether is screwing it up... let me know if I should run this all again with it off!

---

### Post by madjr on 2011-08-28
> **ultravioletfrog said:**
> Hey all,

I am a college freshman who just moved in to my dorm. I used Ubuntu at home and loved it, so when picking out a computer for college, I wanted to have a machine built for Linux use so I could fully embrace the open-source movement.

After doing some research, I settled on a [ZaReason Strata 5330]("http://zareason.com/shop/Strata-5330.html").

There's one big issue, though... it doesn't detect an ethernet connection, which is required for internet connection in my dorm. With classes starting soon, this is a huge problem. I'm starting to regret not just getting an overpriced Windows or Mac machine like everybody else.

I've tried three different ethernet cords and my computer never detects a connection. I've had to tether from my phone using a really sketchy app. It's incredibly inconvenient, and I can't even browse websites using https.

If anybody could give me any direction whatsoever, I'd really appreciate it! Thanks so much for your time and help!

this also happens to many "overpriced" Windows or Macs

the **Gigabit Ethernet** port is used by lots of manufacturers.

zareason only makes/rebrand the cases, nothing else, all other hardware is the same generic that all use.

anyway have you been able to contact them?

i believe you have warranty in case we cant get it fixed here for u

---

### Post by ultravioletfrog on 2011-08-28
I contacted them through Twitter and email but have yet to hear anything.

---

### Post by papibe on 2011-08-28
It looks like every is setup correctly (except the use of the Google DNS [8.8.8.8.]).

I'm guessing you are able to get to Internet sites, but not to Campus site. If you need to bypass a security/login screen maybe all is blocked.

To test this theory, go to Network Connections, go to your ethernet interface and edit it. There go to the IPv4 tab and change the Method from 'Automatic (DHCP) address only' to just 'Automatic (DHCP)'.

Either restart your machine or open a terminal and restart your network:
```
$ sudo service network-manager restart
```
Try connecting to the campus sites, and the Internet.

I hope it helps,
Regards.

---

### Post by madjr on 2011-08-28
> **ultravioletfrog said:**
> I contacted them through Twitter and email but have yet to hear anything.

well no worries, you will only need to contact them in case the hardware is really faulty, for the warranty.

do you know if the wifi is working on the machine? you can always setup one of those wifi things to the ethernet cable.

and you positive the ethernet is working? maybe tell a friend to connect his computer

---

### Post by ultravioletfrog on 2011-08-28
The problem is there *isn't* an ethernet interface. There are absolutely no wired connections listed in my network manager, which is what really has me worried.
> **madjr said:**
> do you know if the wifi is working on the machine?  you can always setup one of those wifi things to the ethernet  cable.
It sure is! I used this computer for a while at home and the wireless network worked perfectly well there.

---

### Post by madjr on 2011-08-29
so, did you remove the google dns?

---

### Post by wormyblackburny on 2011-08-29
Not sure why you guys are worrying about DNS, he isn't connected to the college's network, he is using wireless tether. A simple search for the name of the ethernet adapter and Ubuntu yeilds these instructions. Give em a try :)

Make sure dkms and gcc are installed:

 sudo apt-get install dkms gcc 

Create the dkms.conf:
 echo 'PACKAGE_NAME=r8168 PACKAGE_VERSION=8.019.00 MAKE[0]="make" BUILT_MODULE_NAME[0]=r8168 BUILT_MODULE_LOCATION[0]="src/" DEST_MODULE_LOCATION[0]="/kernel/updates/dkms" AUTOINSTALL="YES"' > /usr/src/r8168-8.019.00/dkms.conf 

Then run:
 dkms add -m r8168 -v 8.019.00 dkms build -m r8168 -v 8.019.00 dkms install -m r8168 -v 8.019.00

---

### Post by wormyblackburny on 2011-08-29
BTW.... no wireless in your dorms? What's up with that? What College is it? Generally they will post how-to's for how to connect to ethernet/wireless. Additionally, most schools that have any kind of engineering programs have many users on various flavors of Linux. I highly suggest joining the school's Linux users club/group...

---

### Post by ultravioletfrog on 2011-08-29
Thanks for the responses! wormyblackburny, when I try to do the second part (dkms.conf) I get this message:

bash: /usr/src/r8168-8.019.00/dkms.conf: No such file or directory

---

### Post by wormyblackburny on 2011-08-29
Hmmmm.... lets try these instructions then

cd /usr/src 
wget [http://djlab.com/stuff/r8168-8.019.00.tar.bz2](http://djlab.com/stuff/r8168-8.019.00.tar.bz2) 
tar jxvf r8168-8.019.00.tar.bz2 
cd r8168-8.019.00 
make clean modules
 make install 
depmod -a echo "blacklist r8169" >> /etc/modprobe.d/blacklist-network update-initramfs -u 

Then, reboot the box and check which driver you&#8217;re using with &#8216;ethtool -i eth0&#8242;.  It should now be r8168 instead of r8169:
 driver: r8168 version: 8.019.00-NAPI firmware-version: bus-info: 0000:01:00.0

---

### Post by wormyblackburny on 2011-08-29
which kernel version are you using? It's possible just updating to the latest kernel release will fix it. Post the results of 

uname -r

if that last set of instructions i gave you don't work

---

### Post by ultravioletfrog on 2011-08-29
That command gives me this:
```
2.6.38-11-generic
```Following the other instructions now, too. Thanks for being so willing to help!

Edit: Once I start doing the "make clean modules" command, I get lots of errors and messages about being denied access, even if I do everything as root.

---

### Post by wormyblackburny on 2011-08-29
even if you do: sudo make clean modules?

well either way, we at least have the folder created for the first set of instructions. try the first set of instructions i gave you....

---

### Post by ultravioletfrog on 2011-08-29
sudo make clean modules does this...
```
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.019.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/usr/src/r8168-8.019.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.019.00/src'
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.019.00/src'
make: *** [modules] Error 2
```

And I get "permission denied" when I try the first instructions. Should I chmod the folder?

---

### Post by wormyblackburny on 2011-08-29
might try taking a look at this thread too:  [http://ubuntuforums.org/showthread.php?p=10283670](http://ubuntuforums.org/showthread.php?p=10283670)

---

### Post by ultravioletfrog on 2011-08-29
Unfortunately, I can't download, since tethering doesn't support [ftp://.](ftp://.) Any chance somebody could download the tarball and send it to me via private message? I realize this is incredibly inconvenient, but I sure would appreciate it.

I'm off to bed, actually--will continue to play around with this tomorrow. If anybody has any other insight please post it, and thanks much to everybody who has helped me already!

---

### Post by madjr on 2011-08-29
hm, i wonder if trying ubuntu from a live-cd/usb (either the current or dev release) will still have the same issue.

---

### Post by ultravioletfrog on 2011-08-29
THANK YOU everybody who helped! I'm not sure what did it, but I did every solution posted and something must have worked.

The Ubuntu community is awesome.

Edit: Oh, and for whoever's wondering, I'm attending the University of Wisconsin-Milwaukee.

---

### Post by wormyblackburny on 2011-08-29
No problem, make sure to mark the thread as solved when you have a chance :)

---

### Post by madjr on 2011-08-29
glad to hear that.

must had been some wrong configuration or something. I was pretty sure it was not the machine, since zareason has a good reputation of throughly testing their hardware with linux and was not an old computer either.

if it ever happens again you should insert a live-cd/usb and see if that works, then you know is a bad config.

and i must say that on linux i hardly had encounter problems with the ethernet, encountered much more when i was using windows...

---

