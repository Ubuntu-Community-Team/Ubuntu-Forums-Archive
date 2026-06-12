---
title: "Ubuntu 8.10 Crashing on install startup"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by dorian246 on 2008-12-04
Hey guys, Im completly and UTTERLY new to Ubuntu, been a die hard windows user for years but Vista finally pushed me over the edge.

Anyways, I burnt the live cd and ran it on my laptop on start up no problem, checked for defects it all checked out and did a speed test and it was all 100% no problems. However, when I hit enter on install ubuntu, the loading bar comes up, it comes to a blank desktop with the cursor as an X. The laptop then quiets down like the cd's stopped running. if I hit enter or anything I can't move the X around anymore the system has completly crashed...I'm not really sure what the issue is.

I should mention its pratically the same issue when I try run it without installing it, except the cursor pops up to a white blank background (no desktop image) and when I hit anything again completly crashes.

Any help would be greatly appreciated as im ready to move on from vista. Thank you

---

### Post by Tatty on 2008-12-04
What are your system specs?

My first thoughts here would be to check the burn, but you have already done that.  Im wondering if it may be worth you installing it from the alternative CD - the LiveCD sadly does not work for every machine.

Get the Alternative CD here [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It looks a little less friendly, but the installer basically works the same as on the Live CD.

---

### Post by dorian246 on 2008-12-04
> **Tatty said:**
> What are your system specs?

My first thoughts here would be to check the burn, but you have already done that.  Im wondering if it may be worth you installing it from the alternative CD - the LiveCD sadly does not work for every machine.

Get the Alternative CD here [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It looks a little less friendly, but the installer basically works the same as on the Live CD.

Yeah I actually just did some re-search and started torrenting the basic one.

I hope it will work...im running a gateway vista, im not sure of all the specs off hand but 3 gigs of ram, intel core duo 2 proc. etc etc.

I dont need flashy just wanna get it working :).

I'll report back if that doesent change anything heres hoping it does!

---

### Post by Tatty on 2008-12-04
Ah good, well it should work.  Sometimes it just needs a little persuasion.

---

### Post by glennric on 2008-12-04
What kind of video card do you have?  Do you happen to have an intel chipset by chance?

---

### Post by handydan918 on 2008-12-04
This sounds like a classic case of having an nvidia or ati card that doesn't do well without the proprietary drivers. A search of the forums should give you some clues, if that's what it is. To find out, try hitting ctrl+alt+F1 and using the console to run ```
lspci
``` and look thru that list for the video info.

---

### Post by dorian246 on 2008-12-05
> **glennric said:**
> What kind of video card do you have?  Do you happen to have an intel chipset by chance?

Im actually about 95% postive it is.

as for hitting crtl-alt-f1 it just goes to a black screen saying loading please wait but it never does.....crashes.

---

### Post by dorian246 on 2008-12-05
Well thanks for all your help guys. The altreante install worked like a charm.

Got a LOT of work to do can't even figure out how to add a wireless setting but im sure i'll learn over time :).

---

