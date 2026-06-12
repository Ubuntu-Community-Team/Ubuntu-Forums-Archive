---
title: "Networking is working, but Firefox/Konqueror can't resolve"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by pholvey on 2008-07-08
Hi all, 

Alright, so here's the low down.  I'm on like my second week of Ubuntu and everything is going really well up until 3 hours ago.  I've got 8.04 on my laptop (Toshiba Satellite A205-S5803) which is a dual-boot for now.  I was looking for ways to move away from that and have a single Linux partition so I was trying out xVM VirtualBox by Sun with XP as the guest, which worked awesomely for like 5 different starts.

Today I was mapping a network drive to Linux - fine.  I start up the xVM and map the drive in Windows.  Prior to this I've noticed no problems with the internet on the host (Linux) or on the guest (XP).  I map the network drive using simple networking in XP (My Computer -> Tools -> Map Network Drive) - fine.  Network drive works.  All is good...

Except that now Linux can't resolve anything.  Firefox/Konqueror crap out on me.  They both are returning "Address Not Found."  So now I'm thinking, ok, ok, xVM has somehow commandeered my networking and Linux can't find it.  Except that the Network Manager is happily connected and can see both the wired connection and the wireless ones.

So I run ifconfig.  I get eth0, lo, and wlan0 all running (eth0 and wlan0 both broadcasting and lo on loopback).  I can see the packet count increasing (especially when windows is running) so Linux sees my connections.  If i '$ host google.com' I get the resolved IPs just fine.  '$ slogin server_i_use_all_the_time' comes back with "Name or service not known'.  

So what I'm seeing is that Linux sees my connections, but can't use them (but kinda can? I don't know).

I thought it might have been a hosts issue, but it looks ok.

I've got 

127.0.0.1 localhost
127.0.1.1 machinename

#the following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback -> I commented this out after seeing another post...didn't help
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I tried removing the mapped drive from the Box to no avail.

Anyone have any idea?  Any help is appreciated...Thanks!

Sincerely,

pholvey

PS...the network drive mapped to Linux still works (I don't think that it's a local network mapping, but I could be wrong...its from my university and I'm on their network).  Internet in the Box works, and on the dual-boot Vista...so its not a blocked MAC address.  That's all I've got.

---

### Post by Ocxic on 2008-07-09
see if you can ping any websites, or routers on the network (just make the last # of your IP a 1 to ping your router) check the DNS section of you network config in system->admin menu. write down the entries and remove them and restart the computer. 
you can also try using the network manager to disable networking and then re-enable it after 30sec-1min also make sure that your using roming mode or it is set to DHCP.

---

### Post by pholvey on 2008-07-09
> **Ocxic said:**
> see if you can ping any websites, or routers on the network (just make the last # of your IP a 1 to ping your router) check the DNS section of you network config in system->admin menu. write down the entries and remove them and restart the computer. 
you can also try using the network manager to disable networking and then re-enable it after 30sec-1min also make sure that your using roming mode or it is set to DHCP.

Hey Ocxic.  Thanks for the speedy reply.  Results:

Ping to the ethernet router = goes just fine.  All packets returned, none lost (23 sent, 23 recieved)

I tried the DNS deletion/reboot...didn't work.  They were reset to what they were before after the system started up.

Tried the disable/reable = didn't work.

Roaming mode is set for all connections.

Sorry.  I'm still showing "address not found" in firefox.

Any other ideas?

pholvey

---

