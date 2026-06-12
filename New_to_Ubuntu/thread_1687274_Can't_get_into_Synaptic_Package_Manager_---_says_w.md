---
title: "Can't get into Synaptic Package Manager --- says wrong password"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Daanii on 2011-02-13
I'm trying to get into Synaptic Package Manager. It asks me for my password. I type it. It says the password is wrong. I've tried things like leaving the password blank, and typing in "password". No joy. 

I can't think of any way to get around this. Can I change the password somehow? The password I have still works for "sudo" commands.

---

### Post by jerrrys on 2011-02-13
if it works for sudo should work for synaptic.  try a reboot, see if you get lucky

---

### Post by coffeecat on 2011-02-13
Press Alt-F2 and run 'gconf-editor' (without the quotes). Now, apps > gksu. Is the 'sudo-mode' box ticked? If not, tick it and try Synaptic again.

---

### Post by jerrrys on 2011-02-13
yet another hidden feature of gconf; nice to know coffeecat

---

### Post by Daanii on 2011-02-13
> **jerrrys said:**
> if it works for sudo should work for synaptic.

That's what I thought too. But I'm sure I typed the right password. I've tried it now about 50 times. (Every three times I get it wrong, it closes. But I can open it and try again.)

>   try a reboot, see if you get lucky

I tried, and was not lucky. 

________________________

I did find a workaround. I typed in "sudo synaptic", then my password when it asked me to. That got me going in synaptic. 

It would be nice, though, to not have to do it that way. I'll have to see what I can figure out.

---

### Post by coffeecat on 2011-02-13
> **Daanii said:**
> I did find a workaround. I typed in "sudo synaptic", then my password when it asked me to. That got me going in synaptic. 

It would be nice, though, to not have to do it that way. I'll have to see what I can figure out.

If 'sudo synaptic' and 'gksudo synaptic' works, but 'gksu synaptic' doesn't, then you need to apply the fix I've already posted. Did you see it?

---

### Post by Daanii on 2011-02-13
> **coffeecat said:**
> If 'sudo synaptic' and 'gksudo synaptic' works, but 'gksu synaptic' doesn't, then you need to apply the fix I've already posted. Did you see it?

Sorry, I had overlooked your post. I tried to run gconf-editor. Apparently, it is not installed on my machine.

---

### Post by jerrrys on 2011-02-13
you have it

alt - f2

gconf-editor

---

### Post by coffeecat on 2011-02-13
> **Daanii said:**
>  I tried to run gconf-editor. Apparently, it is not installed on my machine.

:shock: Are you sure?! :-s

I suggest you re-install it. Yes, [COLOR=Red]re[/COLOR]-install it - it's part of a default installation. Did you uninstall it?

---

### Post by Daanii on 2011-02-13
> **coffeecat said:**
> Press Alt-F2 and run 'gconf-editor' (without the quotes). Now, apps > gksu. Is the 'sudo-mode' box ticked? If not, tick it and try Synaptic again.

I installed gconf-editor, followed your instructions to tick the box, tried Synaptic again, and it worked. Thank you very much.

---

### Post by coffeecat on 2011-02-13
> **Daanii said:**
> I installed gconf-editor, followed your instructions to tick the box, tried Synaptic again, and it worked. Thank you very much.

Excellent. Now that you've fixed it, here's some explanatory information. If gksu is not running in sudo mode (if that box is not ticked in gconf-editor) then the password it prompts you for is the root password, not your account password. And, of course, the root password is disabled/hidden/non-existent/whatever in Ubuntu. You may not have noticed this, but the window that prompted you for a password before you ticked the sudo-mode box was a different design from the one that appears when the box is ticked. 

Having said that, I'm curious to know how you managed to get a system that didn't have gksu running in sudo-mode (the default) and which didn't have gconf-editor installed (the default). You don't say which version of Ubuntu you are running. Are you running Ubuntu, in fact?

---

### Post by Daanii on 2011-02-13
> **coffeecat said:**
> Having said that, I'm curious to know how you managed to get a system that didn't have gksu running in sudo-mode (the default) and which didn't have gconf-editor installed (the default). You don't say which version of Ubuntu you are running. Are you running Ubuntu, in fact?

I'm running Ubuntu 10.10 on a BeagleBoard. The system has only 500 MB of RAM and a 4 GB flash drive as its hard disk. 

My experience is with Windows -- I'm new to Linux. But the BeagleBoard forums had enough instructions and software on them to get me up and running on Ubuntu. 

It looks, though, like I have a version of Ubuntu that is slimmed down to an emaciated degree. Probably needed to be to fit on the 4 GB flash drive and still leave room to work. 

In addition to not having gconf-editor, it did not have gedit or gcc. I've now noticed that it lacks the Archive Manager, having only an Archive Mounter instead. That one I still need to solve. I tried sudo apt-get install archive-manager. Didn't work. 

But in spite of the problems, I am glad to be learning about Linux and Ubuntu. Thank you for your help.

---

### Post by coffeecat on 2011-02-14
> **Daanii said:**
> I'm running Ubuntu 10.10 on a BeagleBoard. The system has only 500 MB of RAM and a 4 GB flash drive as its hard disk. 

....

 Probably needed to be to fit on the 4 GB flash drive and still leave room to work. 


Thanks for the information - interesting.

In the past I've put a standard Ubuntu on an EeePC 701 with 512MB RAM and a 4GB flash drive. A default Ubuntu consumes about 2.2 - 2.3 GB of space before you do any updates or installation of extra apps. Tight, but usable if you are careful what data you store on the internal drive. But I see that Beagle Board uses the ARM port of Ubuntu - of which I know nothing.

No gedit or archive manager - hmmm.

Good luck with your Ubuntu-ing! :)

---

### Post by Dojan on 2011-02-15
I had the same problem with a Ubuntu server install with ubuntu-desktop subsequently added, though gconf-editor was installed and did indeed solve the problem. 

Thanks! Stuff like this can scare the heck out of people new to linux, like myself... Unlike windoze though, here you actually get support. Thanks again!

---

### Post by jage on 2011-03-31
For the record I'm using Lubuntu and gconf-editor was also not installed.  It's a slim version as well.  Attempting to run gconf-editor will give you a proper install line if you do not have it.

Thanks for the solution!

---

### Post by DeMartini on 2011-06-23
> **Daanii said:**
> I installed gconf-editor, followed your instructions to tick the box, tried Synaptic again, and it worked. Thank you very much.

Thanks worked for me too!!:p

---

### Post by Gray Beard on 2011-06-29
I was looking for a way to install a 64-bit version of Lubuntu and found one. Simply put, install the 64-bit version of Ubuntu server and then use 'apt-get install' to put lubuntu-desktop (lxde) on top of the server. The installation process was easy (except for partitioning). After the system was up and running, the first problem I encountered was that I could not log in to Synaptic. I found the suggestion to use gconf-editor to set gksudo and gksu to sudo mode instead of su mode but lxde is not gtk so there is no gconf-editor. It did not occur to me to install the gconf-editor until I got to this post but fortunately I had already lucked out and found the following post somewhere else.
   "gksu and gksudo must look at the same /etc/sudoers directory that sudo does. Open a terminal, run [ gksu-properties ] and in the window that pops up, choose 'Authentication Mode: sudo'." I can't guarantee it will work on your systems but it worked like a champ on mine.
   I hope this information is of some value and thanks to all who contribute their knowledge, effort and time.

---

### Post by erixoltan on 2011-08-27
This was a very helpful tip.  I'm manually installing everything on a low-end system using xfce4 and gconf-editor was not installed for me either.

---

