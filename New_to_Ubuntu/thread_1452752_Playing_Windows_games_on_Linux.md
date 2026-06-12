---
title: "Playing Windows games on Linux"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by HenrySkitsas05 on 2010-04-12
Hey, I'm new to Ubuntu. but I downloaded a game (Oddworld: Aves Oddysee) that says its compatable with windows 95 as an OS, I was wondering is there some way of playing it on Linux?

---

### Post by muteXe on 2010-04-12
You could see if it runs under Wine. Wine is in the repo's I think.

edit: this might be of some use:
[http://ubuntuforums.org/showthread.php?t=683826](http://ubuntuforums.org/showthread.php?t=683826)

---

### Post by sydbat on 2010-04-12
> **HenrySkitsas05 said:**
> Hey, I'm new to Ubuntu. but I downloaded a game (Oddworld: Aves Oddysee) that says its compatable with windows 95 as an OS, I was wondering is there some way of playing it on Linux?You need to install WINE. Go to System > Administration > Synaptic and search for wine.

---

### Post by HenrySkitsas05 on 2010-04-12
Whats the Termimal command to install wine?

---

### Post by sydbat on 2010-04-12
> **HenrySkitsas05 said:**
> Whats the Termimal command to install wine?sudo apt-get install wine

I would also look at the edit muteXe put in their post. That link will likely help you alot.

---

### Post by HenrySkitsas05 on 2010-04-12
Thanks guys. Sorry I really am a Ubuntu virgin so forgive me if I'm slow.

---

### Post by sydbat on 2010-04-12
> **HenrySkitsas05 said:**
> Thanks guys. Sorry I really am a Ubuntu virgin so forgive me if I'm slow.Nothing to be sorry about. We all started someplace.

And I have fixed my earlier post...added the correct terminal command.

---

### Post by karthick87 on 2010-04-12
Is it possible to install [COLOR=Red]NFS most wanted[/COLOR] using wine?

---

### Post by sydbat on 2010-04-12
> **getyourkarthick said:**
> Is it possible to install [COLOR=Red]NFS most wanted[/COLOR] using wine?[http://appdb.winehq.org](http://appdb.winehq.org)

More specifically - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8714&iTestingId=14223](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8714&iTestingId=14223)

---

### Post by e4uforums on 2010-04-12
Also check out PlayOnLinux.  Great front-end to WINE for the new Linux user.  It basically manages the different WINE versions for you - it also have some very nice install scripts.  It's all GUI based and very easy to use - no terminal necessary.

[www.**playonlinux**.com]("http://www.playonlinux.com")

I've used it to get a number of games running, even ones that aren't specifically mentioned by POL.

---

### Post by lanetherif on 2010-04-12
By the way, if the game is not available under Wine and if it is old enough ie. if it won't ask for 3D things and more than 128 mb of graphics, you can consider using a virtual machine.

---

