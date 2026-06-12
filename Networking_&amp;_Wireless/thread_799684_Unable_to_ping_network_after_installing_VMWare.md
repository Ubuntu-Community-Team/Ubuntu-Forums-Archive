---
title: "Unable to ping network after installing VMWare"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by shootermk on 2008-05-19
Hi everyone, I'm running an Amilo laptop with wireless and lan adapter, and just finished installing VMWare. My WLan adapter is what I use for work and it has a static IP address of 192.168.0.188. Now, when I try to ping an address on the network it gives me this error:

shooter@leptop:~$ ping 192.168.0.163
PING 192.168.0.163 (192.168.0.163) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable

The strange it is that my static address is not 192.168.0.1.

After doing ifconfig I got this:

shooter@leptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:65:0c:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110175 (107.5 KB)  TX bytes:110175 (107.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.87.1  Bcast:172.16.87.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:e0:b2:59  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fee0:b259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12841698 (12.2 MB)  TX bytes:1348558 (1.2 MB)
          Interrupt:16 Memory:c0300000-c0310000 

The strange thing is that I'm having an internet connection (I have wireless router that I connect to and use as gateway) I connect to the wireless router but I cannot ping it. Please any help with this will be much appreciated!

Regards,
Mitko

---

### Post by superprash2003 on 2008-05-19
there could be an ip conflict.. most wireless routers have an ip like 192.168.0.1 and your vmnet1 too has 192.168.0.1 .. so firstly change the ip address of vmnet1 from 192.168.0.1 to anything else

---

### Post by shootermk on 2008-05-20
> **superprash2003 said:**
> so firstly change the ip address of vmnet1 from 192.168.0.1 to anything else

Well, I changed the IP in the vmWare but after I reboot the machnie and make ifconfig, the address of vmnet1 is still 192.168.0.1 . Am I doing something wrong here? How to change IP address of the vmnet1?

---

### Post by superprash2003 on 2008-05-20
try changing it in System->administration->network

---

### Post by shootermk on 2008-05-22
Okay, I finally managed to fix this. It seems that vmWare does not support networking through wireless cards. So, surfing the net I found some useful links and I will post the whole procedure about installing vmware and bridging the network cards.

First I have to say thanx to bodhi.zazen, fjgaude, altonbr and Kokopelli about some useful help about installing vmWare, I'm just gonna re-write their lines...

Ok, so we start installing vmWare. We need to download the vmWare server from here  

VMWare server : [http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

Dont forget to get installation codes: 

VMWare serial number : [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

and you will need this update with  support for the wireless cards:

[http://www.mediahouseteam.com/vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz](http://www.mediahouseteam.com/vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz)

Since now you got this, Place them both in the same directory ( I use ~/src/VMWare) and extract.

To install: 

```
cd ~/src/VMWare
tar xzf VMware-server-1.0.5-80187.tar.gz
tar xzf vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl
```

Select defaults. When you get to :

```
Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]
``` type [COLOR="Red"]NO.[/COLOR]

Now run the update:

```
cd  ~/src/VMWare/vmware-any-any-update-116-K2.6.24-WirelessBridge
sudo ./runme.pl
```

You will be asked if you wish to run "/usr/bin/vmware-config.pl" , this time answer "yes" (default is no).

Now, when it comes to networking, I used this :

```
Do you want networking for your virtual machines? (yes/no/help) [yes] yes

It will ask you that you have multiple network adapters, type wlan0 (to bridge wlan0 with the adapter of the vmWare).

The following bridged networks have been defined:

. vmnetx is bridged to wlan0 (x is the number of the vmnet adapter)

When it asks to setup network for other adapters just click no.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] no

Do you want to be able to use host-only networking in your virtual machines?
[no] no
```

At the end just enter the serial number.

And this is not the end. You need to make some post-install configuration.

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

And for the 64bit users:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

Now you can start the vmWare server. If you dont know how to install your windows cd, try this post, very useful:

```
http://ubuntuforums.org/showthread.php?t=183209
```

And dont forget to set an IP address for the adapter in windows network configuration so the bridging will work.

Cheers!

---

### Post by lib99 on 2008-08-14
Recently I had to rebuild my vmware server. The last post previously helped me get the wireless adapter working with vm.

Any idea where to find that wireless bridge update now? Link is dead now and I can't find the file on my sytem.

---

