---
title: "ASUS P5L-VM Ethernet Controller: Unknown Device"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by jtreg on 2007-10-04
Hello, I have had problems installing Ubuntu 6.06 on my new Asus desktop pc. I ran lspci and go the message
Ethernet controller: Unknown device 1969:1048 (rev b0)

I dont really know what to do from here. I have the CD that has Linux drivers but am not sure what to do..
Any help will be most apppreciated.

Thanks

James

I also ran ifconfig -a and got this:
lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr:  ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:71 errors:0 dropped:0 overruns:0 frame:0
     TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:5660 (5.5 KiB) TX bytes:5660 (5.5 KiB)

sit0  Link encap:IPv6-in-IPv4
        NOARP  MTU:1480 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by noob12 on 2007-10-04
You should probably download and build a recent version of the atl1 driver.

[http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)

I strongly suggest 2.0.7 unless you like having your mac address randomly changing.

---

### Post by jtreg on 2007-10-05
Thanks ... now I have added make it should work but I have no kernel source and the package manager wants a network connection (I need the kernel source  so that I can compile the driver!) Bit of a catch 22 situation... how do I progress?

James

---

### Post by noob12 on 2007-10-05
I haven't built that specific driver before, but typically you would only need the right kernel headers.  


If you have a USB jump drive or a shared partition you can download packages from  another networked host via the web interface at [http://packages.ubuntu.com](http://packages.ubuntu.com) ; i.e. navigate to the package you want download it using the browser and transfer them onto the box.

You will also need the build-essential (meta-package) which you should be able to get off the installation cd-rom.

I'll try building the atl1 from sourceforge later today; maybe I can help step you through that.

Note that if you haven't got a real need for long-term-suport on the 6.06 release, then Feisty has version 2.0.6 of this driver which I believe will work for you though it has the pesky random MAC addr problem on ASUS boards; I believe it is possible to workaround that.  Gutsy (still in pre-release, but expected out this month) has 2.0.7.  If you're brave you can try a pre-release version of that, then upgrade to the real release when it's out.

---

### Post by noob12 on 2007-10-09
Sorry for the late response.  I somehow lost track of this thread.  I did the driver build on Feisty and it is a piece of cake.  However, the source states a dependence on 2.6.20 so I doubt it will build on Dapper at all.  I recommend that you upgrade to Feisty and replace the 2.06 version that comes with Feisty with the 2.07 version of the driver downloaded from Sourceforge (or wait for Gutsy release which will have 2.07).

---

