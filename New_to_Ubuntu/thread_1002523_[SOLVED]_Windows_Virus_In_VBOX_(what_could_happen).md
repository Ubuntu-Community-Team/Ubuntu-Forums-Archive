---
title: "[SOLVED] Windows Virus In VBOX (what could happen?)"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-05
Hypothetically If I were to get a virus on my Windows XP guest os in vbox, would that effect my whole computer.

I mean if it were one of those viruses that wipes out your hard drive would it effect my Ubuntu partitions or just the C: drive in vbox?

Sorry I don't really know of a better way to ask this question.

I hope it was clear

---

### Post by hyper_ch on 2008-12-05
not really... however if you do enable sharing between host and guest and the winxp guest has write access to the shared folder it may infect/delete files from the share.

Besides that nothing really can happen.

---

### Post by nakama85 on 2008-12-05
> **hyper_ch said:**
> not really... however if you do enable sharing between host and guest and the winxp guest has write access to the shared folder it may infect/delete files from the share.

Besides that nothing really can happen.

Thanks for the quick reply.

My concern was the fact that I did not really want to put a virus detector on the Xp install because it already runs slow as it is.

I feel a little sense of relief now.

Unfortunately the one and only reason I run xp in vbox is because I have a stupid zune (waste of $250, I wish I had found Ubuntu before I found the zune)
But is sound like as long as I backup My music to an unshared directory I will be ok.

Is this correct?

---

### Post by Tom--d on 2008-12-05
Like 99% of virus are for Windows.

You can do what you like to Windows in a VB. It will not affect your Host OS.

---

### Post by hyper_ch on 2008-12-05
well, windows viruses won't harm your linux install. As said, it can either infect files or delete/rename/... them...

So the "worst" things is that files could get deleted or you pass infected files to your friends...

---

### Post by nakama85 on 2008-12-05
> **hyper_ch said:**
> 
So the "worst" things is that files could get deleted or you pass infected files to your friends...
 no worries there. All my computers on my network are now running Ubuntu:D

---

