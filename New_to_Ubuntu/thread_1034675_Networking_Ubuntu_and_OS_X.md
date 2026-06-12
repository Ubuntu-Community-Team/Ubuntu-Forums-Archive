---
title: "Networking Ubuntu and OS X"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by dabellator on 2009-01-08
Hey guys, I'm running Ubuntu 8.04 on a desktop wired to an old Linksys wrt45g wireless router which shares the internet with two macs running OS X 10.4.11.  Internet works fine through the router, but I want to leave my HP Photosmart printer plugged into the desktop and share it with all three printers.  Right now I'm not having any luck detecting the Ubuntu on the Macs, what should I do?  Thanks!
-JB

---

### Post by handydan918 on 2009-01-08
> **dabellator said:**
> Hey guys, I'm running Ubuntu 8.04 on a desktop wired to an old Linksys wrt45g wireless router which shares the internet with two macs running OS X 10.4.11.  Internet works fine through the router, but I want to leave my HP Photosmart printer plugged into the desktop and share it with all three printers.  Right now I'm not having any luck detecting the Ubuntu on the Macs, what should I do?  Thanks!
-JB
have you set up a share on the ubuntu box? Mac should talk to ubu ok, they both speak samba and ssh...

---

### Post by dabellator on 2009-01-08
I think I do.  I went to printers and enabled share published printers.  ive actually been able to get my ubuntu to recognize the printer settings on my mac, but no the other way around.  Would this fit better in a mac forum?  Thanks again.
-JB

---

### Post by handydan918 on 2009-01-09
Okay, try this. 
Since both OSX and Ubu use cups (common unix printing system) open a browser on the machine connected to the printer, and enter the ip 127.0.0.1:631
This should give you a nice web-based gui to configure your printer. You will need to config the "print server" which is just the cups daemon running on the box connected to the printer. 
Give that a shot, and post back if you get stuck. 
I really can't see any reason to get bogged down in samba if you don't have to tolerate the presence of a windows machine.

---

### Post by dabellator on 2009-01-09
I added the printer with the app you were talking about, and i was able to log into the same address on my laptop and print a test page, but I still can't get it to automatically recognize the printer in the add printer function.  I've tried a few different IP's, the desktop it's plugged into, the router, and the address you just gave me, but OS X won't find it automatically.

I know it works, since I can print the test page online, it's just a matter of the right setting.  If there were windows in the mix right now I would have several computer laying outside and a smashed front window.
-JB

---

### Post by handydan918 on 2009-01-09
Okay, assuming that the printer is hooked to the Ubu box, and the Ubu box has an IP of 192.168.1.2....
Get on the mac and open a browser. Type into the address bar 192.168.1.2:631
That should give you the cups page again, yeah?
Make sure that the priter is "published" and set as default.
My mac isn't hooked up right now, and I can't remember the interface in OSX to set up a remote printer, but it's gotta be simple point and click stuff.

---

### Post by dabellator on 2009-01-09
Well, i guess i solved my problem.  mac is just too intuitive, and here i've been trying to figure out something completely unnecessary.  turns out one does NOT need to add a printer on a network.  I was looking around and went to try printing a page and when I selected my printer I noticed I had a new option, so select a networked printer.

Case closed, thanks for your time, you made me a little wiser!
-JB

---

### Post by handydan918 on 2009-01-09
Glad to hear it. Macs usually talk to other *nix boxen pretty easy...

---

