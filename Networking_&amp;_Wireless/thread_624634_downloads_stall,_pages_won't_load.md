---
title: "downloads stall, pages won't load"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by svriderpokey on 2007-11-27
Total Linux Noob.  I'm having problems with my network connection.  I'm using Gutsy.  I have a Linksys WMP54G internal wireless card, Comcast cable ISP, Motorola Cable modem, Dell wireless router, 64bit wep.  Two other XP machines (one wired, one wireless) work fine even while the problem is happening.  Same machine does not have the problem if I boot into either XP or the Gutsy live CD.

1 Firefox may or may not open a web page, then it will stop working altogether.  The spinning thing that tells you a page is loading goes for about a minute, then just stops moving, and the page stays white and never loads.

2. Synaptic package manager is having a similar problem.  often it is not able to update the server list.  If it does update the server list and I select packages to install, it will not finish the list before stalling.  It displays "unknown" as the download rate, and the expanded view just shows a stationary list of files.  Sometimes there are failed files, sometimes they are all "done" sometimes they will stop with some percentage of the download complete.  If I stop the update and restart it, it will continue at good connection speeds (about 500 kbps) from where it stopped the last completed file until it stalls again.

The problems may not always exist immediately after a boot up, but they will always show up, and soon.  I can't get anything done unless I use Windows.  Please help me.  I'm quite sick of windows.  TIA

Patrick

---

### Post by Digger78 on 2007-11-27
Try
```
sudo ifconfig <interface> mtu 1492
```

e.g. sudo ifconfig wlan1 mtu 1492

If it works add **mtu 1492** to the appropriate section of **/etc/network/interfaces**

---

### Post by svriderpokey on 2007-12-09
I don't get a lot of time at my computer, so sorry I haven't asked about this reply yet, but What does this line of command  do?

---

### Post by svriderpokey on 2007-12-10
That made it worse.  Before I could cancel out of the download part of the updater and restart it.  Now when it hangs up it won't download anything if I restart the "update."

---

