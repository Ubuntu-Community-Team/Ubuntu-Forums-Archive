---
title: "WG111v3 USB Wireless adapter Problem"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Asparatame on 2007-10-27
Hi

I've bought a WG11v3 usb adapter and I've looked up some guides on how to install it... the problem is that the only guide I've found was for the WG111v2 adapter and the first problem I have is that I can't find any drivers for v3.

As a beginner on linux, I don't know at all how to work stuff like this out. So if anyone that have been able to install v3 of the WG111 usb adapter, would be kind to let me know how to do, that would be appreciated. Of course, if anyone that have not installed it but still know how to do, they're also welcome to inform me on how to do it.

---

### Post by Lambert on 2007-10-28
With the device plugged in, open a terminal and type the following command. Post the out put here. 

```

sudo lsusb -v

```

---

### Post by jazzcat on 2007-10-31
I just got one of these yesterday, too.  Here's some relevant output:

/proc/bus/usb/devices has, among other things, this text:

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0846 ProdID=4260 Rev= 2.00
S:  Manufacturer=Manufacturer_NETGEAR
S:  Product=NETGEAR WG111v3
S:  SerialNumber=001B2F35F019
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 9 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=06(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=89(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0a(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0b(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0c(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

And lsusb creates this output:

Bus 001 Device 004: ID 0846:4260 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000

I was hoping to not have to use ndiswrapper, but I can't find the identifier for the chipset on this adapter.   Yikers!

Cheers,
-JC

---

### Post by misterclaw on 2007-10-31
I just bought my Netgear WG111v3 and I have no idea what to do either.  There doesn't seem to be any documentation for it.

---

### Post by jazzcat on 2007-10-31
Ok, there are a number of other threads on this, but the gist of the matter is that you'll need to use ndiswrapper.  I tried the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

But I'm stuck because I keep getting the "no versions of ndiswrapper detected" error, even after I modprobe the kernel module.

It's also a big pain in the butt to get the drivers, because you have to have windows to run their install utility, as they don't provide the .INF files on the CD.

I think I'm going to return this adapter to the store.

---

### Post by jonathanpeter on 2007-11-17
I've installed a WG111v3.  See my post on how to do it:

[http://ubuntuforums.org/showthread.php?t=615471](http://ubuntuforums.org/showthread.php?t=615471)

---

### Post by Maricaibo on 2008-01-10
Followed all instructions to install ndiswrapper. My Gutsy machine sees to USB NIC and using iwlist wlan0 scanning I can see my and other wireless networks. But I can't get an IP address at all. 

Tried disabling WEP on my router, no luck. Tries using the WEP key in ascii AND in hex, no luck.

Now what? Anyone have suggestions? 

I ordered this Netgear WG111 v. 3 USB card because the Wiki list showed this USB nic working out of the box- NOT..

I sure could use some help here!

---

### Post by stooshbunutu on 2008-03-23
Here is my tutorial on this very matter:

[http://ubuntuforums.org/showthread.php?t=732827]("http://ubuntuforums.org/showthread.php?t=732827")

For additional Ubuntu Support see my new help site - [www.helpbuntu.iwarp.com]("http://helpbuntu.iwarp.com/") - Happy surfing!

---

### Post by the goat boy on 2008-07-09
I am at my wits end with this matter

i have tried countless versions of ndiswrapper and many drivers all with the same result. 

no connection. 

my problem is i have a 64bit machine, and for the life of me cannot find a driver for this.

is there anyone that can help me??

i've tried the vista 64  versions, but these do not work,

ive tried the 32 bit windows versions. no good

ive even downloaded some realtek drivers but no joy there either.

its problems like this that stop the masses from getting on board linux

the wireless support is just abysmal

---

