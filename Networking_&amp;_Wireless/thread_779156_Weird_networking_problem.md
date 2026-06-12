---
title: "Weird networking problem"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by agger on 2008-05-02
The last couple of days I have had this very weird problem with my wired network card:

When booting the computer, Network Manager detects the card and I get an IP address.

After a couple of second's use of the Internet connection, the connection apparently "times out" or at least expires; during normal browsing, I'm typically able to read the first page I load but not the second. When reading mail, it usually manages to download only about half my mail before the connection dies.

I can then right click Network Manager, uncheck  "Ensable Networking", wait a sec, check "Enable Networking" once again, which makes it connect and get the computer an IP address, etc ... whereuopn I once again have a few second's worth of Internet connection.

So what did I do? Nothing, as far as I know; the system comes from a clean Gutsy install dating from November, recently (after release) upgraded to Hardy by the Upgrade Manager. The day it went wrong I installed some KVM extensions, found out KVM can't run on my CPU as it doesn't support virtualization optimization, and ended up simulating a Debian-derived system in Qemu instead. AFAIK that's the only things I've done the last days which *might* affect the kernel and its drivers.

Nothing appears to be wrong with the hardware - if I boot into windows, wired networking works just fine.

This is the output from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:53:10:5f  
          inet addr:84.238.94.107  Bcast:84.238.94.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe53:105f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2304 errors:0 dropped:2 overruns:0 frame:2
          TX packets:1672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1275408 (1.2 MB)  TX bytes:198555 (193.9 KB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213215 (208.2 KB)  TX bytes:213215 (208.2 KB)

```

and this is the network card's entry in lspci:

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

Any ideas/any suggestions as to how one might solve this problem?

---

### Post by Trog on 2008-05-02
I've been having similar problems. The latest fix I've tried is shown on this link here [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836). So far so good. It's stayed up over an hour now.

---

### Post by agger on 2008-05-02
> **Trog said:**
> I've been having similar problems. The latest fix I've tried is shown on this link here [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836). So far so good. It's stayed up over an hour now.

Thanks a lot! I'll try the fix and see if it works.

---

### Post by agger on 2008-05-02
> **agger said:**
> Thanks a lot! I'll try the fix and see if it works.

Alas, it didn't. The fix recommended in that bug report is this:

```

# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

```

And alas, it made no difference :-(

As I said, this problem occurs after upgrading to Hardy ... the computer has an IP address according to ifconfig, and NEtwork Manager thinks everything is OK, but there's no connection.

---

### Post by Trog on 2008-05-02
Oddly enough I was just about to say the same.

---

### Post by agger on 2008-05-03
> **Trog said:**
> Oddly enough I was just about to say the same.

OK, I don't know how to solve this and ordinary users should never have to put up with this kind of issue, so I reported a bug: 

[https://bugs.launchpad.net/ubuntu/+bug/226026](https://bugs.launchpad.net/ubuntu/+bug/226026)

Hopefully, the issue will get resolved soon.

---

### Post by Trog on 2008-05-03
I know how you feel, it's really frustrating.

'fraid I got so fed up I reinstalled from the CD (I had originally upgraded from Gutsy). Happily my home directory is on it's own partition and so it's easy it import. So far so good, so far so good...
Splat! it's fallen over again. I know this dist works, I have it on a Dell at work so this has to be a hardware issue. I'm sorry, but the Heron is beginning to look more and more like Vista, great if you've got the right hardware.

---

### Post by Trog on 2008-05-30
If you're still having problems, take a look at this link [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) it may help.

---

