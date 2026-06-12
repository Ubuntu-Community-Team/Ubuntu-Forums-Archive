---
title: "Learning how to fix things - Wired LAN not working in 13.10"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by nitsujz28 on 2013-12-30
Hello,
I'm a new Ubuntu user; I'm having problems right off the bat, but I'm becoming determined!  Installation of 13.10 seemed perfect except for not installing updates due to no internet connection.  My AT&T Uverse internet service works properly wired and wireless on my old Windows XP laptop.

_New, freshly built computer:_
Motherboard - Gigabyte GA-990FXA-UD3
LAN - Realtek 8111E (integral on mobo)
CPU - AMD FX-6300
RAM - DDR3 GSkill something 8gb
Note - This entire computer was virgin when Ubuntu was installed, no other software/drivers/etc have touched it.
Note2 - The LAN port has its green LED on signifying 100 Mbps data rate.  I've seen the orange activity LED flicker but it's rare.

[U]What I've tried:
[/U]- Ubuntu 13.10 amd64 defaults, no good.
- Ubuntu 12.04 LTS amd64 defaults, no good.
- back to 13.10 amd64 with static IP.  I picked a few different IPs outside of my router's IP range.  I used the same DNS Server, Subnet Mask, and Default Gateway numbers that my Windows XP computer works with.  It says it's connected, it shows up/down arrow icon, but Firefox gets nowhere (tried websites and my 192.168.1.1 router address).  No good.
- Yes, I turned it off and back on again between most changes haha..
- Went to Realtek and got "[FONT=Arial]LINUX driver for kernel 3.x and 2.6.x and 2.4.x" per somebody else's forum post.  Extracted this "r8168-8.037.00" folder from USB stick and ran the "autorun.sh".  It completed its thing, but still no good.
- Search more forum posts, no good.
- Make this forum post.  TBD.

I want to fix the problem of course, but I also want to learn what is required to fix this.  How do I go about troubleshooting this myself?  In Windows XP I can figure it out myself usually, and I'd like to have that ability in Ubuntu.  What info must I share?  What must I do?

Help/guidance is much appreciated of course!  I'll tell a bad joke in return if somebody can help me fix this.[/FONT]:p[FONT=Arial]

Justin[/FONT]

---

### Post by nitsujz28 on 2013-12-30
I don't know if this ifconfig output is useful, but I've been seeing it requested in other posts.  So when in doubt:

```
justin@Europa:~$ ifconfig

eth0    Link encap:Ethernet  HWaddr 74:d4:35:09:a8:6f
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe09:a86f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1394 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:832 (832.0 B)  TX bytes:0 (0.0 B)
          Interrupt:74 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:115146 (115.1 KB)  TX bytes:115146 (115.1 KB)


```

---

### Post by chili555 on 2013-12-30
Let's be sure we have the right hardware associated with the right driver. Please open a terminal and run and post:```
lspci -nn | grep 0200
lsmod | grep r8
```Let's see what settings you have in Network Manager for the device:```
nm-tool
```And finally:```
ping -c3 192.168.1.1
```

---

### Post by Iowan on 2013-12-30
> **nitsujz28 said:**
> 
 I'll tell a bad joke in return if somebody can help me fix this.There's motivation... :^o

A few things to check in a terminal (CTRL-ALT-t):
```
ifconfig
sudo lshw -C network
ping <router address>
```


Oops - outtyped again.
Most of this information will be revealed by nm-tool (new command for me...)

---

### Post by nitsujz28 on 2013-12-30
Thank you both for responding; here is the output from the terminal.
First:
```

justin@Europa:~$ lspci -nn | grep 020005:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
justin@Europa:~$ lsmod | grep r8
r8168                 261295  0 



```

Second:
```
justin@Europa:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Ethernet connection 2jjf] -------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        74:D4:35:09:A8:6F


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.171
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.7.254


```

Third:
```



justin@Europa:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.171 icmp_seq=1 Destination Host Unreachable
From 192.168.1.171 icmp_seq=2 Destination Host Unreachable
From 192.168.1.171 icmp_seq=3 Destination Host Unreachable


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3
```


Doing this is interesting though I've struck no eureka moment.  Btw, when I unplug the cable from the port it immediately notifies me of the disconnect, so it is at least responsive to that.
Thoughts?

Justin

---

### Post by chili555 on 2013-12-30
> DNS:             192.168.7.254Who is this?? Is this the same as on some other machines on your network? I would rather see these nameservers: 8.8.8.8 and 192.168.1.1. Please amend Network Manager to fix it unless you can assure me it is valid.

Can you also please check other computers on the network and be sure the gateway is 192.168.1.1 and not 192.168.7.1 or 192.168.0.1 or some other?

May I see:```
cat /etc/network/interfaces
```

---

### Post by nitsujz28 on 2013-12-30
DNS: 192.168.7.254 came from my Windows XP laptop, when I checked "ipconfig /all" in command prompt.  Otherwise, I know nothing about it.  I called my ISP to inquire about DNS but their computers were down... ironically.  My service still works on this XP computer.
I edited the static IP wired connection to try 8.8.8.8 and 192.168.1.1 as the DNS with same results, no good.  Should I even be trying static IP?  It at least claims a connection whereas DHCP does not ever connect so far.

Gateway is same on both the XP computer and Ubuntu, 192.168.1.1.

Here is the output you asked:
```

justin@Europa:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

I'll assume my confusion is normal.  

In the display from nm-tool, should Driver be r8168?  I was sort of expecting r8111 or similar due to the LAN port Realtek 8111E.  hmm..

---

### Post by chili555 on 2013-12-30
The driver is correct. Sometimes....well, almost always, the model name and driver name are unrelated.

What does ipconfig /all suggest the IP address and gateway are in Windows?

---

### Post by nitsujz28 on 2013-12-30
Here is info from my Windows XP laptop that does work on this internet connection wired and wireless, currently wireless.  My router says it asignes DHCP IPs from 192.168.1.100 to .149.

```
Microsoft Windows XP [Version 5.1.2600](C) Copyright 1985-2001 Microsoft Corp.


C:\Documents and Settings\Justin>ipconfig /all


Windows IP Configuration


        Host Name . . . . . . . . . . . . : Cornhoolio
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter Wireless Network Connection 2:


        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
        Physical Address. . . . . . . . . : 00-14-A5-CE-FE-6C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.121
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.7.254
        Lease Obtained. . . . . . . . . . : Monday, December 30, 2013 5:01:31 PM


        Lease Expires . . . . . . . . . . : Tuesday, December 31, 2013 5:01:31 P
M


Ethernet adapter Local Area Connection:


        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-16-D3-13-B9-63


C:\Documents and Settings\Justin>
```


This motherboard is brand new like I said, so is there a way to check the port separate from Ubuntu?  From BIOS?  I will search info regarding this also.

Again, I certainly appreciate help!

Justin

---

### Post by chili555 on 2013-12-31
First of all,whether you are trying to connect with DHCP or static is, assuming the numbers are correct, immaterial. Likewise, the people who attribute the problem to Network Manager and install Wicd. Usually, those steps are a blind alley. The underlying issue remains.

Let's see what's going on under the hood:```
cat /var/log/syslog | grep -e r816 -e etwork | tail -n25
```

---

### Post by nitsujz28 on 2013-12-31
Under the hood looks messy imo, like this:

```
justin@Europa:~$ cat /var/log/syslog | grep -e r816 -e etwork | tail -n25

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...

Dec 31 10:26:58 Europa NetworkManager[704]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Beginning IP6 addrconf.

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.

Dec 31 10:26:58 Europa NetworkManager[704]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...

Dec 31 10:26:59 Europa NetworkManager[704]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]

Dec 31 10:26:59 Europa NetworkManager[704]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.

Dec 31 10:26:59 Europa NetworkManager[704]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]

Dec 31 10:26:59 Europa NetworkManager[704]: <info> Policy set 'Ethernet connection 2jjf' (eth0) as default for IPv4 routing and DNS.

Dec 31 10:26:59 Europa NetworkManager[704]: <info> DNS: starting dnsmasq...

Dec 31 10:26:59 Europa NetworkManager[704]: <warn> dnsmasq not available on the bus, can't update servers.

Dec 31 10:26:59 Europa NetworkManager[704]: <error> [1388503619.651850] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name

Dec 31 10:26:59 Europa NetworkManager[704]: <warn> DNS: plugin dnsmasq update failed

Dec 31 10:26:59 Europa NetworkManager[704]: <info> Writing DNS information to /sbin/resolvconf

Dec 31 10:27:09 Europa NetworkManager[704]: <info> Activation (eth0) successful, device activated.

Dec 31 10:27:09 Europa NetworkManager[704]: <warn> dnsmasq appeared on DBus: :1.57

Dec 31 10:27:09 Europa NetworkManager[704]: <info> Writing DNS information to /sbin/resolvconf

Dec 31 10:27:19 Europa NetworkManager[704]: <info> (eth0): IP6 addrconf timed out or failed.

Dec 31 10:27:19 Europa NetworkManager[704]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...

Dec 31 10:27:19 Europa NetworkManager[704]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...

Dec 31 10:27:19 Europa NetworkManager[704]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

justin@Europa:~$ 


```


I notice that it concerns IPv6 a lot and not IPv4.  Is that significant?  I've done nothing in IPv6 Settings.
Based on info from another thread from a couple years ago, should I blacklist the driver r8169 in /etc/modprobe.d/blacklist.conf?
I'm out of avenues within my own power at this point, so thank you for help!

Have a great new year!

---

### Post by chili555 on 2013-12-31
> I notice that it concerns IPv6 a lot and not IPv4. Is that significant? I've done nothing in IPv6 Settings.It's not really very significant, but you can certainly try setting IPv6 to 'Ignore.' It will lower the message frequency a bit.> Based on info from another thread from a couple years ago, should I blacklist the driver r8169 in /etc/modprobe.d/blacklist.conf?Is r8169 loading?```
lsmod | grep r8
```If not, then no further action is needed. 

I am troubled by this:> <error> [1388503619.651850] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such namePlease see the similar issue here: [http://ubuntuforums.org/showthread.php?t=2193214](http://ubuntuforums.org/showthread.php?t=2193214)  Please post:```
sudo dpkg -s dnsmasq | head -n5
sudo dpkg -s dnsmasq-base | head -n5
```We'll remove the wrong one and hope we have the same result:> Removing dnsmasq possibly solved it.> I'm out of avenues within my own power at this pointNo worries; this is pretty heady stuff and there aren't many here who understand the significance (or lack) of some of these cryptic messages.

---

### Post by nitsujz28 on 2013-12-31
I set IPv6 to ignore, fwiw.

Regarding r8169, last night I added it to blacklist.conf but noticed no change.  Today I removed it, restarted, and ran this:
```

justin@Europa:~$ lsmod | grep r8

r8168                 261295  0  

```

If I understand correctly it means r8169 isn't a problem.


Your next instructions yielded:
```

justin@Europa:~$ sudo dpkg -s dnsmasq | head -n5

[sudo] password for justin:

dpkg-query: package 'dnsmasq' is not installed and no information is available

Use dpkg --info (= dpkg-deb --info) to examine archive files,

and dpkg --contents (= dpkg-deb --contents) to list their contents.

justin@Europa:~$

justin@Europa:~$

justin@Europa:~$

justin@Europa:~$ sudo dpkg -s dnsmasq-base | head -n5

Package: dnsmasq-base

Status: install ok installed

Priority: optional

Section: net

Installed-Size: 616

justin@Europa:~$ 


```

Looks like I do not have dnsmasq and I do have dnsmasq-base?  If this is similar to the link you referenced then that is good, but perhaps my situation is different (they were wireless, I'm wired).  Since dnsmasq-base is installed, can it conflict with Network Manager (fragmented info I picked up from referenced thread)?

---

### Post by chili555 on 2013-12-31
> Looks like I do not have dnsmasq and I do have dnsmasq-base?Correct and that seems to be correct for your situation: [http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict](http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict)> Note that the package "dnsmasq" interferes with Network Manager which can use "dnsmasq-base" to provide DHCP services when sharing an internet connection. Therefore, if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq. If you have a more complicated set-up, uninstall network manager, use dnsmasq, or similar software (bind9, dhcpd, etc), and configure things by hand.You have a simple setup and I don't recommend removal of NM. 

Since it all appears correct, I wonder why the error pops up. May we see:```
cat /etc/resolv.conf
cat /etc/dnsmasq.d/network-manager
```Off for the evening; I'll check back tomorrow.

---

### Post by nitsujz28 on 2013-12-31
Here is the output:
```

justin@Europa:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
justin@Europa:~$
justin@Europa:~$
justin@Europa:~$ cat /etc/dnsmasq.d/network-manager
# Tell any system-wide dnsmasq instance to make sure to bind to interfaces
# instead of listening on 0.0.0.0
# WARNING: changes to this file will get lost if network-manager is removed.
bind-interfaces


```


At any point would you suggest I reinstall 13.10 to start from a clean plate?

I'll be out as well to crack open the new year :P

---

### Post by nitsujz28 on 2013-12-31
This link is from 2011, so possibly outdated advice for my 13.10 release, but do you think it would be worth me going through these steps?  I'm not sure how I could install build-essential without a connection though.
[http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

---

### Post by nitsujz28 on 2014-01-01
OK!  I am posting this from the Ubuntu computer in question, and yes of course I have connection now!  I bought a USB 3.0 Ethernet adapter and it immediately worked.  It was $30 at Best Buy, though I would have bought the $5 PCI Ethernet card at Micro Center if I would have had time to drive there.  

I'm still curious why my motherboard ethernet isn't working..  Hardware problem?  Not sure how to conclude that.  Could it be a hardware address problem?  ifconfig's HWaddr matches the settings for my previous attempted connection.

```

justin@Europa:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d4:35:09:a8:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:945 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1723 (1.7 KB)  TX bytes:0 (0.0 B)
          Interrupt:74 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:05:1b:a3:41:52  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1bff:fea3:4152/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4095138 (4.0 MB)  TX bytes:372387 (372.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146290 (146.2 KB)  TX bytes:146290 (146.2 KB)


```

```
justin@Europa:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ax88179_178a
  State:             connected
  Default:           yes
  HW Address:        00:05:1B:A3:41:52

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.7.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        74:D4:35:09:A8:6F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



```

---

### Post by r3dd on 2014-01-01
I am sure this has already been covered, but;
```

lspci | grep Network
dmesg | grep 'Ethernet'

```

The first command will tell you what the NIC is and the second will tell you what driver is being used. Make sure they match up.

Also, are you using static or DHCP? If you are using static, try setting the DNS server to your router's IP. You could also just try setting it to DHCP to see if that works.

Another thing you could try, go in to your router and set your lease time to 0, then reboot the router. That way your router releases the IP addresses faster instead of keeping them associated in memory. I recently reconfigured my entire home network and this was what I had to do in order to get my router to recognize the constant changes as I set up all of the systems with static IPs.

Once you get the networking set up and functional, set the lease time back to 1440 (one day).

---

### Post by nitsujz28 on 2014-01-02
Thank you for responding!  When I enter "lspci | grep Network" into terminal nothing happens, it just gets ready for a new line command.  If there was a typo I don't know enough to spot it.

However "dmesg | grep 'Ethernet'" could be interesting.
```

justin@Europa:~$ dmesg | grep 'Ethernet'
[    1.030034] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.332913] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.358699] ax88179_178a 5-1:1.0 eth1: register 'ax88179_178a' at usb-0000:02:00.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:05:1b:a3:41:52


```

From what I understand now, that r8169 is NOT what I want.  I've read posts about blacklisting it so that what I want, r8168 will operate instead.  Should I do that?  When I tried it previously it didn't fix anything, so I un-blacklisted it.  Should I have blacklisted and done more in addition to that?

Right now, with this USB Ethernet adapter thing, it's functioning in DHCP calling itself "Wired Connection 1".  When I tried through the motherboard's ethernet, DHCP and a variety of static IP setups did nothing.

---

### Post by chili555 on 2014-01-02
> From what I understand now, that r8169 is NOT what I want. I've read posts about blacklistingI thought we established that r816**9 ** wasn't loading. You certainly could blacklist it, detach the USB, reboot and see what happens. If r816**8**  loads and the device still doesn't work, I'd blacklist r8168, too, plug in the USB and call it a day.

---

### Post by r3dd on 2014-01-02
> **nitsujz28 said:**
> Thank you for responding!  When I enter "lspci | grep Network" into terminal nothing happens, it just gets ready for a new line command.  If there was a typo I don't know enough to spot it.


You can take out the "| grep Network" part. The network adapters should be listed near the bottom of the list that will come up.

---

### Post by nitsujz28 on 2014-01-02
> I thought we established that r816**9 ** wasn't loading.

We did, a few days ago with nm-tool.  I honestly can't tell what changed, but even nm-tool right now reports r8169.  I even created a line "blacklist r8169" in /etc/modprobe.d/blacklist.conf and restarted.  I don't know.

> plug in the USB and call it a day.

I'm about ready to call it a long day haha.  It's time I get to using Ubuntu and dealing with more useful and fun things.  It'll probably bother me, and I'll probably try to fix it later.

For the record, lspci contained this near the bottom:
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


```

Nothing else related to betwork.  

chili555, I greatly thank you for helping me in my near-helplessness.  This exercise has been benefitial.  Thanks to other folks as well that chimed in to help.


The joke I mentioned is so stupid and excellent, imo.

* So this guy walks in to a psychiatrist's office and he's wearing nothing but saran wrap around his body..  The psychiatrist takes one look at him and says, "Well, I can clearly see your nuts!!!"

---

### Post by chili555 on 2014-01-03
> **nitsujz28 said:**
> We did, a few days ago with nm-tool.  I honestly can't tell what changed, but even nm-tool right now reports r8169.  I even created a line "blacklist r8169" in /etc/modprobe.d/blacklist.conf and restarted.  I don't know.



I'm about ready to call it a long day haha.  It's time I get to using Ubuntu and dealing with more useful and fun things.  It'll probably bother me, and I'll probably try to fix it later.

For the record, lspci contained this near the bottom:
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


```

Nothing else related to betwork.  

chili555, I greatly thank you for helping me in my near-helplessness.  This exercise has been benefitial.  Thanks to other folks as well that chimed in to help.


The joke I mentioned is so stupid and excellent, imo.

* So this guy walks in to a psychiatrist's office and he's wearing nothing but saran wrap around his body..  The psychiatrist takes one look at him and says, "Well, I can clearly see your nuts!!!"Off topic, but, oh well! A woman decides to spice up her married life and greets her husband at the door wearing nothing but saran wrap. He exclaims, "Leftovers again??"

---

### Post by nitsujz28 on 2014-01-03
HAHA but surprisingly on topic with my off topic joke!

Regarding the network connection, I plan on getting a cheap internal network card for PCI/PCIe from Microcenter so that at least I feel better without having this goofy USB dongle connection thing.  Eventually I want to solve the motherboard problem, or at least confirm it's a faulty mobo port.

Thanks again for help.

---

### Post by nitsujz28 on 2014-01-15
For the record, and for future reference, I continued doing an irritating amount of research on other people's problems regarding Ubuntu and Realtek based NICs.  No golden solution from any discussions dating from around 2008-2013.

So I bought this Intel NIC:  [http://www.microcenter.com/product/360498/Gigabit_PCIe_X1_Adapter](http://www.microcenter.com/product/360498/Gigabit_PCIe_X1_Adapter)

And I wish I had done it right off the bat.  It works perfectly immediately upon first boot.  Ubuntu 13.10.  If there is a way to fix the onboard Realtek stuff, I don't think it's worth it.  Anyways, good first Ubuntu learning experience!

---

