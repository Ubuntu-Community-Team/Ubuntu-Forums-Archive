---
title: "Wireless USB Linksys"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by mikev77 on 2007-12-08
hi. im a noob. I am trying to get internet to work. 

I did a lsusb. Here are the results:

bus 004 device 002: ID 13b1:000d Linksys
Bus 004 device 001: ID 0000:0000
bus 003 device 001: ID 0000:0000
bus 002 device 001: ID 0000:0000
bus 001 device 001: ID 0000:0000

I don't really know what my ESSID is or exactly what that is, or how to find out. 

When I have it set to roam, I can seem to connect but cant seem to get firefox to display any pages, or if it does, it is VERY slow and then craps out.

Like I said, I'm a noob. can i get an explanation in simple terms what to do?

---

### Post by rustybronco on 2007-12-08
> **mikev77 said:**
> hi. im a noob. I am trying to get internet to work. 

I did a lsusb. Here are the results:

bus 004 device 002: ID 13b1:000d Linksys
 your wireless device uses a rt2570 chipset so possibly it is a wusb54g v.4 nic (network interface card)

> I don't really know what my ESSID is or exactly what that is, or how to find out.  essid id is your network name or the name of a network you are trying to connect to.

> When I have it set to roam, I can seem to connect but cant seem to get firefox to display any pages, or if it does, it is VERY slow and then craps out.do you need roaming capabilities?

>  Like I said, I'm a noob. can i get an explanation in simple terms what to do?
as requested...

---

### Post by mikev77 on 2007-12-08
Thank you.

So what should I be trying to do to get it to work? A starting point for me to work on?

It seems to connect to my ESSID when I have roaming, but the Internet still won't work. (I say it seems to connect because the icon on the menu bar says connected at 87 percent, or whathaveyou, but my browser won't display anything or seem to be connected.) 

When it is not in roaming, it doesn't seem to be connected in any way.

I have tried changing various settings, but nothing seems to work. At some point I got it to start displaying a Web page, very slowly, but would never completely load the page. But now, I can't get anything to load.

---

### Post by mikev77 on 2007-12-08
Also, I thought about trying to blacklist some things, but I don't know how to do that or if that would help at all.

---

### Post by rustybronco on 2007-12-08
I'm in and out (like most people) could you post the output of  lshw -C network in a terminal?

and read  this post it will help you learn  [http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

---

### Post by mikev77 on 2007-12-08
I'm at work, but I'll post the output tonight. 

I had read that post before and was trying some different things and settings in it. I'm still learning. I think I might need to install ndiswrapper, but I'm not sure. Anyway, like i said I'll post the output later.

Thanks.

---

