---
title: "How to make VPN connect automatically after login (18.04)"
date: 2019-06-03
forum: Networking &amp; Wireless
---

### Post by goodstuff9 on 2019-06-03
I have a working VPN on Ubuntu 18.04.2 and GNOME shell 3.28.3.  

I can't see how to make the VPN connect automatically after I login.  How do I do that?  

I do not want the VPN available to all users.  

I want the VPN to start automatically after I log in, and I also want then to be able to control it using the standard network settings panel and have the VPN connect icon in the system tray to show that it is indeed still running.  

How do I do this?

---

### Post by james_creasy2 on 2019-11-25
I have the same problem. Ubuntu 18.04 and

$ cat /usr/share/gnome/gnome-version.xml
<?xml version="1.0" encoding="UTF-8"?>
<gnome-version>
 <platform>3</platform>
 <minor>28</minor>
 <micro>2</micro>
 <distributor>Ubuntu</distributor>



I found a website that shows a settings dialog that looks like:
[ATTACH=CONFIG]284484[/ATTACH]

But I only have:
 [ATTACH=CONFIG]284483[/ATTACH]

---

### Post by goodstuff9 on 2019-11-25
I found this the hard way, you need to enter this into a terminal:  nm-connection-editor , and then double click on the appropriate  connection for you in the resulting window, and in the general tab select the VPN(s) to automatically start with.

---

