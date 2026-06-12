---
title: "Wireless router - Firefox can't see internet"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by hodad on 2007-12-02
I just bought a new Ubuntu laptop last month, and have had much trouble trying to get it to connect thru my Linksys Wireless G (WRT54G) to the internet.  I can ping the wireless g, and access it's setup page.  I can ping my internet provider, but can't ping the associated gateway at the internet provider.

Here's what I get with "route -n":

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
216.52.32.0     0.0.0.0         255.255.255.128 U     0      0        0 eth3 
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth2 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth3 
0.0.0.0         216.52.32.126   0.0.0.0         UG    100    0        0 eth3 
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth2 

the first line is for my internet provider, but the gateway for the provider is in the next to last line, not in the same line as the internet destination (?).  I don't know what 169.254.0.0. is (I think it's someone elses wireless).

Since I can ping the network provider, but not the gateway, could it be some gateway setting problem?  

ALSO where do I fing the MAC address of my laptop, because the router has a security setting for allowing some pc's to access thru the router (I think).

Thanks


How do I get into the routing table to clean it up, since Network and Network Tools simply don't work!?  I used the "route add" command to add|del the default gw, but can't get it to work to add|del any other lines in the routing table.  Where is the routing table located, and can I go into it to clean it up, or is there another way to clean it up?

---

### Post by Drate on 2007-12-02
Wow, okay, I can tell you some of that.

169.25.0.0 is apipa=automatic private ip addressing, it means that your network card is set for DHCP but it's not getting any information from a DHCP server (probably can't can't find one).

ifconfig or iwconfig (in a terminal) should provide you with mac addresses for your laptops network card.

Did your laptop come with Ubuntu preinstalled from the vendor?  If so then I would THINK that the drivers on it should be kosher, so it's probably (no offence sir) a user error thing and not an "oh crap, Ubuntu doesn't know my hardware" thing.  That's actually good though, cuz it means there is probably an easy solution waiting for you somewhere. :)

Hope I've given you some decent clues to solve the puzzle.

---

### Post by hodad on 2007-12-02
Thanks for the reply; I got the following from the iwconfig and ipconfig commands:

l@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth3      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:641   Missed beacon:0

davel@ubuntu:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:16:D4:DE:DB:3C  
          inet addr:216.52.32.4  Bcast:216.52.32.127  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9783075 (9.3 MB)  TX bytes:540220 (527.5 KB)
          Interrupt:16 

eth3      Link encap:Ethernet  HWaddr 00:1C:BF:19:CF:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:644 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8066 (7.8 KB)  TX bytes:6034 (5.8 KB)
          Interrupt:16 Base address:0x8000 Memory:f8200000-f8200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11095 (10.8 KB)  TX bytes:11095 (10.8 KB)

Not sure where this leaves me, though...  Still need help if anyone has any ideas?

---

### Post by hodad on 2007-12-03
Thanks to Tom at System 76 for the resolution to this problem.  Here's what we did.


I made the changes to the "/etc/network/interfaces" file, basically commenting out all lines except the two lines:
auto lo
iface lo inet loopback

I then reset the wireless router with the reset button on the back. I then "hardwired"the laptop to one of the hardwired ports on the back of the wireless router. The "internet" connector on the wireless router was then hooked up to the internet modem (wireless microwave modem located outside). After doing this, I rebooted, and was able to connect to the wireless router (in hardwired mode) and enter it's setup screen (BASIC setup tab).

At this point, I could see that the router was configured for DHCP. I could still not connect thru firefox to the internet (though I could ping the URL of the internet provider, which meant the hardware connection was OK).

I unselected DHCP on the basic setup screen on the Wireless G, chose "static IP", and a new screen appeared asking for the IP, GW, and DNS server addresses. I then entered the proper addresses for my ISP and tried Firefox. The connection came up immediately,so problem solved.

Just to confirm what you said (Tom), try not to use "System/Admin/Network or Network Tools" unless absolutely necessary, as they change the "interfaces" file, which hoses the wired and wireless network logon process (at least in my case).

Everyone involved - Thanks for your help!:KS
__________________

---

