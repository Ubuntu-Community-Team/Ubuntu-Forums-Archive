---
title: "Can print to Windows printer, but nothing prints!"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by elbowgeek on 2006-11-29
This is a strange one: I've managed to connect to my Windows XP-attached printer, and it goes through the motions of loading the paper and moving the print heads across the page as if it's actually putting something on the page.  However, it actually prints nothing!  

It does have adequate ink, and prints fine from Windows.  This also happened six months ago when setting up a similar connection with a Windows printer from Ubuntu Dapper (which I'm using now), but it never got resolved as we switched to an all Windows environment.

Now I do wish to resolve the issue, so if anyone has encountered this before I'd appreciate any help.

Many thanks,

Dennis

---

### Post by trubblemaker on 2006-11-29
I've wanted to do this forever to so I'll keep my eyes out for any tips for you.  Also if you figure it out please post back here.

---

### Post by elbowgeek on 2006-11-29
Ah, good (or not so good?) to know that there's another with the same problem, and I'm not going crazy *grin*.

Seriously, keep an eye on this thread in case anyone replies.  Also, what kind of printer do you have?  Mine's an HP Deskjet 3550.  

Cheers

---

### Post by trubblemaker on 2006-11-29
LexMark E232 but had mutliple printers. It goes mad it I try and use the cups driver! It prints and prints and prints. Funny except for the dead trees.  Dead trees everywhere!....ok I'm calm again.

---

### Post by trubblemaker on 2006-11-29
haven't tried it yet but [found this howto]("http://ubuntuforums.org/showthread.php?t=32190")

also had a suggestions

[QUOTE=racecat ]What I ended up with was kdeprint, then I started adding smbclient, samba, and then smbfs. I had to reboot to get the network selection to show up in the kdeprint wizard, but it works great. I have a printer on a Win2000 box and my Ubuntu boxes are the only ones I don't have to manually log into the printer's machine before printing.[/QUOTE]

oh and you don't need kde to use some kde pieces in gnome but you might have to download some depenecies.

---

### Post by elbowgeek on 2006-11-29
I followed the thread on printing from Linux to Windows and got it to print using the Print Services for Unix in Windows. However it still prints nothing, just feeds the paper and pretends to print without actually printing anything.  

This is just wierd!

---

### Post by trubblemaker on 2006-11-30
I'll try the kdeprint tomorrow and let you know how it goes.

---

