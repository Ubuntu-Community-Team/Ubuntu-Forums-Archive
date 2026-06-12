---
title: "I burned windows vista 64bit iso to a cd but need help"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by zxy on 2009-03-23
Ok so i burned a windows 64 bit iso to a cd at 10x speed with magic iso....but I dont know how to boot it, When I pop it in, it just shows 2 folders and a file

---

### Post by SuperSonic4 on 2009-03-23
If you burnt the ISO correctly you'll need to reboot and select boot from CD in the bios

---

### Post by karlr42 on 2009-03-23
Why are you asking here? It's an Ubuntu forum, not a Windows forum. You have to reboot the pc, then make it boot from the CD- usually press one of the function keys as soon as the power comes on, keep an eye on the screen and you should see "press f2 to edit boot options/setup" etc). That should bring up a menu where you can change the boot order, set CD-ROM to the top

---

### Post by perlluver on 2009-03-23
Would that be a pirated CD?  If so this question would be illegal.

---

### Post by theozzlives on 2009-03-23
Sounds like pirated software to me.

---

### Post by zxy on 2009-03-23
alright thank you, the reason i need to know this is because when i install ubuntu i received and error and am trying to repair it and my laptop only has the partition repair which is annoying. It never came with a Vista CD.

---

### Post by SunnyRabbiera on 2009-03-23
Ah thus the piracy, carry on ;) (really, I stopped caring ages ago :D)

---

### Post by linuxisevolution on 2009-03-23
Yea, no one cares anymore.. I will thereby admit that I just pirated windows 99. :) 

It's for an older machine. Who cares? Not like it's worth anything anymore...



You will need to boot from the cd(leave cd in drive and restart).




(PS: win99 is just a haxors version of 98)

---

### Post by Therion on 2009-03-23
> **zxy said:**
> ... When I pop it in, it just shows 2 folders and a file
That doesn't sound right at all.  You should have *several* files and folders for a bootable .iso CD/DVD of any operating system.  Methinks you need to unpack some additional files or look for a "Read Me" file on your CD...




/also quit caring some years ago...
//yarrrr...

---

### Post by zxy on 2009-03-23
gah i solved it

i press f2 and make the cd priority number 1. restart and press any key to load the iso. it loads and all but when i repair and restart i still see the vista or ubuntu option >.<

if i burned ubuntu again correctly and installed it correctly, will another option come up or will the second option be fixed >.<

---

### Post by linuxisevolution on 2009-03-23
Whats funny is I had lots of tabs opened and firefox named this one:

"I burned windows vista...."

---

### Post by presence1960 on 2009-03-23
> **perlluver said:**
> Would that be a pirated CD?  If so this question would be illegal.

probably is pirated...I may be incorrect but I think Vista media are DVDs.

---

### Post by theozzlives on 2009-03-23
Vista is on DVD, so is Windows 7 (Vista SP2)

---

### Post by amadeus266 on 2009-03-23
> **zxy said:**
> gah i solved it

i press f2 and make the cd priority number 1. restart and press any key to load the iso. it loads and all but when i repair and restart i still see the vista or ubuntu option >.<

if i burned ubuntu again correctly and installed it correctly, will another option come up or will the second option be fixed >.<

Sounds like you are trying to repair grub. If you are just trying to repair the boot sector, load the recovery option on the cd and type "fixboot", if that doesn't work then type "fixmbr". the second option will rewrite the master boot record and you will no longer have have grub menu and windows will load normally. If you then install Ubuntu either on it's own partition or WUBI, you will have grub back and the menu to select the operating system.

Piracy is not the problem if the above case is true.

---

### Post by zxy on 2009-03-23
erm....where do i type it?

when i load the iso it ask me if i want to it ask 

repair
restore
etc...

I dont see where i can type fixboot or fixmbr

---

### Post by anewguy on 2009-03-23
(A) - "it ain't a Windows forum - go search the net - plenty of instructions there"

(B) - I just installed Windows 1000 - it so cool - I got rocks around all my Windows.  What's really wierd is that the wind blows right through them.  It shows mud and dried grass at the top of the screen.  I was looking for help on horsepower, so I thought I'd try Windows help first - it asked me how many horses I had!  So cool, all the other versions kept talking about something they called "engines".  I also asked for help on Leonardo Di Vinci, but it said it never heard of him.  That 1 I don't understand - didn't he do something famous?

---

### Post by zxy on 2009-03-23
erm i just want the dual boot of ubuntu gone so i can re install it correctly :(

---

### Post by amadeus266 on 2009-03-25
> **zxy said:**
> erm....where do i type it?

when i load the iso it ask me if i want to it ask 

repair
restore
etc...

I dont see where i can type fixboot or fixmbr

choose the repair option, you should be able to get a command prompt in there.

---

