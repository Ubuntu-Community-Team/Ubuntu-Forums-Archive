---
title: "Wireless connected, but no ping, no web"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by johnjust on 2007-10-11
Oddly enough, I'm laughing at this instead of swearing.  I've been on and off with my wireless (Just like Feisty is supposed to be >.> ), and it's getting worse.

I've finally got my wireless to work by blacklisting the prism2 driver, causing it to load the orinoco driver, which works great at my house.  When I go anywhere outside my house, wireless is broken.  At work, it will connect but I can't ping, can't use the web, etc...  It doesn't work at all at my friends house (SAME EXACT wireless setup as me, same router, same settings), it hangs at 57%, the IP config stage.  I can't use a wired connection at his place, because it assigns me an automatic private address.

I'm typing from a wired computer now, not my laptop, so if you need any command output, I'll transpose it the best I can.  Here's some initial info to get you started.

iwconfig
```

eth1      IEEE 802.11b  ESSID:"TRC"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:80:BC:E3   
          Bit Rate:1 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=2/92  Signal level=112/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:9  Rx invalid frag:0
          Tx excessive retries:102  Invalid misc:0   Missed beacon:0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0B:CD:A9:CD:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:02:8A:99:E1:70  
          inet addr:192.168.123.213  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:fe99:e170/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:54 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34296 (33.4 KiB)  TX bytes:34323 (33.5 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:0B:CD:A9:CD:53  
          inet addr:169.254.8.116  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2425 (2.3 KiB)  TX bytes:2425 (2.3 KiB)

```

sudo lshw -C Network
```

  *-network:0
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 01
       serial: 00:02:8a:99:e1:70
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 ip=192.168.123.213 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d000a000-d000afff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a9:cd:53
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:2400-24ff iomemory:d0008000-d0008fff irq:10

```

lspci | grep 'Network'
```

00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

```

---

### Post by Lambert on 2007-10-11
The device and driver are working on your computer. 

> 
Access Point: 00:1A:70:80:BC:E3


this from your first command of iwconfig says you were able to associate with whatever router you were trying to connect to during the time you ran this command. The problem is the routers is not handing you an ip and other information.

Once you're associated with a router, type in this command to see what happens.

```

sudo dhclient eth1

```

Are you using the default network manager in ubuntu to connect? I haven't used it but it suggested by some to uninstall network manager and use a program called wicd to manager wireless connections.

---

### Post by johnjust on 2007-10-11
the dhclient gives me an ip address, no problems there, I am using KNetworkManager (KDE), so I'll uninstall that and try wicd.  I've seen that around the boards, I just never thought it would be something simple like that...

---

### Post by Lambert on 2007-10-11
> **johnjust said:**
> the dhclient gives me an ip address, no problems there, I am using KNetworkManager (KDE), so I'll uninstall that and try wicd.  I've seen that around the boards, I just never thought it would be something simple like that...

missed that, iwconfig doesn't show ip for you, but I see it in ifconfig.

Look at the output of 

```

route

```

---

### Post by devilears on 2007-10-11
I had this problem with both edgy & feisty and it frustrated me endlessly. After a long time, I figured out that it was interference caused by a (2.4GHz) audio-video sender/receiver in my house! So now, whenever i want to get on my wireless home-network, I switch the AV sender/receivers off and my laptop connects flawlessly!

---

### Post by johnjust on 2007-10-11
> **devilears said:**
> I had this problem with both edgy & feisty and it frustrated me endlessly. After a long time, I figured out that it was interference caused by a (2.4GHz) audio-video sender/receiver in my house! So now, whenever i want to get on my wireless home-network, I switch the AV sender/receivers off and my laptop connects flawlessly!

Good idea, I actually noticed that my friends router was broadcasting on channel 6, and my wireless was set to channel 13 (or something like that).  When I first got my wireless router (2.4ghz), it interfered with my cordless phone (2.4ghz)...  but for some reason, everything works now >.>

---

### Post by johnjust on 2007-10-11
OK, apologize for the double post...

I installed wicd, ran the autostart script, created the link to autostart, but I still can't ping, and there is no tray icon for wicd, just a grey square.

Any suggestions?  I added the repository to my list, and made 'edgy' into 'feisty', and dl'ed/installed wicd through Adept.

---

### Post by kevdog on 2007-10-11
check out the link in my signature to do a manual connection -- its good for troubleshooting.

type
sudo modprobe -r orinoco
sudo modprobe orinoco

then begin the commands

---

### Post by johnjust on 2007-10-11
Your tutorial was one of the first things I looked at during my early troubleshooting stages, I get the same results.  The network I'm connecting to is unencrypted, so it's not a WPA/WEP problem.

I'm wondering if there's something on the router (firewall for instance) that's stopping me from doing anything, although it's strange, since I have a 192.168... IP address, and I can ping the gateway.  I don't know what else to do.

My wired connection is working fine here at the office, and I'm sure when I go home, my wireless will work.

The tray.py file in /opt/wicd has an if...else to decided between edgy and dapper, should there be a feisty test in there?

---

### Post by Lambert on 2007-10-11
> **johnjust said:**
> Your tutorial was one of the first things I looked at during my early troubleshooting stages, I get the same results.  The network I'm connecting to is unencrypted, so it's not a WPA/WEP problem.

I'm wondering if there's something on the router (firewall for instance) that's stopping me from doing anything, although it's strange, since I have a 192.168... IP address, and I can ping the gateway.  I don't know what else to do.

My wired connection is working fine here at the office, and I'm sure when I go home, my wireless will work.

The tray.py file in /opt/wicd has an if...else to decided between edgy and dapper, should there be a feisty test in there?

In your first post you said

> 
it will connect but I can't ping


your last post you said
> 
and I can ping the gateway



Can you ping an outside server using their ip? Try ubuntu.com's ip.

91.189.94.158

If you can do that then need to check the dns settings.

---

### Post by johnjust on 2007-10-11
No dice with the ping, Lambert.  It's weird, instead of timing out or saying it cant find host, the Konsole just stops.  It goes to a new line with nothing on it, and I waited 5 minutes before it returned to the prompt.

And yes, I can ping the gateway, but nothing outside the network, sorry for the confusion :)

EDIT: I also said that the wicd tray icon wasn't showing up for me, I fixed it by going to /home/[user]/.kde/Autostart and manually making a new link to the tray.py script.  Previously, I followed the instructions on the wicd homepage:

```

sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py

```

but that didn't work

---

### Post by kevdog on 2007-10-11
Lets just summarize b/c Im confused

#1 - You get a local IP address?? ipconfig to check
#2 - You can ping the router/gateway???
#3-  You can't ping anywhere externally outside the gateway??
#4- Please post route -n

---

### Post by Lambert on 2007-10-11
Your work and friends router connections are probably going to be different problems.

1. As far as your work connection, it appears that a connection to the router is being set up (the ability to ping the router) but the domaincontroller is not authenticating your pc and allowing you into the domain. You might have to contact the IT dept and ask them to help you get on the domain with your machine. You can read the following page

[http://www.yolinux.com/TUTORIALS/LinuxTutorialMicrosoftWindowsNetworkIntegration.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialMicrosoftWindowsNetworkIntegration.html)

For more on this you can try to search around for samba and domain/connect linux client to domain/ etc...

2. As far as your friends router, will have to go through the troubleshooting again for that router, check route, can you ping, like previous post said is there a possible signal inteferance etc...

---

### Post by johnjust on 2007-10-11
Sorry for the confusion, I'll try my best to clear it up.

> **kevdog said:**
> Lets just summarize b/c Im confused

#1 - You get a local IP address?? ipconfig to check
#2 - You can ping the router/gateway???
#3-  You can't ping anywhere externally outside the gateway??
#4- Please post route -n

There's 3 different setups: home (which isn't a problem), work, and my friend's house

First, my wireless/wired work fine at home.  I have two routers, actually.  One is the LINKSYS BEFW11S4 (B wireless), the exact same model as my work and my friend's house.  The second is the same router with G wireless, I just can't remember the model number.  Both run wireless fine, I have 0 problems.

Second, my wireless doesn't work at work, wired works perfect.  When on wireless, I'm connected, I have a 192.168... IP Address, and I can ping the router, but nothing external.

Third, my friend's house doesn't work wired or wireless.  He has the EXACT same router I have, with all the exact same settings (guess who set it up :P).  I get an automatic private IP with wireless and wired, I can ping the router, but nothing external.

> **Lambert said:**
>  You might have to contact the IT dept and ask them to help you get on the domain with your machine.

Haha, we're a small business, the router is right here behind me, on the server rack.  Its the same as the one I have at home...  and the exact same one my friend has, all are LINKSYS BEFW11S4 (B wireless).

---

### Post by Lambert on 2007-10-11
Ok, interesting issue you have here. I really don't know what steps to take next but I'll suggest 2 and give a free bump for the thread.

1. Turn off ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2.before connecting to the router, power cycle them off/on.

---

### Post by kevdog on 2007-10-11
Ok, sounds like on the two networks that nothing works that its either a routing problem or a dns problem.

If you can ping by IP address and get a reply from outside then its a dns problem.

To discover a routing problem, type route -n

Mine looks like this:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

Notice the last line, or the one with UG.  This is the Universal Gateway -- the door out to the internet.  You need this statement here (should be same address as your router).  If you dont have a gateway you need to add it manually, something like

sudo route add default gw 192.168.1.1

If you have an incorrect gateway, to get rid of it:
sudo remove route 192.168.1.1

Hopefully you can provide some info to help us out.

---

