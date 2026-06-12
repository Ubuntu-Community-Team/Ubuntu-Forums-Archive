---
title: "Can't access Ubuntu installed on partition"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by MargaretA on 2011-01-01
After two days of trying I finally got Ubuntu netbook 10.10 installed on a partition - or at least I think I did. The process seemed to go smoothly; I found the empty partition (which I'd already set up using Windows XP Pro, the existing OS) and even figured out how to set aside a separate piece for "swap". But when I rebooted there was no option to choose Ubuntu - the computer loaded Windows automatically.

I can't see the Ubuntu partition in "My Computer," although it does show in Windows' Disk Management tool (it's not labeled, though). And Ubuntu is not listed in the Windows Programs menu - which is pretty much what I was expecting. But it *is* showing in the Control Panel for Adding or Removing Programs. Except I don't want to uninstall it. I want to use it.

Isn't there supposed to be an option to boot into Ubuntu at startup? If not, how do I find it and use it?

Thanks in advance for your help.

Meg

---

### Post by sandyd on 2011-01-01
> **MargaretA said:**
> After two days of trying I finally got Ubuntu netbook 10.10** installed on a partition** - or at least I think I did. The process seemed to go smoothly; I found the empty partition (which I'd already set up using Windows XP Pro, the existing OS) and even figured out how to set aside a separate piece for "swap". But when I rebooted there was no option to choose Ubuntu - the computer loaded Windows automatically.

I can't see the Ubuntu partition in "My Computer," although it does show in Windows' Disk Management tool (it's not labeled, though). And Ubuntu is not listed in the Windows Programs menu - which is pretty much what I was expecting. But it *is* showing in the Control Panel for Adding or Removing Programs. Except I don't want to uninstall it. I want to use it.

Isn't there supposed to be an option to boot into Ubuntu at startup? If not, how do I find it and use it?

Thanks in advance for your help.

Meg
lemme clarify first.
a) Installing using wubi (ubuntu listing in the windows programs menu) is not installing on partiton
b) How did you install it? (i.e. booting from the cd or installing from the cd)

---

### Post by Ravenshade on 2011-01-01
> **sandyd said:**
> lemme clarify first.
a) Installing using wubi (ubuntu listing in the windows programs menu) is not installing on partiton
b) How did you install it? (i.e. booting from the cd or installing from the cd)

or from USB? (At least that was my method)

---

### Post by MargaretA on 2011-01-01
I downloaded this file:
ubuntu-10.10-netbook-i386.iso

to my Windows desktop and used Unetbootin to put it on a flash drive, then installed from the flash. I'm sorry, I can't remember the exact process after that; I've done this too many times and in too many different ways over the last couple of days and I can't keep them straight anymore. But I know I booted from the flash; I just can't remember whether I picked "try" or "install" at that point, but I think it was "install". Sorry, I'm just seriously confused at this point. I'm not used to having more than one way to install anything.

I hope that helps.

Meg

---

### Post by MargaretA on 2011-01-01
One other thing - I don't have Wubi - or Ubuntu - in my Windows Programs menu. I do have "Ubuntu Netbook" - *not* Wubi - showing on the list when I open Control Panels --> Add or Remove Programs.

Meg

---

### Post by sandyd on 2011-01-01
> **MargaretA said:**
> One other thing - I don't have Wubi - or Ubuntu - in my Windows Programs menu. I do have "Ubuntu Netbook" - *not* Wubi - showing on the list when I open Control Panels --> Add or Remove Programs.

Meg
it doesn't show up as wubi in the add/remove menu, wubi is just the name of the program thats used to install ubuntu inside windows.

---

### Post by ktat on 2011-01-01
> **MargaretA said:**
> I just can't remember whether I picked "try" or "install" at that point, but I think it was "install". 
I hope that helps.

Installing for the first time can seem tricky.

From what you've described it seems there may be a problem with where grub has been installed.

I've installed Ubuntu numerous times alongside XP with no problems.  Are the partitions for XP and Ubuntu on the same Hard Disk?  It may be that the MBR (master boot record) of the primary partition still has the xp boot settings and that is why you're not getting the option to boot into ubuntu.

---

### Post by MargaretA on 2011-01-01
OK, so it sounds like it is installed inside Windows. I don't understand how it does that, but that's fine; there's a lot I don't understand about this whole process :). How do I access it, then? Is it supposed to show as a choice on startup, or is there some other way I get it started?

Thank you.

Meg

---

### Post by MargaretA on 2011-01-02
[I]Installing for the first time can seem tricky.
[/I] 
And for the 12th time too :) Or at least it seems like that many.

*From what you've described it seems there may be a problem with where grub has been installed.*

What is "grub"?

*I've installed Ubuntu numerous times alongside XP with no problems.  Are the partitions for XP and Ubuntu on the same Hard Disk?  It may be that the MBR (master boot record) of the primary partition still has the xp boot settings and that is why you're not getting the option to boot into ubuntu.*

Yes, the partitions are on the same hard disk; each is 60 gigs (the full hard disk is 120). I've heard of the master boot record (from all the reading I've done lately about this), but don't really know much about it. Is it something I can change?

I guess I also don't understand what "installing alongside Windows" (any Windows) means. I *thought* it meant that Windows and Linux were on the same hard drive, but in separate partitions. But then I didn't think two different operating systems could exist in the same partition, and it seems I may be wrong about that.

Meg

---

### Post by Ravenshade on 2011-01-02
Not particularly wrong...it's actually quite sensible to install them in seperate places. But windows is quite...annoying when it comes to sharing it's information anywhere and everywhere...it's like a damn virus. 

On the other hand, you can install it on the same partition through the use of Wubi...else your Windows os will be quickly wiped out.

---

### Post by confused10 on 2011-01-02
I have no clue how to do anything I am soooo lost.

---

### Post by Ravenshade on 2011-01-02
psst - please open your own thread.

---

### Post by MargaretA on 2011-01-02
> **confused10 said:**
> I have no clue how to do anything I am soooo lost.

It's true, this needs its own thread - but I can sure sympathize. :)

I have accomplished one thing here, though. I have managed to turn off those animated smilies. So even though I haven't found my Ubuntu yet, at least my headache won't get any worse.

Meg

---

