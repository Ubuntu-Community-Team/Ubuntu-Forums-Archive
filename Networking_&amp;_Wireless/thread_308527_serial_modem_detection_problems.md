---
title: "serial modem detection problems"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by dckirba on 2006-11-28
Hello all,

I finally got my hands on a serial external modem! What joy! What happiness! In this land of windows and no serial cables, I found a 25 pin serial cable and an adapter to fit the 9 pin end on the modem.:-D 

Right. Ubuntu doesn't detect the modem. :( I'm not sure where to look in the hardware list and I have no idea how to find out which com port it's connected to so I can figure out what ttys* to use.:confused: 

Do I have to randomly go through each one and see if it works?

Is there something wrong with the modem?

I had it on and plugged in when I booted. I even restarted a couple of times to make sure.

I know I'm probably missing something basic here. I did read the wiki howtos as well.](*,) 

Funny thing is it sees my internal winmdem that doesn't even wok anymore.

Thanks in advance,
Cheers,
David K

---

### Post by PennYanPete on 2006-11-28
Hi dckirba

I see your post is down 4 pages and no reply, I'll try to help.

You didn't say what kind of modem you have, most important is rs-232 interface. Check [http://start.at/modem](http://start.at/modem) or google it.

Try ttyS0 first, it usually works for me. Ubuntu doesn't detect my modem, but it works.

It may be a good idea to remove or dissable the winmodem to avoid a conflict.

Configure it and give it a try, if you still have problems post back.

PYP

---

### Post by dckirba on 2006-11-29
Hi PYP,

Thanks for writing.

The modem I have is a Diamond Supra 56e. A google search tells me that it is linux compaible. It connects with a 9 pin serial cable. I beleive this is the same as the RS thingy?

I later logged on with windows and found out that I have a COM1 and an LPT1 port. The cable I have is a 25 pin one with an adapter on one end to fit the modem. I think what I've done is plug it into the printer port not the COM1 port.

This means I'll have to go and get anoter adapter to test my theory. That might hae to wait because I had fever last night that felt suspiciously like malaria so I'm staying home today :)

While we're on the topic, there are 2 types of serial interfaces right? 9 pi and 25 pin?

Printer ports are parallel, but one of their interfaces is the same as the 25 pin serial correct?

I don't know much about hardware, but its fun to learn. 

Thanks again,

Cheers,
David K

---

### Post by unisol on 2006-11-29
i have the same modem and it works fine what i did was right-click on taskbar and select add to panel then i selected the modemlights applet then click add. when its in the taskbar rightclick on modem app and click properties. fill in all your isp info username,password isp phone number etc. when you are finished right-click on modem icon and click activate. your modem will work on ttys0 or ttys1. good luck

---

