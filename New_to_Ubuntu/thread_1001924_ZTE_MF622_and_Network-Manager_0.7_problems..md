---
title: "ZTE MF622 and Network-Manager 0.7 problems."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by uiaiu on 2008-12-04
Hello everyone!

I have a laptop with an Ubuntu 8.10/Windows XP dual-boot I have Network-Manager 0.7 and a ZTE MF622 USB Modem with a SIM card from Portuguese TMN, the connection worked for several weeks but now it does not work any more.

Some notes (maybe knowing this will help, maybe not):

- To make Ubuntu work in my laptop I had to edit a file, menu.lst if I recall correctly.

- The connection never worked perfectly, to make it start I had to boot Windows XP first write my PIN when the modem software asked for it then reboot to Ubuntu, try to connect once, it would fail, then go to the edit connection menu, select the connection then click edit then click ok, and then it would work.

- Before the connection stopped working there were some updates.

When I said the connection does not work I actually may be wrong, the problem is that the TMN named connection that I created no longer appears in the connection menu, having been replaced by "Auto mobile broadband (CDMA) connection".

The TMN connection still appears in the menu where I created  it, now with the new Auto (...) connection (that had never appeared before), but I do not have the option to use it to connect, and the Auto (...) connection always fails.

I tried deleting the new connection but it always appears again after some time, and even when I delete it from the editing menu it still appears in the connection menu except for one time when nothing appeared in the connection menu, even through the TMN connection exists.

I tried searching but I was not sure what I should be searching for.

The problem can probably be solved easily but I am an absolute noob. English is not my native language so it is likely that I made some mistake somewhere so if someone does not understand something I can try to explain it better. I hope this was the right place to post this and I am sorry for all the text.

---

### Post by colin james on 2008-12-05
I have the same problem. It would appear that an update has changed things as I booted my laptop from the original CD and the automatic CDMA was not present. I then configured my ZTE MF622 modem in Network Connections as mobile3 and went to network manager clicked mobile3 button and was connected. What has change and how can I get it working with the installed system? 

Thanks in advance for any help.

---

### Post by simonbanyard on 2008-12-15
I've had the same issue. I'm on the 3 network. The device worked out-of-the-box on a fresh install, but once I'd updated, it was broken. My Girlfriend has an Acer Aspire One with 8.10 on it, which I have *not* updated and it works fine. Strangly the update seems to have broken other things too. The Atheros chipset seems completely broken - even using madwifi. Seems odd.

UPDATE:

See [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968").

---

### Post by kapetus on 2009-01-08
I have made all that is on that "bugs launchpad" and I still can't connect with my TMN card, it recognises the modem but don't connect.

---

