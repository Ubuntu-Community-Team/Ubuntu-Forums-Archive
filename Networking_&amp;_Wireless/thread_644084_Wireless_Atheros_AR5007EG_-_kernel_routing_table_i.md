---
title: "Wireless Atheros AR5007EG - kernel routing table issue?"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by A + on 2007-12-18
I'm not in a huge hurry to have this problem fixed but I would appreciate a little information if anyone could help, as I'm pretty new to ubuntu.  Network Manager shows me a wireless connection and a strong signal (in system>admin>wireless properties>essid).  This means that my card is communicating with the router, correct?  I don't understand why the card cannot reach my ISP via the router, however, as the wired connection is flawless.  I'm thinking it could be the router table entry which shows blank gateway/destination addresses for wlan0 when I issue the 'route' command.

Could someone who has working wireless issue this command in a terminal window and let me know if the wlan0 addresses are blank? (or all zeros) 

I have an Atheros AR5007EG wifi card with Realtek 8139 chipset.  I got this far using the advice kevdog posted on the following thread
[http://ubuntuforums.org/showthread.php?t=574501&highlight=compile+ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=compile+ndiswrapper)

Could the problem be the kernel routing table?  I'd like to know how to update it regardless, if anyone knows that.  I should get addressed with DHCP but my ISP will always have a static address.

---

### Post by A + on 2007-12-18
:oops::oops:  This is now working perfectly...

lspci shows my card as AR5006EG though Vista sees AR5007EG.  This information can be ignored for this setup because it's working.

Hope this helps someone else but I didn't do anything to the routing tables in the end.  I went to Network (by right-clicking on the two computers on the taskbar or Systems>Admin>Network to open Network Manager) and even though the information there was correct (WEP, essid) I disabled ROAMING MODE in PROPERTIES and closed the Network window.  Right-clicking again on the computers graphic on the taskbar gave me 3 new options which I hadn't seen before ... Connect to Wireless Network,  Make new Connection and another and I chose connect to a wireless network and entered my essid and WEP there.  Nothing happened until after I rebooted and now it's faster than Windows.  

Network Manager has problems I suppose.  Hope this helps someone else.

---

### Post by stauntonel on 2007-12-28
I have the same problem. Looks like an ndiswrapper issue:
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468")

I don't use gnome but XFCE with debian lenny, but the problem is the same.

---

