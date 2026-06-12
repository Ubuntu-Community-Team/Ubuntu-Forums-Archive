---
title: "[SOLVED] Wireless networking issues with Netgear WG11v3 and WPA"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Cursula on 2008-12-30
Newbie needing help! 

Been on Ubuntu for a couple of days now.  It's been great so far except for my wireless internet connection.

Ubuntu 8.10 with a Netgear WG111v3 dongle. If I can turn off the security (WPA and WPA2) then I can connect. I haven't worked out how to do this reliably.. connecting can take several attempts.

With security active, I can't seem to connect.  Network manager shows connection, but I can't ping the router or use the internet.

I attempted a bug report fix in Terminal:
sudo renice 19 `pgrep wpa_`

The setting changed but it didn't seem to fix my problem
PS.  When I plugged the USB network card

Cheers :)

---

### Post by Michael.Godawski on 2008-12-30
hey, 

just as a side not you can read through:

[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html](http://godawski.oxyhost.com/solvingwireless.html)
[/LIST]
Now to your issue.

I guess you will have to use the ndiswrapper method as described here:

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)
[/LIST]
If you have questions concerning this guide feel free to ask.:D

Check out the ndiswrapper section in my guide posted first, there is also a graphic user interface for it, so you do not have to bother with all that code.

---

### Post by cmnorton on 2008-12-30
Is Network Manager prompting you for a key to enter?

If so, are you doing something like entering the translated hex key when you're being asked for the ascii key? The wording of the prompt was not clear to me, so to me it was a logical mistake.

If you have not already visited this page, you might want to:

[http://kbserver.netgear.com/kb_web_files/n101190.asp](http://kbserver.netgear.com/kb_web_files/n101190.asp)

---

### Post by joukez on 2008-12-30
[http://lists.ubuntu.com/archives/ubuntu-zw/2008-November/000255.html]("http://lists.ubuntu.com/archives/ubuntu-zw/2008-November/000255.html") 
Maybe this wil help you, just try and see

---

### Post by Michael.Godawski on 2008-12-30
Please do not double post.[-X

---

### Post by Cursula on 2009-01-01
Hi all,

Thanks heaps for the replies, and of course sorry for the double post (accidental)!!

Issue is now fixed.

I tried installing drivers using ndiswrapper, etc but that did not solve the issue.  I have since removed ndiswrapper and the netgear drivers because they are not necessary in Ubuntu 8.10.

In case someone else has encountered the same problem, I think that one of 2 things may have solved the issue:
-creating a new wireless connection myself (rather than using the AUTO one that Network Manager creates..) and/or
-upgrading the firmware on the router

Internet works perfectly with WPA now. :D

---

