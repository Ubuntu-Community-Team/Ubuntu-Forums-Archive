---
title: "Failed security update... not booting - plz help"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by nirsoft on 2010-04-17
I am new to linux . I have a dual-boot system with windows vista and ubuntu 9.10.

In ubuntu I was updating the important security updates but something went wrong and a message was displayed stating that not all updates could be downloaded from the server.
Hence, the kernel was partially updated.
Now that I try to start ubuntu, instead of showing the login screen, this is what is displayed -----

> 
[CENTER]GNU GRUB Version 1.97~beta4

[LEFT][ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>
[/LEFT]
[/CENTER]


[CENTER][LEFT]

I need help as I have no idea what the problem is or what I have to do.
Thanx
[/LEFT]
[/CENTER]

---

### Post by MichealH on 2010-04-17
Do you have a Live CD on you?

---

### Post by nirsoft on 2010-04-17
yes i do...

---

### Post by nirsoft on 2010-04-17
> **MichealH said:**
> Do you have a Live CD on you?

Yes I do...

I tried inserting the CD and then typed --

> sh:grub> boot /cdrom


but this was the result -

> error: no loaded kernel

---

### Post by warfacegod on 2010-04-17
Boot from your LiveCD and reinstall GRUB2.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics")

---

### Post by nirsoft on 2010-04-17
> **warfacegod said:**
> Boot from your LiveCD and reinstall GRUB2.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics)

I forgot to mention that I had installed ubuntu through **wubi**.
LiveCD might not work as I will first have to get into Windows Boot Manager..

Is there any possibility of reinstalling GRUB2 for a wubi installation??

---

### Post by warfacegod on 2010-04-17
See if this helps: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by nirsoft on 2010-04-18
> **warfacegod said:**
> See if this helps: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Yep.. thats exactly what I was looking for. Works fine now
Thanx a lot mate!!

---

