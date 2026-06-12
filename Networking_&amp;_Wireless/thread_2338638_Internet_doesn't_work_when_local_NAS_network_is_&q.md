---
title: "Internet doesn't work when local NAS network is &quot;connected&quot;"
date: 2016-09-30
forum: Networking &amp; Wireless
---

### Post by mike248 on 2016-09-30
The setup is Kubuntu 16.04 running inside Vmware 11 Workstation.  Host OS is Kubuntu 14.04.  I have 8 NICs - 2 internet NIC's - each seperate ISP.  One NIC goes to a switch with a NAS (IP range 100,100,100,xxx).  The other ISP NIcs have standard IP's 192.168.100.xxx and 192.168.101.xxx  - those are the interior addresses for the LAN and routers, the modems are external.  

I did an install of 16.04 and I think the internet work fine before I assigned an address for the NAS NIC via the manual selection.  All use IPv4.  I even gave the correct address in the host file and tried adding the address in the fstab.  

Well when I try to access the internet with the NAS network "connected" nothing works.  I can't even ping outside of the network though I can ping the routers.  as soon as I "disconnect" the NAS network all is fine and dandy.  

I have found that it seems that Kubuntu doesn't like to use the /network/interfaces files (which sucks b/c you can define everything here with a cut and paste from an old system).  This make assigning metrics difficult from what I have seen.  

Can anyone help me get ny NAS working so I can talk to it?  The setup on my 16.04 system is exactly the same as my host 14.04 but with different IP's for the NIC's obviously.  Same for my windows VM's.  I just tried again and when NAS NIC is conected it pings away but no other NIC can ping outside network.  

What's going on here?  Any help is greatly appreicated!

---

### Post by TheFu on 2016-09-30
Using a routable subnet for an internal subnet is problematic for non-experts.  Can you put the NAS on a private address range, like 10.10.10.xxx/8?  Plenty of IPs there.

Sure, in theory it shouldn't matter.
Would be clearer if you posted the routing table and ifconfig data for each system, including the NAS. Please use code tags.

---

