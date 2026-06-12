---
title: "Ethernet keeps going up and down (never connects)"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by chadk on 2006-12-18
In the messages log I see eth0 up, eth0 down every second.  It never connects to the net.
This started happening this morning when I booted up.

This same problem happened last week and I tried everything I could think of until finally I had to format the drive and reinstall dapper.

The NIC is a nVidia onboard nic.

I'm behind a router using DHCP.  DHCP is working fine for other boxes on the network.
On the problem PC I can ping localhost but nothing else.

I can't supply log files or anything becuase the PC having problems isn't on the network  -- hence this post.  It also doesn't have a floppy drive so I can't output the log to a floppy.  Does anyone have any ideas?  When I first install dapper, the network works perfectly.  When I installed flash on firefox it started failing (after a reboot).

I have installed flash using automatix2 and the problem started, but I also updated the kernel to 27 and had the problem again even after a fresh OS install.

So... I installed edgy.  Network worked fine for a while then flaked out.

This is when I realized what was going on (I think).

When I installed edgy, I disconnected the little Logitech Play Link that I'd been using recently (it's my wife's computer and she doesn't need bandwidth so a 10/mb half duplex suits her fine).  Anyway, I disconnected that, hooked up a lan cable and isntalled edgy.  I did this to increase the speed so it wouldn't take forever.  Everything worked fine, I updated all files, installed automatix2 and did the swiftfox and plugins install. rebooted, everything was still fine.
I moved her PC back to her desk, hooked up the logitech play link and rebooted.  Everything seemed to work just fine so I walked away.
Came back about 30 minutes later and moved the mouse to deactivate the screensaver and the network connection was gone.
I rebooted the PC and still no network.
I verified that the playlink was working properly by hooking it up to another PC. But in the process I also tried a new LAN cable between the playlink and the wife's PC.  NETWORK WORKING.
I rebooted, NETWORK IS STILL WORKING.

Hell, this could've all been caused by a faulty lan cable?!  It's possible, it's an old cable.
Time will tell.

---

### Post by chadk on 2006-12-19
New information regarding LAN cable added.

---

