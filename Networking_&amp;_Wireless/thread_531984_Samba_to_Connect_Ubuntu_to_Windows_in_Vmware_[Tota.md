---
title: "Samba to Connect Ubuntu to Windows in Vmware? [Total Networking Newb]"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by OzzyFrank on 2007-08-22
HI. OK, I am fairly knowledgeable in many things technical, and have made the jump from Windows to Linux pretty easily, but I am a TOTAL network newbie in Windows or Linux, though I have tried unsuccessfully in the past (or with very limited success).

Now, my question is not how to connect to a Windows box but how to connect to Windows running in Vmware within Ubuntu. I've been told to get Samba to do it, but I have no luck finding any folders I mark as "shared". I have Samba installed properly from what I can see, so can someone lead me on the path the getting it all going, PLEASE? Cheers

PS: I do have Vmware Tools installed and running in the virtual Windows, so that isn't it.

---

### Post by Tsu Dho Nimh on 2007-08-28
Uh ... me too.

The WIN2K guest in VMWare can see the shared directories on the other machines just fine. It can't see the directories on its host at all. 

The Samba client on the host used to see the shared directories on the other machines ... I was told by the VMWare help forums that I need ot be running a Samba server so the VMWare client can see the host folders, and now the host Ubuntu can no longer see the other machines. 

What's FUBAR?

---

### Post by OzzyFrank on 2007-09-05
No takers? I'm going to have to reinstall Windows XP into Vmware coz I can't activate it through Ubuntu's web connection. Boo hoo...

Besides, the main reason for XP in Ubuntu is not Photoshop or anything, as I can use the Gimp (and if need be go into Windows for Photoshop on rare occasions)... but the only thing that has be rebooting into XP is ebay's Turbolister, which barely runs in Windows, so has no hope in hell in Wine, hehe! (I assume it will run in Vmware, but it needs a Windows that isn't going to disappear in a few days, oh, and a web connection!).

PS: Unless you're asking about a program, FUBAR is a military expression for when a situation looks dire ("F*&$ed Up Beyond All Recognition")... like SNAFU ("Situation Normal... All F@#$ek Up!").

---

