---
title: "Cisco VPN chokes (Ibex)"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by DaAlexMax on 2008-11-03
I'm encountering issues with Ibex and Cisco VPN's.  I upgraded from Hardy to Ibex.  Hardy works 100% great, no problems.  In Ibex, though, I can connect to a Cisco VPN and it works fine until I try to transfer something larger than a few kilobytes using any protocol.  It seems to 'freeze' midstream on anything bigger than a few kilobytes.  It doesn't appear to kill the VPN connection, but it 'freezes' that one connection so I have to kill the program (ssh, filezilla) and try again.

This happens with both the Cisco VPN client for Linux AND VPNC through network manager, which leads me to believe that it's not a problem with network-manager and rather a network driver bug.  It's a showstopper, so unless I can get this fixed quickly I'm going back to 8.04 and will seriously consider upgrading to newer versions in the future.

I'm using a Dell Vostro 200 with an Intel 82562V-2 network adapter.

---

### Post by Rob Glenn on 2008-11-26
I've got exactly the same irritating problem!  Exact same VPNC config file works fine on Gutsy Gibbon, but on Ibex, connections fail after only a small amount of data transfer.  For example, internal company web pages load partially and then stop.  Any solutions would be greatly appreciated!

---

### Post by Rob Glenn on 2008-11-26
OK, I think I may have found a workaround for this.  Grepping for vpnc in the /var/log directory found:

[INDENT]daemon.log:Nov 25 21:19:41 cydonia vpnc[9822]: sendto: Message too long
daemon.log:Nov 25 21:20:31 cydonia vpnc[9822]: sendto: Message too long
daemon.log:Nov 25 21:21:20 cydonia vpnc[9822]: sendto: Message too long
daemon.log:Nov 25 21:22:00 cydonia vpnc[9822]: sendto: Message too long
daemon.log:Nov 25 21:22:46 cydonia vpnc[9822]: sendto: Message too long
daemon.log:Nov 25 21:22:56 cydonia vpnc[9822]: select: Interrupted system call
daemon.log:Nov 25 21:22:56 cydonia vpnc[9822]: terminated by signal: 15
[/INDENT]

I ran ifconfig and found that the MTU was 576.  For a standard ethernet connection, this is obviously the wrong value!  So I manually set it to 1500 (network icon right click -> edit connections -> eth0 -> edit -> wired -> MTU) and, so far, so good.  I can now browse company web pages and set up my remote desktop connection.  However, it does at least initially appear to be a bug that the "Automatic" MTU setting came up with the wrong value.

---

### Post by delictuscoeli on 2008-12-07
Thanks Rob!  I had the same problem after upgrading to Intrepid and your workaround did the trick.  Hopefully this issue will get addressed soon.

---

### Post by lgdahl on 2009-09-24
> I ran ifconfig and found that the MTU was 576. For a standard ethernet connection, this is obviously the wrong value! So I manually set it to 1500 (network icon right click -> edit connections -> eth0 -> edit -> wired -> MTU) and, so far, so good.

That didn't help for me, but in another forum (can't remember where), I saw some pointers on editing /etc/ppp/options.

I opened that file, and noticed: 

#mru 542

... meaning it was commented out. I removed the «#», saved the file, and now I've been connected for 30 minutes - while my last «record» was 30 seconds or thereabout.

So, this seems to work flawlessly, thank you very much!

---

### Post by mehturt on 2010-09-14
I have found this issue all over the web and everyone solved it with setting the local interface (eth0 or whatever) MTU to whatever the MTU of the tunnel interface was.
My tunnel interface tun0 has MTU 1412, so I set my wlan0 MTU to 1412, or even 1400 but I stil have the "message too long" issue.

---

