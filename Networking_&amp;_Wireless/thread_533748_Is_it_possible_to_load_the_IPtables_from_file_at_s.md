---
title: "Is it possible to load the IPtables from file at startup?"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-24
In the same vain, I currently have my iptables setup the way I want them with guarddog, however again lose the settings when I reboot.  After reboot, I have to start guarddog up again, in order to repopulate the ip tables.  Is there a way to export the current IP tables for example in a file, and then load them manually at startup from the file rather than going through a program (such as firestarter or guarddog)?

I found this post: [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111).  Its close to what I want to accomplish, but not exactly.

---

### Post by Lars Noodén on 2007-08-24
The link you provided is quite good, you can use the second one (/etc/init.d/iptables) as a base for your own shell script:
    [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111)

The trick is that once the script works, set the run levels so that it will start automatically.  After that, make the changes you want and when they work use  [FONT="Courier New"]iptables-save[/FONT] to save your changes.  e.g.

[FONT="Courier New"]iptables-save > the-way-i-like-them.iptables[/FONT] 

and later to restore using [FONT="Courier New"]iptables-restore[/FONT] , e.g.

[FONT="Courier New"]iptables-restore <  the-way-i-like-them.iptables[/FONT] 

You can see that's the method in the second script.  

I'm unfamiliar with firestarter or guarddog, but if they work with IPTables, then configure IPTables using either one and then save using [FONT="Courier New"]iptables-save[/FONT]


--

If you want to be tricky, you can set different configurations for different run levels.  Have on for the home network, one for the wifi in the café, one for school, one for work, etc.

---

