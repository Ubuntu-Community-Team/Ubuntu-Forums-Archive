---
title: "How I got my WPC54g v5 working on Edgy"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by alexlindley on 2007-02-11
Hello,

I've spent the last week trying to get my Linksys WPC54g v5 working on Ubuntu 6.10 and had no success what-so-ever. I've reinstalled the whole OS and carried out different tutorials for installing the WPC54g wireless card more than I can remember.

I finally managed to get it working this morning!!

So if your having problems installing this card this is how I did it.

Reinstall the OS so you have a fresh install to work on.

Follow **[this]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")** guide word for word.

Although it doesnt talk about the linksys card itself the chip on it is exactly the same as you should see when you do a 'lspci' command in the terminal.

You need to follow the guide to the word in that you should install ndiswrapper 1.29 as it states.

When you get to the area about installing the drivers you will need the drivers from the linksys website **[here]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper")** (version 1.0.0.8).

Unzip the WPC54g.zip you just downloaded to your home directory and when it says in the guide to enter: sudo ndiswrapper -i Mrv8000c.INF
replace Mrv8000c.INF with LSMVNDS.inf

The rest of the instructions should work find and when you restart your laptop you'll notice the power LED light up when you hit the loading screen.

Hope this helps you, im so pleased I finally got this working!!


Alex

PS. a **HUGE **thanks to the people who wrote that guide originally.

---

### Post by erik.teichmann on 2008-01-24
Hooray! This worked perfectly for me. The lights don't seem to light up, but they are obnoxious anyway.

Thank youuuuuU!

This was on Dapper 6.06 by the way...

---

