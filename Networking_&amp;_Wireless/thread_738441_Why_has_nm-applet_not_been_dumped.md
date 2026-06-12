---
title: "Why has nm-applet not been dumped"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by petermck on 2008-03-28
For several months I've struggled with Network Manager, PAM and nm-applet trying to get a convenient solution in place for managing wired and wifi connections.
 While I have managed to get it working it's always been flaky and quite frankly a bit embarassing compared to the ease with which XP and Vista handle wireless for friends with these systems. I'm no fan of Microsoft, but after nm-applet once again failed to authenticate my connection I began to wonder how Ubuntu will ever be a real contender on the desktop when there are problems like this and I began to feel depressed...:(
After the most recent  round of frustrations I decided to re-access the alternatives and came across [[COLOR="RoyalBlue"]_Wicd_[/COLOR]]("http://www.wicd.net"), which I had installed and working in less that 5 minutes compared to the ***days of wasted time*** I have lost with Network Manager PAM etc.:)
It's simple. That's the key. Wicd was easy to set up and it works, so why not use it by default in Ubuntu and dump the flaky, unreliable, frustrating Network Manager/PAM setup?

---

### Post by jimv on 2008-03-28
Try WICD ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/))

I've been using it for awhile, and I love it.
-This will remove NetworkManager
-to get the tray app to show up, you need to run /opt/wicd/tray.py

Also, you can try WiFi Radar.  It has a nice gui, and it leaves NetworkManager intact.
-should be in the repos

OOPS...I only read the problem part...I missed that you already have WICD

---

### Post by petermck on 2008-06-16
I successfully used WiCD on Gutsy, but reverted to Gnome Network Manager when I upgraded to Hardy. Unfortunately, it exhibited exactly the same problem as I have been experiencing for months on Gutsy and Feisty. 
I've now moved back to WiCD 1.4.2 and it works perfectly. If you find you are having the same problems with Gnome Network Manager and nm-applet, you can checkout WiCD at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php).

---

