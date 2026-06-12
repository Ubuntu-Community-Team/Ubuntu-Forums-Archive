---
title: "Installed on windows, Extremely slow internet connection!"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by LastWho on 2009-10-16
Hi,
i just installed ubuntu8.10 on my laptop and due to a lack of space i installed it directly on windows (not dual booting)
one problem so far: extremely slow internet connection, about 23kb/s or it should be 1Mb/s
i am now on windows and here is my real speed on windows (tested it a second before posting):

[img]http://www.speedtest.net/result/594463434.png[/img]

I didn't edit any settings on Ubuntu, its freshly installed and had auto-detected my network

i'll reboot asap, to give you any details you want
thank you in advance


Edit: Ok i think the problem is with my dns, i sat it on windows to be the same as the one my ISP gave me

Please how do i configure my DNS on ubuntu? 

i tried to add the DNS to /etc/resolv.conf file with "gksudo gedit" but when i restart my connection DNS goes back to 192.168.1.1

Also tried: Edit connections -> Edit Eth0 -> IPV settings: 
Manual -> Add -> and i filled in the settings i have on windows

what should i do please? :(

---

### Post by mike555 on 2009-10-16
dns problems are usually the "lookup "times , where it will say at the bottom of your browser something like "looking up ***** " for a long time .......

---

### Post by LastWho on 2009-10-16
hi, 

> dns problems are usually the "lookup "times , where it will say at the bottom of your browser something like "looking up ***** " for a long time .......
at the bottom of my browser i get only: connecting to.. waiting... transferring data..

Please help guys, its 4 AM here and still straggling with this problem :(

i managed to set my DNS and other settings to look 100% the same as those on windows:

---

### Post by LastWho on 2009-10-17
Bump plz!! :(

tried also to disable IPv6 by following this:

> FIX:
found in Ubuntu help:

3.2.7. IPv6 Not Supported

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications ? Accessories ? Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

and when i rebooted, couldn't connect at all!!

---

### Post by 3rdalbum on 2009-10-17
> **LastWho said:**
> Bump plz!! :(

tried also to disable IPv6 by following this:



and when i rebooted, couldn't connect at all!!

IPv6 is mandatory in later versions of Ubuntu (for various reasons); it will be mandatory throughout the whole world some time some time next year when we run out of IPv4 addresses.

Are you connected to your network through wired Ethernet or wireless?

---

### Post by LastWho on 2009-10-17
Wired Ethernet,
actually because i didn't get answers here i posted in Network section,
[here is the thread]("http://ubuntuforums.org/showthread.php?t=1293493")
me and another user from the same country/ISP concluded that it must be our ISP who messed up with something lately that caused that problem :(

---

