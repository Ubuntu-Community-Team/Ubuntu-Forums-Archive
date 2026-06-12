---
title: "Can see internet but can't ping gateway??"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by dgavenda on 2008-11-07
Here's my problem...

Using wired, everything works.  Using only wireless card, I can see internet but not my other computers.  I can't even ping the gateway but I can ping yahoo.com.  

I have verified I am on my network so that is not the problem.

wired card ip=192.168.1.55
wireless care ip = 192.168.1.101

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
localnet        *               255.255.255.0   U     2      0        0 wlan0_rename
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0_rename
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0



Any ideas why this would occur?

---

### Post by mantelo on 2008-11-07
hi.

Since you can see the internet but not your own network, most likely you connected to somebodyelse's wireless network.


good luck.

---

### Post by Coreigh on 2008-11-07
I know you said you were on your own network, BUT did you verify this by the network name, or by the IP addresses you posted? I ask because the 192 address range is not unique, it is common and used behind a gateway so it is still "unshared." I would re-verify that the network you connected to is yours. One simple way is to unplug your wirless base station and if you still can ping Yahoo.com then TA-DA! its not your network.

---

### Post by dgavenda on 2008-11-07
I am 100% sure it's my network.  Verified w/ looking at external IP too.  So, ya...it's mine.

---

### Post by Coreigh on 2008-11-07
Can you post output of:
```
ifconfig
```

and:
```
netstat -rn
```

---

### Post by dgavenda on 2008-11-07
Sure.

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:be:2b:3d  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:UNSPEC  HWaddr 00-1C-BF-4C-F4-85-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14192 (14.1 KB)  TX bytes:14192 (14.1 KB)

wlan0_rename Link encap:Ethernet  HWaddr 00:1c:bf:4c:f4:85  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe4c:f485/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4002769 (4.0 MB)  TX bytes:519566 (519.5 KB)



$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0_rename
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0_rename
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0_rename
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by Coreigh on 2008-11-07
Says there that the wireless (wlan0) IP is 192.168.1.100, not 101, not a big deal. The 169.254.0.0 address for eth1 is worrisome. It should not interfere, but if you could eliminate the suspect it makes trouble shooting easier. And it is showing as connected to wlan0-rename in the netstat. Can that card be removed or disabled?

You said you can ping Yahoo.com, but not the gateway 192.168.1.1. Can you ping eth0 (192.168.1.55)? Or localhost?

Are there any other computers on this network that you can try to access to or from?

I see no other obvious problems.

---

### Post by dgavenda on 2008-11-07
Ya...I have been trying some things and looks like it took 100 over 101 during that.  Problems still exists though.  

I can ping 192.168.1.55, localhost and yahoo.  

I can't ssh into it from other computers...can't even ping it.  From the problem child, I can't ssh nor ping the other computers.  Really odd.  

I have nothing set up in my router.  I have another laptop using 105 and it can ping the other computer with exception of the problem child.  

Hmmmm....confusing.  I appreciate the help.

---

### Post by gpsmikey on 2008-11-07
Just out of curiosity, assuming you are running dhcp to get that address, go into your router from one that can get to it and see if it did indeed hand that address out (and if the MAC address matches your problem child).  Most routers let you see what addresses they have handed out and what MAC address they are associated with.

mikey

---

### Post by dgavenda on 2008-11-07
Can you point me to where I would find this in a Linksys wrt54g?  Doesn't seem to be obvious and it's not under the admin/log section.  I could block my mac and see if I can still get out on the problem child.


Side note: to use cisco vpn, I have to use the wired card.  "Secure VPN Connection terminated locally by the Client
Reason: Failed to enable Virtual Adapter."


I wasn't running this before at all but just really stumped on this issue.

---

### Post by dgavenda on 2008-11-07
Ok...I can block my problem child's IP and internet traffic ceases for it.

I also reboot the router and problem still exists.   Gonna try a Live CD....

---

### Post by Coreigh on 2008-11-07
On my Linksys WRT54G (firmware v 1.00.9) it is in the Status tab under Local Network and then there is a DHCP Clients Table button.

---

### Post by dgavenda on 2008-11-07
Ya...it's in there.  The mac and ip match up.

---

### Post by dgavenda on 2008-11-07
Works w/ live cd.  I can ssh to my other computers and see the internet.  

So, it's definitely a setting/config problem.  The only hard part is finding where and what it is.

---

### Post by Coreigh on 2008-11-07
I didn't think of this because I use a hardware firewall, but do you have the firewall installed and enabled on "the problem child?"

Like I said I don't use the Ubuntu one so I don't know how to turn it off but here is a link to the wiki:
[https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

---

### Post by dgavenda on 2008-11-07
First, can you set up the ufw to monitor only wireless and not the wired?  If so, kinda cool.

But...to add to the confusion....after I rebooted coming out of LiveCD to using the harddrive...it works.  

So confusing and now aggravating that it just magically works after a reboot.  


Thanks for all your help. I just really wish I knew what caused the problem.

---

### Post by gpsmikey on 2008-11-07
I have the WRT54GS but suspect they are similar (although I have reloaded with the Tomato firmware ver 1.21 so now it really is different!!).  I had printed it out before switching and it shows that it was at 192.168.2.1/DHCPTable.asp (note that I have mine set to 192.168.2.x instead of the normal 192.168.1.x for Linksys routers.  It was labeled "DHCP Clients Table" with a heading on it of "DHCP Active IP Table".  I remember it was not intuitively obvious how to find it - each time it took some snooping around on the router config to finally stumble on that page.  Don't forget that your wireless will have a different MAC than the wired connection (I've made that mistake before).  Hope that helps.

For what it's worth, here is what it looks like in "tomato" (the Linksys version was similar)
```

Interface MAC Address     IP Address    Name RSSI    Quality Lease      
vlan1 00:1D:45:70:69:05   71.231.76.1     
br0   00:06:5B:2B:DF:82   192.168.2.101 michi       0 days, 03:08:07 
br0   00:22:15:15:2F:3C   192.168.2.102 flicker     0 days, 19:48:35 
br0   00:03:1B:5B:6E:F7   192.168.2.107 CS-5B6EF7   0 days, 15:29:41 
br0   00:0E:A6:A0:0F:0B   192.168.2.138 quickpix    0 days, 22:22:31 
br0   00:22:15:05:F6:04   192.168.2.205  

```

The "vlan1" interface is the WAN side and the "br0" is the LAN side.

mikey

---

### Post by dgavenda on 2008-11-07
Hmmm...tomato looks interesting.  Better layout of pages/info than the default linksys.

---

### Post by dgavenda on 2008-11-07
Ok...I can repeat the problem.

Using network-manager-gnome to connect the wifi card.  Works.  Wired card has no cable in it.  

If eth0 is down, it works fine.  If it's up w/o a net cable, it stops the wifi from being about to ping internal computers but the access to the interest remains.  


Anyone have any logical explanation for that?

---

### Post by gpsmikey on 2008-11-07
Yeah, I liked the bandwidth monitoring feature so I can see what the network is doing and has been doing for the last day/week/month as well as some other features.  One of the nice features that the Linksys didn't have (or I never found) is a "static dhcp address" - for those machines that need to have a known IP address in your network, instead of having to set them up with a static address, you can configure the router to always hand out the specified IP to that specific MAC, so you can leave the machine set to dhcp but it will always have a known IP address (unless you change your ethernet card ... ).  Kind of handy.

As far as your problem goes, you have verified that it is indeed your network handing out the IP.  Only other thing I can think of is to try rebooting the router and the other machines to see if that changes anything (switches can be funny when things change and they don't wake up to that fact). 

mikey


mikey

---

### Post by dgavenda on 2008-11-07
gpsmikey,

I tried all that before I even posted.  The only think I found was a factor was a reboot of the problem child laptop and what I found in my above post dealing w/ eth0 being up/down.

---

### Post by gpsmikey on 2008-11-07
Kinda suspected you had already been there, but it was worth asking.  Networking is funny (or not) - billions and billions of bits run around the network magically unless one of them is wrong then nothing goes anywhere.  I was there the other day when I reconfigured some stuff and I couldn't even get to the router much less anything else for a bit ... NOW we're havin fun !!

mikey

---

### Post by Coreigh on 2008-11-10
I noticed that when you restated the problem you said that it works when eth0 is disabled but not when it is enabled. Is that correct? It could be a routing problem either with the WRT or iptables (if you are using it) Here os a forum link for a simlar problem:
[http://ubuntuforums.org/showthread.php?t=501221]("http://ubuntuforums.org/showthread.php?t=501221")

I don't have any machine with two NICs so I have been unable to recreate your troubles.

---

