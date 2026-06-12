---
title: "wireless connection established, still no internet"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by karvec on 2007-09-06
I was hoping to solve this without having to post anything, but I haven't yet, so here goes...

I have a nice new laptop, and at home I can connect to my wireless network just fine, even though the router is a crappy one.  But, at school, it's a different story.

I have tried, or at least I thought I tried disabling IPV6, with net-pf-10 off instead of net-pf-10 ipv6, and I've disabled it in firefox, but no cigar.

The wireless connection connects, but I cannot get online or do anything.  I have a screenshot of one of the lab computers, all running Microsoft, and I've seen everyone else's laptop is also using Windows...

I don't want to use Windows!!!

(I'm at home right now, will be at school again in an hour)

My settings closely reflect the ones on the workstation computers, however mine are obviously the set IP and gateway, but the DNS settings are all the same.  I do not use Firestarter, by the way...

(Feisty Fawn 7.04 and an Acer 5630-6288)
Intel Pro Wireless

I have also tried an ethernet connection to no avail, and I'm really stumped, so I'm hoping someone can suggest something.  Thanks in advance!!!

~~karvec

---

### Post by Megaqwerty on 2007-09-06
Are you using the nm-applet to connect? (The tray applet)
Are you getting an IP address from the network?

---

### Post by karvec on 2007-09-06
> **Megaqwerty said:**
> Are you using the nm-applet to connect? (The tray applet)
Are you getting an IP address from the network?

yes, and yes..  Using network manager, it sees a network, I click on it(Or it connects on startup), and I do get an IP.

---

### Post by Megaqwerty on 2007-09-06
Can you describe in more detail what errors you get when trying to connect to the internet?
Can you ping out? ```
ping google.com
```

---

### Post by karvec on 2007-09-06
It said 

```

$ping google.com
ping: send failed

```

I believe, at the moment I am at the school yet I'm not around a wireless network...  So, I will post more info as soon as I can.  I did some editing of my modprobe.d/aliases, and maybe that will fix things, I removed some stuff that I had entered following the IPV6 tutorial to turn it off.

So!

It would not connect at all.

Well...  It is connected, the wireless is connected, but I cannot connect to anything else.  Can't wait until Gutsy comes out, the final release, really looking forward to all the power management options in the new kernel, and the supported devices...

---

### Post by Megaqwerty on 2007-09-06
That is quite odd...out of curiosity, what does: ```
ifconfig | awk '{print $2}' | grep addr
``` give you?

---

### Post by karvec on 2007-09-06
```

karvec@karvec-laptop:~$ ifconfig awk '{print $2}' grep addr
{print $2}: Unknown host
ifconfig: `--help' gives usage information.


karvec@karvec-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:D4:D5:8C:A9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:C7:01:54  
          inet addr:10.13.111.130  Bcast:10.13.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:3 dropped:51 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11027 (10.7 KiB)  TX bytes:6582 (6.4 KiB)
          Interrupt:19 Base address:0xe000 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1000 (1000.0 b)  TX bytes:1000 (1000.0 b)


```

---

### Post by karvec on 2007-09-06
Umm, first one did not display anything.  Just ifconfig did, but I do not know what the first ifconfig awk whatever was supposed to do, so I just typed in ifconfig.

Home again, won't be there tomorrow, but will have to wait till Tuesday...  Really disappointed in the fact that this was one of the reasons that I wanted a laptop.

Still looking for a fix, but if nothing works, I can wait for Gutsy.

---

### Post by kevdog on 2007-09-06
Lets just start at the top and get some background info

Can you post the following:
lspci -nn
lshw -C network
iwlist scan

That should cover the basics.  And if you could tell us about your networking card that would be great.

---

### Post by karvec on 2007-09-06
> **kevdog said:**
> Lets just start at the top and get some background info

Can you post the following:
lspci -nn
lshw -C network
iwlist scan

That should cover the basics.  And if you could tell us about your networking card that would be great.

You mean at home or at the college?  Because it'll be a coupla days before I go back to college...  And all I know about my wireless card is I'm using the restricted Intel Pro Wireless 3945 Network Connection driver for it...

But, however...

```
karvec@karvec-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc Unknown device [1524:0551] (rev 01)
karvec@karvec-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:c7:01:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.70 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0100000-d0100fff irq:19
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:d5:8c:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
       resources: iomemory:d0000000-d0001fff irq:21
karvec@karvec-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:3F:A0:51:39
                    ESSID:"2WIRE086"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
                    Extra: Last beacon: 36ms ago

karvec@karvec-laptop:~$ 

```

That's all from home...  Will post school's when I am there once again.

---

### Post by kevdog on 2007-09-07
Obviously you stated you can connect to your home unencrypted router just fine without a problem.  Does your school's LAN use WEP or WPA or do you know??

---

### Post by Megaqwerty on 2007-09-07
> **kevdog said:**
> Obviously you stated you can connect to your home unencrypted router just fine without a problem.  Does your school's LAN use WEP or WPA or do you know??

He can connect, get an IP, but he can't ping out.

> Umm, first one did not display anything. Just ifconfig did, but I do not know what the first ifconfig awk whatever was supposed to do, so I just typed in ifconfig.

You didn't enter the first command correctly, it included **|** symbols, which are called pipes. That's alright though, as the commands following ifconfig were just to strip out the extra info I didn't need to know. It's alright though, I have the info I needed. 

It would appear that, yes, you are indeed getting an IP address, and you are also connected to the network, as you stated before. The thing I would try to find out, is whether or not your school uses a proxy. It's the only thing I can think of. It's primarily a Windows network, so they probably have it set up so that Windows will automatically use it, and thus seemingly works without any changes to the system. 

I would find out by your own means, or by asking an Admin at the school if they are using a proxy, and if so, set up Ubuntu to utilize it.

I'll be interested to know the results,

Megaqwerty

---

### Post by karvec on 2007-09-07
They don't use a proxy that I know of, and I already talked to someone there...  It's an unencrypted or open network, I talked to one of the computer center guy, he thought it was my DNS settings, but those automatically set up and were consistent with the school's...  I'm wondering if there is some hidden DNS settings somewhere not stored in NM?

What difference would a proxy make?  Wouldn't my computer automatically route through that, as it's server-side?  And shouldn't I be able to get SOMEWHERE with a traceroute instead of just everything not being found?  (Traceroute is in the graphical tools...)

Anyways...

Thanks for all your feedback, I'll wait for more, and hopefully get it working some day.

---

### Post by Megaqwerty on 2007-09-07
I'm stumped...this *should* be working...as for the "Hidden DNS settings," the file:  ***/etc/resolv.conf*** contains the DNS info.

Good luck,

Megaqwerty

---

### Post by karvec on 2007-09-11
Installed Gutsy Gibbon Tribe 5, and at first wireless didn't work (The intel 3945 driver), but plugged it into the router and updated it, wireless started working again.  Read a similar thread about the wireless not working with the gnome network manager, but I figured the updates would fix it, and they did.  So, the next thing to do will be to test this at school.  Will post with updates!!


EDIT:  Well, went to school and tried to connect, same thing--  connected fine, just no internet.

I can't ping the DNS servers, it says "send failed"...  So, I don't know.  Maybe it's just the OS and not me?  They've got all Windows and Macs--  but mostly Windows.  I've seen people with iMacs connecting just fine, but I don't know.  *shrugs*

---

### Post by iloveketchup on 2007-09-12
i'm having the same problem as this.  I'm using VMware on a windows xp box however i think that has little or nothing to my problem.

[LIST]
[*]i can get to google based pages in firefox
[*]I can use gaim
[*]i get an ip from my router
[*]i can ping opendns.org dns servers
[*]my /etc/resolv.conf file seems to be okay.  I just put in the 2 opendns.org ip's for nameservers
[*]i commented out # /modprobe.d/aliases (# alias net -pf -0 ipv6) - i read to try disabling ipv6 completely
[*]in firefox i toggled "network.dns.disableIPV6" value to "true" from "false".  This should disable IPV6 in firefox.  I got there by typing in "about:config" in the url box and using the "filter"
[/LIST]

I don't know exactly what to check.  This is a fresh install of ubuntu.  i didn't see anything in the installer that i could have removed these options.  I don't seem to be able to use the apt-get feature because of this mess.  I can't believe that on a fresh install that i get this problem.  It's kind of rediculous.  Could my parents ever install this and use it as a primary OS?  

[-X

Thanks for any help in advance.

---

### Post by kevdog on 2007-09-12
From your school can you post 
route -n

---

### Post by iloveketchup on 2007-09-12
not sure if the question was for me or the other guy but:

(11:33:16 AM) Me: Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by karvec on 2007-09-13
> **kevdog said:**
> From your school can you post 
route -n

Will post tomorrow--  I removed the gnome network manager and installed wicd, maybe this will straighten some things out......

---

### Post by medad on 2007-09-13
As I was surfing around trying to find an answer for you, I came across several threads with similar issues.  Two of them claimed to work okay after using opendns.com.  Does anybody know anything about this website?

---

### Post by karvec on 2007-09-13
Opendns is just that, more DNS servers.  I tried using them at one point, to no avail.  I will get the IPs, and try them again....

Maybe it's an operator error.

---

### Post by kevdog on 2007-09-13
what happens with

png 72.14.207.99

thats google

---

### Post by iloveketchup on 2007-09-13
> **kevdog said:**
> what happens with

png 72.14.207.99

thats google

seems like a high packet loss but:

(3:15:25 PM) Me: kenny@Ubuntu:~$ ping 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=243 time=42.1 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=243 time=41.4 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=243 time=40.4 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=243 time=47.5 ms
64 bytes from 72.14.207.99: icmp_seq=6 ttl=243 time=43.4 ms
64 bytes from 72.14.207.99: icmp_seq=9 ttl=243 time=51.2 ms

--- 72.14.207.99 ping statistics ---
9 packets transmitted, 6 received, 33% packet loss, time 8009ms
rtt min/avg/max/mdev = 40.440/44.393/51.295/3.831 ms
kenny@Ubuntu:~$ 


wonder if my ipv6 still isn't disabled?  thanks for any ideas.

---

### Post by karvec on 2007-09-13
route -n displays 

10.13.10.0  0.0.0.0 255.255.0.0 U 0 0 0 eth1

It doesn't display a gateway, could that be the cause?

I actually ran into someone I had a class with last year, and they were also using ubuntu and had the same problem.  Could it just be the operating system itself, because it's unsupported?

He was running 7.04 also, and had only had his for several days, an IBM.

I would go back to trying Windows, but seeing as I don't have it on my computer anymore, and I really don't want to use Windows AT ALL, I'd rather get wireless working on this.

He said he had the same problem at internet cafes, such as Caribou and Starbucks, something I have not yet tried.  Is this just in this school?  And is there a fix?

Grr.

---

### Post by rudeboyskunk on 2007-09-13
Well, if you have to go back to Windows, do Win98...the only good one.

But I had this problem too once.  Could get an IP and everything, but no internet.  The way I ended up having to solve it was by going back to Breezy (or Edgy, can't remember).  Wireless connected and got me on the internet.  Dunno why, but there ya go.

---

### Post by karvec on 2007-09-13
Finally posting some stuff from the school....


```


$sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:c7:01:54
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=10.13.113.129 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:d5:8c:a9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s


$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:D5:8C:A9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:C7:01:54  
          inet addr:10.13.113.129  Bcast:10.13.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:d2ff:fec7:154/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:1 dropped:1 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18701 (18.2 KB)  TX bytes:6926 (6.7 KB)
          Interrupt:19 Base address:0xe000 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KB)  TX bytes:1200 (1.1 KB)




$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:74:D2:D2:F0
                    ESSID:"NccWireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 8ms ago

$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.13.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1

```

---

### Post by kevdog on 2007-09-14
Yes you need a default gateway which could be your problem

To add the gateway try the following

```
sudo route add -net 10.13.0.0 netmask 255.255.0.0 gw x.x.x.x eth1
```

Now the trick is to figure out the gw address in your school's network. You might have to ask someone for this -- or look at a windows computer to find the gateway.

---

### Post by karvec on 2007-09-14
thanks, I will definitely do that...  I have a couple of screenshots on my comp from windows computers, both the computer lab and laptops.  So I will use that gateway and let you know how it turns out.

---

### Post by karvec on 2007-09-20
Well, finally tried again at school.  Used the route that was posted, and it said the IPs weren't the same or somesuch, apparently trying to force a gateway with a different IP as your address is a no-no.

Will post friend's ipconfig as well as error message for route when I get home.

*EDIT*

Added picture, and it's the same throughout the computer lab.  However, when using route it displayed this error:

```

$ sudo route add -net 10.13.113.126 netmask 255.255.0.0 gw 10.10.10.253 eth1
route: netmask doesn't match route address

```

Is there a way to force it to accept that?

---

### Post by kevdog on 2007-09-20
The settings that I wrote may be different than your current situation.  You will need to substitute your appropriate values.  Im glad at least you have check out a few different computers to figure out the correct values.

---

### Post by kevdog on 2007-09-22
What if you just add the following:

sudo route add gw 10.10.10.253 eth1

And then can you post the route -n statement after this?

---

