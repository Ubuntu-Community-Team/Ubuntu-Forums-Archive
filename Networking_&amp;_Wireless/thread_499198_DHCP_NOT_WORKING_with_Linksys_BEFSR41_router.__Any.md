---
title: "DHCP NOT WORKING with Linksys BEFSR41 router.  Any advice?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by rstewartmailacct on 2007-07-12
Hi all,

I have three computers connected to BEFSR41 Wired router/gateway with the setting on router to be a DHCP server.  The windoze box connects and one Ubuntu box will connect with DHCP set to Automatic in network config.  

I have to reset router and turn off both linux boxes to allow one or the other to get on.  Basically either the router is not offering the IP or Ubuntu is asking for a new IP each time /etc/init.d/networking restart is run.  The interfaces file is set correctly and once again as I have said either machine can get on but not both.  The nics are different and machine names are different.

What gives?  Has anyone encountered this?

Thanks

---

### Post by tcpip4lyfe on 2007-07-12
First off try, try a new cable.  Even if the link light is on. Then click on manual network configuration in the taskbar, type your password, and make sure you wired connection is set to dhcp. If it still doesn't work, try setting you connection to manual and copy the info from you windows box.  Use an unused ip though of course. If it still doesn't work after you've tried those steps let us know.

---

### Post by tcpip4lyfe on 2007-07-12
Ohh yeah you can do a firmware upgrade too if the other step doesn't work. good luck.

---

### Post by rstewartmailacct on 2007-07-12
Thanks for the reply.  I tried brand new cable and manual config.  I'm thinking it's the Linksys.  M$soft must be doing something special with Linksys to make the IP get offered?

Don't see a way to force linux to release and request new IP.  Already tried ifup and ifdown.  Tried /etc/init.d/networking restart.  Looks like the restart contains the dhclient so this is no help.

Any other ideas anyone?  I hate to do a static IP.  I'm also thinking of replacing the old stuff with wireless but the laptop only has usb 1.10 so the usb adapter I was looking at may be toooo sloowwww.

Laptop is a Dell Latitude C600 with 256mb ram 20gb hd and 800mghz Pentium III.  Any suggestions for wireless nic and router?

Thanks

---

### Post by MD_Willington on 2008-01-29
I get the same thing :(

Ain't the cable because the same cable works fine with our XP Pro machine...

The router (V2) has the latest firmware.

---

### Post by jonnadab on 2008-04-21
I tried some other tips, such as these facts:
 The Gateway is the router 
 dns ip is the router
 host ip is (or might be) the router ip +1, meaning that the last number on the router ip may be some number from 2 up to 200 something.

Then I tried to modify the DHCP this way:

Places-Administration-Network-Static IP
  IP Address - 192.168.1.1  (router ip)
  Subnet Mask- 255.255.255.0
  Gateway    - 192.168.1.1  (router ip)

This worked for some people. However....

After trying these and many variations on every page I encountered in the network sections, I finally changed to roaming in my network, then in Firefox, went to Edit-Preferences-Advanced-Network-Settings, selected Manual Configuration, inserted 192.168.1.1 for HTTP Proxy, selected the check to use with all protocols. The port was set to 0, and No proxy to localhost, 127.0.0.1. And, Viola! I was online! My system showed internet activity even when I couldn't get online. This worked for me!

Cheers!

---

### Post by Grandma_DOG on 2008-07-07
I'm having trouble with this too, on a Netgear NAT router.  The router worked fine  for over a year.  I run a data warehousing server group and need these machine IPs to stay static without creating static IPs for each frilling box.

So 2 weeks ago, after a long time, we rebooted a couple of boxes.  We noticed they didn't take their reserved IPs, but took IPs outside of the range ie. range was x.x.x.100 and they took x.x.x.150.  Things we did different was we upgraded my ubutu boxes from Dapper to Fawn a few months ago.  I also suspected one of the other boxes on the network may accidentally have DHCP server up and interfearing with it, but I ruled that out after you see the rest of this post on the DHCPREQUEST thing.

So we figured the old Netgear router was crapping out, we ordered 2 new routers, one for production and one for back up.  Guess what?  The new routers show the same weird stuff, Ubuntu boxes are not taking the reserved IPs they are supposed to.  Looking at 'sudo dhcpclient eth0' they seem to be requesting "DHCPREQUEST" the goofy IPs.

I suspect the solution will be some DHCP setting on the client side in Ubuntu. Can anyone tell me what it is?

---

