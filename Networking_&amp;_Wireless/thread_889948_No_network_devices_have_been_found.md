---
title: "No network devices have been found"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by diwas on 2008-08-14
Hi,
Iam connected through ethernet card and ADSL modem. The internet works fine...but the problem is...on the top panel the "network manager" says "no network devices have been found" on left clicking it.

Yes, the internet works fine..no doubt about it...but why is this thing shown even though i have a network device??

Here are some outputs on the terminal:
```

diwas@diwas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:46:01:4e:e3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:46ff:fe01:4ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5149975 (4.9 MB)  TX bytes:860476 (840.3 KB)
          Interrupt:20 Memory:ff8ffc00-ff8ffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137925 (134.6 KB)  TX bytes:137925 (134.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.1.56.40  P-t-P:10.1.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5042717 (4.8 MB)  TX bytes:734649 (717.4 KB)

```

```

diwas@diwas-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)

```

---

### Post by Proot on 2008-08-14
Hi!

I've developed the same issue.
I've got 8.04.1 386 installed into a VM on a Vista host. The networking was all fine and showed in the network manager.
I then installed the kubuntu-desktop package, rebooted and then logged into kde and noticed the error in the network manager.
I still had my windows hat on so i rebooted and logged into kde but the error was still there so I logged into gnome. There i found the situation to be the same.
A quick search on the forums led me to check my /etc/networks/interfaces file and there was no entry for eth0, so I added 

auto eth0
iface eth0 inet dhcp

to that and restarted the networks (sudo /etc/init.d/networks restart) 

The network manager still reported no network connections but i could ping the bbc (ping bbc.co.uk) so i knew that the interface was now working again.

A reboot later and it still reported the same thing. I could still ping the bbc/google. Firefox (FF) appeared to be less happy, it wouldn't connect to the net. It was in offline mode despite there being a working network. unticking "File>work offline" has made FF work,but needs to be done each time I reboot. Same deal for evolution. Pidgin doesn't appear to have an offline mode but it doesn't work and i can't see anywhere to make it work. 

Anyone got any bright ideas?

@diwas did you do anything to the system before you noticed this was the case? do you have the same issue with applications?

---

### Post by diwas on 2008-08-14
Yes, with FF. It is so damn annoying to uncheck work offline every time.

But pidgin works fine for me...

And no, i didnt go and change anything of the system before this problem came up because it persisted since the time i installed 8.04.

For pidgin, try this(it works for me...but is a stupid idea..anyways):
> 
First open pidgin and set it to "Offline". Then set the status to "Available" or anything like "invisible"...After few seconds you will notice that a plug type of animation is shown saying "connecting". And if your internet is working well enough, you will be connected.



So, anyone has any idea about the network problem?? Coz this really freaks me (oh sorry us lol) out.

---

### Post by diwas on 2008-08-16
bump

---

### Post by diwas on 2008-08-19
bump

---

### Post by diwas on 2008-08-22
BTW when i connect the same router through USB, it recognizes the network device....

---

### Post by diwas on 2008-08-23
bump

---

### Post by diwas on 2008-08-30
bump!!!!!!
hehe.

---

