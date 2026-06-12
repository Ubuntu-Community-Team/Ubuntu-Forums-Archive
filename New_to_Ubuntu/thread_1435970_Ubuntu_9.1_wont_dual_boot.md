---
title: "Ubuntu 9.1 wont dual boot"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by oziwombat on 2010-03-22
I have two P4 PC's both had Ubuntu 9.1 installed & both installed within Windows XP pro & both now wont boot Ubuntu . I get this message on this PC 
[ minimal bash .like line editing for the first word ,tab lists possible commands completions .]

[ anywhere else tab lists possiable device/file completions ]

sh:grub> 

Is there a way to fix this from live cd ?  Or link to a thread ?

I found one answer to run live cd & use terminal to run sudo fsck-y/dev/sda1  & this did not work .

Cheers Ozi

---

### Post by Doctor Mike on 2010-03-22
> **oziwombat said:**
> I have two P4 PC's both had Ubuntu 9.1 installed & both installed within Windows XP pro & both now wont boot Ubuntu . I get this message on this PC 
[ minimal bash .like line editing for the first word ,tab lists possible commands completions .]

[ anywhere else tab lists possiable device/file completions ]

sh:grub> 

Is there a way to fix this from live cd ?  Or link to a thread ?

I found one answer to run live cd & use terminal to run sudo fsck-y/dev/sda1  & this did not work .

Cheers OziWere both systems working with dual boot and failed after say an update?

It sounds like a grub problem. If it followed an update I could see how both were affected. Otherwise are the two computers networked together? If so it sounds like something affected the MBR of one and spread to the other. A full virus scan from a free live cd would be a good way to see if a malware program has caused this. Super Grub live cd can be used to repair the Grub if that is the problem.

---

### Post by undecim on 2010-03-22
> **Doctor Mike said:**
> Were both systems working with dual boot and failed after say an update?

It sounds like a grub problem. If it followed an update I could see how both were affected. Otherwise are the two computers networked together? If so it sounds like something affected the MBR of one and spread to the other. A full virus scan from a free live cd would be a good way to see if a malware program has caused this. Super Grub live cd can be used to repair the Grub if that is the problem.

The problem isn't a virus. OP said he installed "within Windows XP" which means he used Wubi, which sometimes breaks from Updates.

I don't know exactly how to fix it without some research, but I just wanted to clear that up.

I can try to help until someone with experience in it comes along though. Did you get any text before the "minimal bash..." line?

---

### Post by ubu newb on 2010-03-22
[COLOR=Navy]I had a similar problem.  I installed within Windows 7 using wubi and after an update I couldn't load ubuntu.  Don't full around with grub and terminal or you may loose the ability to log into Windows like I did.  

I finally installed Ubuntu in its own partition and I was able to get back into Windows.  First thing I did was uninstall Ubuntu in Windows.  All is working now.   Now maybe XP is different but I'm just sharing my experiences.   Good luck[/COLOR]

---

### Post by undecim on 2010-03-22
> **ubu newb said:**
> [COLOR=Navy]I had a similar problem.  I installed within Windows 7 using wubi and after an update I couldn't load ubuntu.  Don't full around with grub and terminal or you may loose the ability to log into Windows like I did.  

I finally installed Ubuntu in its own partition and I was able to get back into Windows.  First thing I did was uninstall Ubuntu in Windows.  All is working now.   Now maybe XP is different but I'm just sharing my experiences.   Good luck[/COLOR]

Yeah, Wubi is a bit of a mess. It's still in its early stages of life.

A real install is MUCH more stable, but so many people are scared of the p-word.

---

### Post by oldfred on 2010-03-22
There are some issues with wubi.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by ubu newb on 2010-03-22
> **oldfred said:**
> There are some issues with wubi.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


[COLOR=Navy]I wish you would have seen my post when I had the problem over the weekend :icon_frown:[/COLOR]

---

### Post by oziwombat on 2010-03-22
> **oldfred said:**
> There are some issues with wubi.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

I tried this , but where do I put the wubldi ? I tried dropping it in C Drive & did not help , put into Ubuntu folder & did not help ,opened Ubuntu folder & put it in winboot & no go . Ubuntu folder has 3 folders 1 Ubuntu logo & 1 uninstall-wubi . 

Both PC's have two hard drives & both have main H/d IDE & slave Sata , I deleted Ubuntu on spare PC , but found the Wubldi files on the Sata drive on this PC & this drive has an old XP operating sys on it ,could this have caused problem ?
I don't want to reinstall Ubuntu if this is likely to happen again .

Thanks for the help so far Ozi

---

### Post by oldfred on 2010-03-23
I do not use wubi but the instruction say this:
Move the file to "C:\"  to replace the faulty "C:\wubildr".

---

### Post by oziwombat on 2010-03-23
> **oldfred said:**
> I do not use wubi but the instruction say this:
Move the file to "C:\"  to replace the faulty "C:\wubildr".

Like I said ,tried that & I found that link before posting my problem . 
Will delete Ubuntu & reinstall .:confused:
Thanks Ozi

[B][COLOR="Blue"]OK All fixed . I put my XP disc in & repaired XP & now all working correctly . 
Thanks for the help .
Ozi [/COLOR][/B]

---

