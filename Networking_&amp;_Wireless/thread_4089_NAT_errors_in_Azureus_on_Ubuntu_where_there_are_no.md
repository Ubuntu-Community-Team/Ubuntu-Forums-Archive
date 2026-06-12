---
title: "NAT errors in Azureus on Ubuntu where there are none in Windows"
date: 2004-11-11
forum: Networking &amp; Wireless
---

### Post by conchobar on 2004-11-11
I'm having a strange problem in Ubuntu where all of my torrents stay yellow, yet I can boot into Windows XP on the same computer, with the same settings in Azureus and downloading from the same torrent, and have greens. So, I'm assuming it's a software problem in Linux rather than a port forwarding issue. Any ideas? Also, the router in question is a D-Link 514. I've gone to the configuration page in Linux and Windows and there are no differences.

---

### Post by stoneguy on 2004-11-20
I've got the same thing, but I've explored it a bit further (not to solution alas).

Your problem is that there's another problem. You may be seeing a complaint about port 6969 when Azureus starts. Or when you go to Tools|Configuration Wizard|Next|Next|Test, you're seeing a NAT error on port 6881.

The yellows are because ports 6881-6889 aren't open. Sounds like you've virtualized those ports on your D-Link, or it wouldn't work under XP. (I assume you haven't upgraded to SP2 yet, or if you have, you've disabled its firewall.)

I have a USR8000, and the D-Link and SMC boxes of that vintage are actually the same rebadged product of some company nobody has ever heard of.

I'm baffled by this one. I ran iptables -L just to make sure a firewall hadn't crawled into the machine when I wasn't looking (it hadn't). I also tried toggling the uPNP setting in Azureus - no luck.

---

### Post by stoneguy on 2004-11-27
After a fair bit of Googling and head-scratching, I figured out the fix.

Turns out that the statement that Ubuntu doesn't have a firewall is somewhat misleading. A more accurate description would be that Ubuntu has a firewall that doesn't give a damn. Since iptables is in the kernel, other network settings in /proc/sys/net affect system behaviour.

Turns out that what lets Azureus upload is to turn on ip_forwarding using the oft-quoted statement
[INDENT]echo "1" > /proc/sys/net/ipv4/ip_forward[/INDENT]
Or in Warty, editing /etc/init.d/networking and changing the two instances (occurring after the case "$1")  of
[INDENT]doopt ip_forward no[/INDENT]
to[INDENT]doopt ip_forward yes[/INDENT]
so that ip_forwarding is turned on by default.

Azureus users, go forth and leech no more  8-)

---

### Post by jdong on 2004-11-27
weird -- ip forwarding is an option typically associated with iptables provided NAT services... which is why it's off by default.

---

### Post by conchobar on 2004-11-29
[QUOTE=jdong]weird -- ip forwarding is an option typically associated with iptables provided NAT services... which is why it's off by default.[/QUOTE]
 Thanks for the tips, but so far nothing has changed. Strangely, I got greens after a frest boot. I switched to XP for a few hours, then, back to Ubuntu. No more green. I tried powering down everything to try another fresh boot, but this time it didn't work. Yellow. So, I can't really can't determine why it worked that one time. Any theories?

---

### Post by Magneto on 2004-11-29
edit--- run azureus then type netstat -l in a terminal

---

### Post by jdong on 2004-11-29
are you absolutely sure you configured PORT FORWARDING / (virtual servers) ? Don't rely on UPNP...

Also make sure Linux is getting the same IP as Windows... they may have separate DHCP leases, especially on primitive DHCP servers that routers use!

---

### Post by conchobar on 2004-11-30
Both windows and Linux show 192.168.0.1 as the IP, and thus it's what I entered in the router setup. And yes, I'm absolutely sure I've configured port-portwarding, I set up about 10 different ports in the 50,000+ range. Again, it works fine in Windows with the exact same parameters. Greens for days.

---

### Post by stoneguy on 2004-11-30
I didn't manage to get to green after enabling ip forwarding either. But at least I was showing yellow with non-zero uploading. Before I was running (errr-crawling) red.

Only way I can get green is running Azureus under WinXPsp2 with its firewall disabled (behind a D-Link clone). That's how I know it's not the router setup.

---

### Post by badrinarayan on 2004-12-08
In addition to stoneguy's suggestion,
> Or in Warty, editing /etc/init.d/networking and changing the two instances (occurring after the case "$1") of

    doopt ip_forward no

to

    doopt ip_forward yes 

also try editing [FONT=Courier New]/etc/network/options[/FONT] and change **ip_forward=no** to **ip_forward=yes**

You may restart networking using [FONT=Courier New]sudo /etc/inet.d/networking restart[/FONT] and verify that ip_forward is on by [FONT=Courier New]cat /proc/sys/net/ipv4/ip_forward[/FONT]

Cheers
Badri

---

### Post by stoneguy on 2005-03-20
After a couple months of intermittent pondering  ](*,) , I finally figured it out. Had nothing to do with Ubuntu vs Windows.

I though that my router would let me share ports amongst the systems on my local network if I listed them all in virtual server entries. NOPE! I can only assign ports 6969 and 6881-6889 to a single static IP. I thought that NAT would somehow magically sort out the packets like it does for http etc. But that's not the case.

So if I want to change which system I'm torrenting with, I have to reconfigure/reboot  the router. Very minor annoyance.

---

### Post by gatopolar on 2006-01-19
Hi
I had  the same problem and I notice that the firewall was guilty
I removed the INPUT chain constraints and everythings worked.

iptables -F INPUT
(I have an Accept policy)

Now I have to read some manual to know how to configure my firewall correctly

I hope it helps

Gatopolar

---

### Post by auraithx on 2007-07-25
Sorry to revive a 2 year old thread but can someone explain this to me.

I would do it myself but the commands listed are for warty and do not work in Ubuntu.

---

### Post by sferland on 2007-08-04
Yea, I'm having the same issue, and I also have Ubuntu.  So if anyone can step by step help me fix this issue, I would greatly appreciate it. 

I have dual booted linux and windows xp on two different hard drives.  When I use Azureus in WinXP, everything's fine, green smiley, no NAT error, I've correctly configured my router, and I've port forwarded/triggered with a port 50000+.  I've also set up a static ip (which originally resolved my first NAT error when using windows XP)

When I switch to Ubuntu and start up Azureus, yellow smiley and the SAME port says it's closed.  What's going on/how can I resolve this?  Let me know!!!

---

### Post by Mr. Swiveller on 2007-08-04
There may be multiple reasons. First of all, the ports need to be forwarded properly. If you are absolutely certain that your router is configured correctly, yet torrents still don't work, check whether

- Your firewall is letting BitTorrent traffic through;
- You are behind one or multiple routers (!).

It is possible that you are behind a chain of routers without realising it (this may, for instance, happen if you plug a wireless router into your DSL modem - which is often also a router).

If you are behind multiple routers, forwarding can get a little tricky. Some information can be found here [http://www.duxcw.com/dcforum/DCForumID2/1742.html](http://www.duxcw.com/dcforum/DCForumID2/1742.html) and here [http://portforward.com/help/doublerouterportforwarding.htm](http://portforward.com/help/doublerouterportforwarding.htm).

Swiveller

---

