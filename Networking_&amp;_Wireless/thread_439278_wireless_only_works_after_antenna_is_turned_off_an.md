---
title: "wireless only works after antenna is turned off and on"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by dskloet on 2007-05-10
Since a couple of days (since I returned from a 4 week trip), every time after I've rebooted my laptop (Fujitsu Siemens Lifebook S6120) or returned from hibernate, my wireless wasn't working until I turned off and on the antenna with the switch on the back. By "not working" I mean that no access points show up when I do a
[FONT="Courier New"]$ sudo iwlist scan[/FONT]
I could think of several reasons for this:
[LIST=1]
[*] During the trip I couldn't get my wireless to work because I needed WPA. I tried to get it to work and might have done something to my configuration that caused this, although I have no idea what that could be.
[*] During the trip I installed Fiesty.
[*] Maybe the antenna got damaged during the trip.
[/LIST]
Although I kind of ruled out the third option because it does work without switching off/on in Windows XP.

Any ideas what could be causing this or how I could solve it?
Any help is appreciated.

---

### Post by dlugidll on 2007-05-10
maby remove files 
/etc/network/interfaces
and then restart mashine
its work for me

---

### Post by dskloet on 2007-05-10
It seemed to have worked after rebooting. But when I returned from hibernate I had the same problem again. So now I'm not sure if I did have the problem after rebooting (which I normally don't do) or maybe only after hibernating.

Anyway, thanks for posting. Anybody else for a solution?

---

