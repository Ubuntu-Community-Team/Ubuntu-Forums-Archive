---
title: "Having Trouble With  Wired Internet Connection In Hardy"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Garretonfire on 2008-09-07
I have been trying to get the internet up and running on my laptop, which is dual booting Windows Vista and Hardy Heron Ubuntu for quite a while now. I was asking for help on an different board, but eventually the member helping me couldn't figure out what else to do, so he sent me here.

Here is the topic where I was asking for help, so I don't have to retype everything out again [(topic)]("http://www.zybez.net/community/index.php?showtopic=1111995").

I just find it weird that I can't even get a wired internet connection to work in Hardy. I did a quick look around for some kind of guide, but I couldn't see anything. I think that once I can get my wired connection up and running, I will be able to follow guides and whatnot to get my wireless running as well. However, if there's some way of getting both to work at the same time, that would be excellent.

Thanks!

---

### Post by Garretonfire on 2008-09-07
bumpity bump

---

### Post by lost_soul on 2008-09-07
what kind of connection do you have ? do you have it setup to a router and should work fine by plugging the cable from the router to the ethernet port on the laptop? or do you need to setup a PPPOE connection ? maybe static IPs we need to know your problem so we can try to help you ,

btw when you put ifconfig in the terminal what does it give?

---

### Post by cariboo on 2008-09-08
also could you post the output of:

```
sudo lshw -C netwotk
```

Jim

---

### Post by RedPandaFox on 2008-09-08
I have the same problem same situation and im running it on an Asus M5 laptop, brand new, any help is much appreciated, no wireless or cabled connection, it wont even detect them.




[SIZE="1"](By the way garret, rune scape forums? :P)[/SIZE]

---

### Post by Iowan on 2008-09-08
I noticed from your link that you're connecting (trying...) via DHCP.  What is (supposed to be) the DHCP server? Router, modem?  If modem, it may need to be power cycled to pick up the MAC address.

---

### Post by Garretonfire on 2008-09-09
> **lost_soul said:**
> what kind of connection do you have ? do you have it setup to a router and should work fine by plugging the cable from the router to the ethernet port on the laptop? or do you need to setup a PPPOE connection ? maybe static IPs we need to know your problem so we can try to help you ,

btw when you put ifconfig in the terminal what does it give?
I have a desktop that is connected to the internet via an ethernet connection. I unplugged the ethernet cable from there and plugged it into my laptop; it worked on my desktop but not laptop.

(see bottom of post for ifconfig info)

> **cariboo907 said:**
> also could you post the output of:

```
sudo lshw -C netwotk
```

Jim
See bottom of post.

> **Iowan said:**
> I noticed from your link that you're connecting (trying...) via DHCP.  What is (supposed to be) the DHCP server? Router, modem?  If modem, it may need to be power cycled to pick up the MAC address.

I have a modem that is connected directly to a wireless router. From the router stems three ethernet cables that go to various desktop computers throughout my house. All desktops have perfect access to the internet via these ethernet cables, but when I take one of them and plug it into my laptop, it doesn't work.

Here's the terminal information you asked for:

```

eth0      Link encap:Ethernet  HWaddr 00:1b:38:73:57:18  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:220 Base address:0xa000 



eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:73:57:18  

          inet addr:169.254.3.185  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:220 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:152 errors:0 dropped:0 overruns:0 frame:0

          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:7848 (7.6 KB)  TX bytes:7848 (7.6 KB)

```

```

PCI (sysfs)

```

---

