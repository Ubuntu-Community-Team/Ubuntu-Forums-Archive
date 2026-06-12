---
title: "Blog viewable in XP but not Ubuntu: networking differences?"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by SteveHoffmanUK on 2006-12-14
My son&#347; blog is viewable on my Windows XP Home desktop with Firefox but not on either my Ubuntu 6.06 Dapper desktop with Firefox 1.5.0.8 or my Ubuntu 6.10 Edgy laptop with  Firefox 2.0. All three are connected to the same UK ISP (Vispa) using a single Netgear wireless router. The blog is at:
[http://www.hofflimits.com](http://www.hofflimits.com).

Respondents to a similar thread in General Help show similar results: Some can see it using Dapper, Edgy, Firefox 1.5.0.8 and FF2.0, others cannot. There is no common factor among those who can view it and those who cannot.  Therefore it has been suggested that the difference must lie in different network/dns settings between my XP and my Ubuntu machines.

I am not an expert in this area. Can anyone help me to identify the differences in these settings between my two machines and suggest how I can change my Ubuntu settings to enable me to see the blog?

Many thanks

---

### Post by eriefisher on 2006-12-14
FF 1.5.0.3 and Konqueror ok. Try about::config in the address bar on both sides and compare the settings.

---

### Post by SteveHoffmanUK on 2006-12-14
Eriefisher wrote:
> Try about::config in the address bar on both sides and compare the settings.

If I put just that in the address bar of my browser, I get an error message that it&#347; not a valid URL. Do I need to prefix it with something?

---

### Post by spd106 on 2006-12-14
Works fine from here, I'm on Edgy, connected through BT.

[QUOTE=SteveHoffmanUK]
If I put just that in the address bar of my browser, I get an error message that it&#347; not a valid URL. Do I need to prefix it with something?[/QUOTE]

Too many colons, it should be **about:config**.

---

### Post by SteveHoffmanUK on 2006-12-14
Spd106: Thanks; corrected it and - WOW - there seem to be about 60 settings just for networking. Can you suggest which ones I should look at as likely to be the critical ones that make the difference between the XP and Ubuntu results?

---

### Post by eriefisher on 2006-12-14
I would first just see what or if the are any differences between the two. Then change Ubuntu to match XP to see if it helps.

DOCUMENT ALL CHANGES!!!!!

---

### Post by compwiz18 on 2006-12-14
Not that is is related, but I have a similar problem with Wikipedia.  It works in Windows, but not in Ubuntu, unless I use an SSH tunnel to a proxy.  So I would be interested in seeing your solution.

---

### Post by cracker on 2006-12-14
Looks like this isn't a problem with Firefox. Post the results of the following:
On windows, click Start > Run..., and enter
```
cmd
```
Once the command window opens, run 
```
ipconfig /all
``` 
and paste the results here.


On Ubuntu, open a terminal (Applications > Accessories > Terminal), and run 
```
ifconfig
```
then 
```
cat /etc/resolv.conf
```
and paste all the results here.

---

### Post by SteveHoffmanUK on 2006-12-14
@cracker
Here are the results that you requested. 

In my Windows XP:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Jennifer Hoffman>ipconfig /all

Windows IP Configuration

       Host Name . . . . . . . . . . . . : jen
       Primary Dns Suffix  . . . . . . . :
       Node Type . . . . . . . . . . . . : Mixed
       IP Routing Enabled. . . . . . . . : No
       WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

       Connection-specific DNS Suffix  . :
       Description . . . . . . . . . . . : D-Link AirPlus DWL-520+ Wireless PCI
Adapter
       Physical Address. . . . . . . . . : 00-80-C8-CE-EA-3E
       Dhcp Enabled. . . . . . . . . . . : Yes
       Autoconfiguration Enabled . . . . : Yes
       IP Address. . . . . . . . . . . . : 192.168.0.2
       Subnet Mask . . . . . . . . . . . : 255.255.255.0
       Default Gateway . . . . . . . . . : 192.168.0.1
       DHCP Server . . . . . . . . . . . : 192.168.0.1
       DNS Servers . . . . . . . . . . . : 192.168.0.1
       Lease Obtained. . . . . . . . . . : 15 December 2006 00:27:27
       Lease Expires . . . . . . . . . . : 18 December 2006 00:27:27 
```

In my Ubuntu 6.06 Dapper:

 ```
steve@steve-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:18:77:66:48
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:00:1C:56
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fe00:1c56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11457 errors:23 dropped:0 overruns:0 frame:0
          TX packets:10171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8895184 (8.4 MiB)  TX bytes:1346613 (1.2 MiB)
          Interrupt:185 Base address:0x9000

steve@steve-desktop:~$ cat /etc/resolv.conf
domain mshome
nameserver 192.168.0.1
steve@steve-desktop:~$

```

Hope this helps!:)

---

### Post by spd106 on 2006-12-15
Have you tried disabling IPv6? You can do this in the about:config in firefox, toggle network.dns.disableIPv6 to true.

---

### Post by SteveHoffmanUK on 2006-12-15
spd106 wrote:
> Have you tried disabling IPv6? You can do this in the about:config in firefox, toggle network.dns.disableIPv6 to true.

IT WORKED! IT WORKED! Toggled the setting and now I can see the blog. 

In case no one has told you, you are a genius. :D

ON EDIT: Works also on my Edgy Ubuntu 6.10 laptop, consistently on both that and my Ubuntu Dapper 6.06 desktop. Is this everyone else&#347; experience as well?

---

