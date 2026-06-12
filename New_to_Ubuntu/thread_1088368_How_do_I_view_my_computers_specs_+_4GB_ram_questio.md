---
title: "How do I view my computers specs? + 4GB ram question"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-05
In windows, I could just go to computer properties and it would tell me my computers specs.

I'd like to view them in Ubuntu, and see if it's showing up as using 4gb of ram.

The other question is, does ubuntu support 4gb in 32-bit like Vista 32bit?


Thanks. =]

---

### Post by trinidadflores on 2009-03-05
> **Gp. said:**
> In windows, I could just go to computer properties and it would tell me my computers specs.

I'd like to view them in Ubuntu, and see if it's showing up as using 4gb of ram.

The other question is, does ubuntu support 4gb in 32-bit like Vista 32bit?


Thanks. =]

system>administration>system monitor
then you click on the first tab

the 32bit maxes out at 3 gb.  the 64 bit is what you would need to use all 4 gb. just like myself i have 4 gb installed but because of having the 32bit i max out at 3 gb.
trinidad

---

### Post by williane on 2009-03-05
any 32bit OS can see up to 4gigs of total physical memory (this includes video mem, etc). so if you have a vid card with 512 ram youre already taking up half a gig of your 4gig limit. this is why you often times only see 3ish gigs of ram being used in a 32bit OS. 64bit can use much more. if you have <=4gigs of ram you wont lose too much using a 32bit OS. if you have >4gigs you'd def want to go 64bit (not that you couldnt still use 32bit, you'd just be wasting a lot).

im running 32bit ubuntu atm with 4gigs of ram and it shows 3.5 on my system monitor. if i installed 64bit it would show all 4

---

### Post by Gp. on 2009-03-05
Damnit.
Guessing theres no way to change 32-bit to 64-bit without re-formatting?

---

### Post by williane on 2009-03-06
nope. cant do an upgrade like going from xp to vista.

---

### Post by Gp. on 2009-03-06
> **williane said:**
> any 32bit OS can see up to 4gigs of total physical memory (this includes video mem, etc). so if you have a vid card with 512 ram youre already taking up half a gig of your 4gig limit. this is why you often times only see 3ish gigs of ram being used in a 32bit OS. 64bit can use much more. if you have <=4gigs of ram you wont lose too much using a 32bit OS. if you have >4gigs you'd def want to go 64bit (not that you couldnt still use 32bit, you'd just be wasting a lot).

im running 32bit ubuntu atm with 4gigs of ram and it shows 3.5 on my system monitor. if i installed 64bit it would show all 4

Does this mean the system is ACTUALLY using 4gb, it's just not showing as 4gb? Or I need 64bit to fully utilize 4gb...?

---

### Post by Somiac on 2009-03-06
It sees it, but 32-bit systems can ONLY utilize 3GB of ram, you have to have a 64-bit system to use more.

---

### Post by Svensk023 on 2009-03-06
> **Gp. said:**
> Does this mean the system is ACTUALLY using 4gb, it's just not showing as 4gb? Or I need 64bit to fully utilize 4gb...?

you need a 64-bit to utilize 4 or more GB of RAM, but i have seen how-to's on switching your kernel around to use up to 64GB RAM on a 32-bit ubuntu install, but it can cause problems.

---

### Post by williane on 2009-03-06
> **Gp. said:**
> Does this mean the system is ACTUALLY using 4gb, it's just not showing as 4gb? Or I need 64bit to fully utilize 4gb...?

if its showing 3.5g of ram then its using 3.5 of RAM, .5 is taken up somewhere else in the address space.

what i meant was that if you have 4gigs installed and its only using 3.5, youre not losing a whole lot (half a gig). whereas if you upgraded to 6, it will still only use 3.5 and you would be wasting 2.5. 

heres a great explanation. scroll down to the "32-bit Client Effective Memory Limits" section (2nd or 3rd section).

[http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx](http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx)

---

### Post by egalvan on 2009-03-06
OK, here we go again....

A DIRECT QUOTE from ubunut's Documentation.

[i]    *      [B]For [COLOR="Red"]32-bit systems[/COLOR] the [COLOR="Red"]Server Edition[/COLOR] is configured to use PAE which [COLOR="Red"]allows addressing up to 64GB of memory[/COLOR]
 while the [COLOR="Red"]Desktop Edition is configured for 4GB[/COLOR].

[Note] 	
When running a [COLOR="Red"]64-bit version[/COLOR] of Ubuntu  [COLOR="Red"]on 64-bit processors[/COLOR] you [COLOR="Red"]are not limited by memory addressing space[/COLOR]. [/B][/i]

(emphasis, italics and colors are mine)

Which is why I run the 32-bit Server Core with GNOME/KDE added.
With 8GB of RAM.


web-page:
[https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755](https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755)

---

### Post by LowSky on 2009-03-06
> **williane said:**
> any 32bit OS can see up to 4gigs of total physical memory (this includes video mem, etc). so if you have a vid card with 512 ram youre already taking up half a gig of your 4gig limit. this is why you often times only see 3ish gigs of ram being used in a 32bit OS. 64bit can use much more. if you have <=4gigs of ram you wont lose too much using a 32bit OS. if you have >4gigs you'd def want to go 64bit (not that you couldnt still use 32bit, you'd just be wasting a lot).

im running 32bit ubuntu atm with 4gigs of ram and it shows 3.5 on my system monitor. if i installed 64bit it would show all 4

OK this statement couldn't be more wrong!

32 bit will only read 3.2 GB of RAM, that is all without some kind of add-on (like PAE) that allows for more RAM to be used.

64bit can automatically see anything over 4 GB so it the best option if you have a newer processor (like the Intel Core line, or AMD64 Althlon or Phenom). Not to mention 4BG of RAM will most likely show up as 3.9GB

If you have the 32bit version of Ubuntu install you can add the PAE with a few mods, if your a noob it may look tough, so reinstalling with 64bit might seems a better option.
to use the server kernel here is the code to enter into a terminal, but be careful after the install you may have to reset up your video drivers and the like.
```
sudo apt-get install linux-server linux-headers-server
``` then just reboot and all your RAM should show up


sources
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by williane on 2009-03-06
> **LowSky said:**
> 32 bit will only read 3.2 GB of RAM, that is all without some kind of add-on (like PAE) that allows for more RAM to be used.

:grin: where did you get that number?

---

