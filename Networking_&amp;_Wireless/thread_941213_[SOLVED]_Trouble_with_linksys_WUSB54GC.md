---
title: "[SOLVED] Trouble with linksys WUSB54GC"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Washer on 2008-10-07
I can't get it to work. I hear it's supposed to work on hardy but some people have problems. It works from the livecd but not from the HD. How the hell do you fix this?

I tried following [this]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC") link, but i can't find the sources.

I'm using a vanilla kernel, but I don't think that's the problem. It doesn't work from the stock ubuntu kernels either.

---

### Post by Washer on 2008-10-07
tried ndiswrapper. Balls. :x

---

### Post by Washer on 2008-10-08
I tracked down the problem to "modprobe ndiswrapper" not working. Apparently you have to build ndiswrapper from [source]("http://sourceforge.net/project/showfiles.php?group_id=93482") if you're using a vanilla kernel, who knew.

Got that & got the 64 bit windows drivers from [somewhere]("http://ubuntuforums.org/showthread.php?t=516649")*. Works. Added ndiswrapper to /etc/modules & I think I'm all set until I want it to do something more complex like haxing WEP


*Never run scripts you don't understand.

---

