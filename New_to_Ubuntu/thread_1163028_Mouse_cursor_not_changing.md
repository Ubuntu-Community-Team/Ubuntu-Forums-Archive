---
title: "Mouse cursor not changing"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-18
When I go into appearance>themes>customise>pointers and then select various mouse cursors, the changes are not reflected immediately. This is on a pristine install of 9.04. Other installs of 9.04 are fine as was the previous 8.10 one.

What could be the possible issue? The cursor does change if I log out and log back in. Minor issue I know but annoying nonetheless.

Thanks a lot

---

### Post by charliehorse55 on 2009-05-18
The mouse will only change when X is restarted - when you log out/log in or reboot your computer. 

X is an underlying component that runs your computer.

---

### Post by Andy06 on 2009-05-18
But it changed just fine in 8.10 and changes instantly in other installs of 9.04 as well. In fact it changes in my Live USB on the same system as well.

---

### Post by mvalviar on 2009-05-18
> **Andy06 said:**
> But it changed just fine in 8.10 and changes instantly in other installs of 9.04 as well. In fact it changes in my Live USB on the same system as well.

I got this same problem as well. On hardy and intrepid I changes the moment you click on a cursor theme. But on my install of Jaunty I had to relog for the changes to take effect. Quite inconvenient. Perhaps this is a bug because when I select a black cursor the cursor remains white (coz I haven't logged out yet) but turns black when I mouse over certain objects.

---

### Post by Andy06 on 2009-05-19
Yes, the rest of the mouse theme changes. The loading, busy etc cursors all change, just the pointer does not change. Only seeing this problem on some installs of Jaunty though, not all.

---

### Post by Andy06 on 2009-05-21
I think it *might* have something to do with the Nvidia 180 driver. All the other installs have Nvidia 177, 173 or generic Intel drivers. I had the 177 on my 8.10 install which was fine.

Mvalviar, which driver do you have installed?

---

### Post by ledzepjes on 2009-06-04
I am having this issue as well, but ironically, on my desktop with 9.04 the cursor changes to all pointers after logging out and back in. I understand that xorg is changing with every release but very inconvenient for something trivial or it should be explained in the menu if this is how it works now, but my laptop won't change to the one called "white glass" - or it does but it isn't grey like the picture, it's white in the middle but still transparent. It's not a biggie, but just wanted to mention it.

My desktop has Nvidia geforce 6600gt 128mb, and my laptop has ATI mobility radeon 9600. I do have emerald installed on my desktop but not on my laptop.

I'm not an operating system or hardware guru, but I don't see how hardware drivers would cause certain aspects of the cursor to not change. Especially since it worked in other versions of Ubuntu.

PS: is my spelling of ubuntu off, the spell checker is underlining it? uppercase and lowercase? I vote this needs to be added to the lexicon in the Ubuntu Forums spell checker.

---

### Post by Taiyou on 2010-02-01
I had the same issue.. Though relogging did the trick, automatic changes would be nice :)

---

### Post by JPtja on 2010-05-01
In 9.04 and 9.10 I had the same problem, but now it is even worse..
All pieces of the new mouse-theme changes immediate, but the mouse itself keeps to the original mouse. Also when I reboot after picking a new mouse, it doesnt change..

---

### Post by sysdrum on 2010-05-05
Same issue. I did a clean install my Desktop theme works and everything i reboot and the pointer goes back to default. The oddest thing I change the back to the cursor theme I want and save the them log out then back in theme works I shut down the computer come back later boot up and log in and back to the default cursor.
I checked my theme setting and it has the default cursor in the theme file i change it and the cursor becomes a black square.

Desktop-everything works but my Mouse theme
 
Proc: AMD Athlon 64 x2 5600+
Ram: 4 by 1024 of 667mhz 
Chip set: Nvidia
Video Card: Nvidia Quadro PCI-E Series 280nvs NV34GL

Laptop-Everything works perfect

proc: AMD Turion X2 2.0Ghz
Ram: 2 by 2048 of 667mhz
Chip set: Nvidia
Video card: Nvidia Quadro Mobile Series 330FX NV37GL


I have the same theme on my laptop and My desktop running the same 
10.4(lucid) 
Kernel 2.6.32-21-genric
Nvidia drivers 173.14.22 

****
The issue if you have a nvidia card has to do with the Cursor shadow setting. Goto NVIDIA X server Settings>Cursor Shadow> uncheck enable Cursor Shadow.
 
I tested with both the laptop and desktop. When I enabled it the laptop broke also.
This may or may not fix your issue.

---

### Post by nutellajunkie on 2010-10-17
Same happens with me, but only sporadically. I think ubuntu has a mind of its own when it comes to preferences :S

---

### Post by jtarin on 2010-10-17
> "the inconvenience of logging out"lol :)

---

