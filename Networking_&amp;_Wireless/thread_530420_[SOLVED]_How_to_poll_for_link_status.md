---
title: "[SOLVED] How to poll for link status?"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by bdk6m2007 on 2007-08-20
I have a problem where my ethernet Link goes away and sometimes doesn't come back (I think it's a HW problem but really don't know).  So I want to test for the link status and take action if it is down.
 
The only way I've been able to tell if the link is up or down is by looking at messages in /var/log/messages.  Is there another way?  An API?  Or some command line utility I can call to get this info?
 
As noted in [http://ubuntuforums.org/showthread.php?t=525503](http://ubuntuforums.org/showthread.php?t=525503) the connection stays active even though the link is down.
 
Any help greatly appreciated.  Thanks!

---

### Post by bdk6m2007 on 2007-08-20
I guess I need to bone up on my googling skills...... after many fruitless hours of searching I finally found [http://www.netadmintools.com/html/mii-tool.man.html](http://www.netadmintools.com/html/mii-tool.man.html) (the mii-tool) which does the job.

I checked this out on Ubuntu 7.04 and also Fedora Core 5 - an interesting twist is that while [FONT=Courier New]mii-tool[/FONT] seems supported just fine on Ubuntu, the FC5 manpage says that it is obsolete and replaced by [FONT=Courier New]ethtool[/FONT], which seems to also do the job just fine.

---

