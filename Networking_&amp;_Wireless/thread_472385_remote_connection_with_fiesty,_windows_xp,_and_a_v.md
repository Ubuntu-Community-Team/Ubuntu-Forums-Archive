---
title: "remote connection with fiesty, windows xp, and a vista window( help plz)"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by BtJizzle on 2007-06-13
im not a network expert, but i do know the basics when it comes to computers. i now currently have a desktop with fiesty installed. Both of my sisters have their own laptop, one with windows xp media, and another with vista basic (they are all in same network). I want to find out a way how to connect to both of their laptops from my computer. what do i need and how do i do it? if anyone can help me, plz do. i would be so grateful.

---

### Post by maher_79 on 2007-06-15
r u talking about creating a network to be able to access their shared folders and visa versa or are you talking about remotly accessing their laptops?

---

### Post by BtJizzle on 2007-06-15
remotly accessing their laptops.......

---

### Post by finite9 on 2007-06-28
to remote access their desktops, you need some kind of remote control program.  VNC is available for all platforms so I would suggest that you install VNC server (free for personal use) on both their laptops then use vncviewer on your Fiesty PC to access them.  You can transfer the clipboard contents this way but not file transfer, with standard settings.  This is quite an easy solution.

You could try to enable Windows inbuilt remote desktop facilty (in Control Panel) on their PCs and use Terminal Server client from Fiesty, using the RDP protocol, but I have never really gotten this to work, and didnt investigate further, but it seems like the Linux client is a bit shaky.  I am unsure if you will see their mapped drives when connecting from linux like you would if you used RDP from one Win pc to another.

If you just want network access to shared folders then you need Samba installed on your fiesty box, which provides SMB network protocol which Windows uses, for Linux.

---

### Post by t4thfavor on 2007-06-28
to connect to the shared drives press Alt+F2 and then enter in 
smb://ipToTheLAptop it will ask you to log in.

for remote desktop I use terminal server client which is included in Ubuntu under  Applications --> Internet --> Terminal server client 

It works quite well. You may have to enable it on the two laptops, and I am not sure but vista basic may not have it installed at all. (unsure about Vista, because it only survived on my laptop for a week then I removed it forcefully and upgraded to XP.)

---

