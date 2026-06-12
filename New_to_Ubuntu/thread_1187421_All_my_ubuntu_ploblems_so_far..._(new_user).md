---
title: "All my ubuntu ploblems so far... (new user)"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by geirknappen on 2009-06-14
All my ubuntu problems so far: (I dont know what happenend whith the r i problems)
keyboard problems: 

in windos ctrl + alt + 2 would give me the at-sign @, but nothing happens in ubuntu


when i press copy paste from gedit to opera browser some symbols do not show. Example: 
¤ becomes \u00a4, 
ø becomes \u00f8 
æ becomes \u00e6 
å becomes \u00e5.

Make programs work:
In audacity the studio mix function is missing (to record all sounds on desktop)

In tuxguitar there is no sound when I open a file (.gp4)

In skype, call contact is not working

Thats all, so far...

---

### Post by camper365 on 2009-06-14
Why would Ctrl+Alt+2 give you the @ sign, just press Shift+2
I don't know about the other programs. Try Firefox and see if the problem with the symbols persists.

---

### Post by Miljet on 2009-06-14
I would guess that you are not using an English keyboard.

As far as the symbols changing, what you are seeing are the Unicode strings for the symbols. It means the same thing, just different ways of showing it.

Other than that, I'm afraid that I can't be much help.

---

### Post by zonination on 2009-06-14
To get unicode symbols in ubuntu, press CTL+SHIFT+u, release the keys, and then proceed to type the unicode number. When you're done typing in the code (which should look like _u123_ or something of the sort), just hit enter and that should convert the code to the fancy symbols you know and love.

¤ = a4
ø = f8
æ = e6
å = e5

Hope this helps! :)

---

### Post by pous on 2009-06-14
> **geirknappen said:**
> All my ubuntu problems so far: (I dont know what happenend whith the r i problems)
keyboard problems: 

in windos ctrl + alt + 2 would give me the at-sign @, but nothing happens in ubuntu


when i press copy paste from gedit to opera browser some symbols do not show. Example: 
¤ becomes \u00a4, 
ø becomes \u00f8 
æ becomes \u00e6 
å becomes \u00e5.


i had similar problems since my keybord is not the standard american one and the symbols got moved all around + had no ñ... here is my solution:
SYSTEM -> PREFERENCES -> KEYBOARD(not keyboard shortcuts)  
once it opens in the layout tab add the one that corresponds to your language/country.

another thing that i'm not sure if has to do with the symbols, check:
SYSTEM -> ADMINISTRATION -> LANGUAGE SUPPORT
once there make sure your language is fully installed

hope this helps your problems.

---

### Post by geirknappen on 2009-06-15
Copy paste problem only happens between gedit and opera/firefox, not bewteen openoffice and opera/firefox.  

I have norwegian keyboard layout and it was installed. I noticed in keyboard preferences the option to choose keyboard model. I have chicony kbr0108 but it seems like I could only choose from 4 other models. CTL+SHIFT+u seems to be too complex for me. My solution is therefore to only use openoffice for copy paste. 

@ solution: Altgr+2 gives me @ (not CTL+SHIFT+2)

My solution for use of skype, audacity, tuxguitar is to use windows xp when I need thoose programs.

---

