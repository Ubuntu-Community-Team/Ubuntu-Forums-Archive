---
title: "Removing un-needed applications - HELP !"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Chlorhydrikk on 2010-05-16
Hello,
It seems that I use only 10% of Ubuntu applications. I mostly surf on the computer, listen to music, watch videos/films and that's all!
What can I safely remove from my Ubuntu? (it seems that only Bluetooth is useful for me, I replaced Totem with VLC that is more lightweight, installed Wine and FileZilla).
Please help me to have the cleaniest Ubuntu possible !! I did not remove totally Totem as i still have the choice when playing a file between Totem and VLC (Totem of course doesn't run because i've uninstalled it...), so i'm a bit afraid about removing the other applications !

---

### Post by davec64 on 2010-05-16
If you've got the space, right clicking on the **Applications** menu and selecting **Edit Menu's** will enable you stop the applications from appearing in the menu (you can always re-enable them if you want to at a later date).

Using Synaptic and looking at the installed items is useful, but be careful removing certain things as occasionally other applications rely on certain applications being present. In the past if you removed anything with Evolution in the title certain other things failed to work (this might not be the case now!)

---

### Post by ed-koala on 2010-05-16
Unless you're strapped for space, I wouldn't worry much about the apps that come with Ubuntu.  Most take up little space and it doesn't slow anything down being there.

---

### Post by cuberts on 2010-05-16
> **Chlorhydrikk said:**
> Hello,
It seems that I use only 10% of Ubuntu applications. I mostly surf on the computer, listen to music, watch videos/films and that's all!
What can I safely remove from my Ubuntu? (it seems that only Bluetooth is useful for me, I replaced Totem with VLC that is more lightweight, installed Wine and FileZilla).
Please help me to have the cleaniest Ubuntu possible !! I did not remove totally Totem as i still have the choice when playing a file between Totem and VLC (Totem of course doesn't run because i've uninstalled it...), so i'm a bit afraid about removing the other applications !Just uninstall the applications that you dont want

---

### Post by -humanaut- on 2010-05-16
You can use the Ubuntu Software Center to uninstall the software you don't need. But as was mentioned above me if your not strapped for space theres not alot of reason to remove the programs.

---

### Post by Chlorhydrikk on 2010-05-17
I do have problems of space but I am also lost with too many applications that I really don't use (servers and so...).
I want a more personalized Ubuntu... And I hate having useless applications (like the ones that are pre-installed with a Windows computer...).
So, is it possible to have a list of all applications on Ubuntu? And how to remove them? I tried to remove Totem but as i have explained it it didn't work...

---

### Post by 3rdalbum on 2010-05-17
> **Chlorhydrikk said:**
> I do have problems of space but I am also lost with too many applications that I really don't use (servers and so...).
I want a more personalized Ubuntu... And I hate having useless applications (like the ones that are pre-installed with a Windows computer...).
So, is it possible to have a list of all applications on Ubuntu? And how to remove them? I tried to remove Totem but as i have explained it it didn't work...

Ubuntu doesn't ship with any servers. I don't even think the server version ships with server applications.

The default Ubuntu is pretty frugal anyway; you could remove F-Spot if you don't use it, you can remove Openoffice.org if you don't use it, remove Remote Desktop Viewer and Terminal Server Client if you don't use them.

Basically, anything you want to remove, try it. But if you get a warning that you're going to be removing a LOT of packages or any packages that seem pretty essential, like gnome-panel or gdm, then click Cancel and don't remove them.

I'd recommend using Synaptic Package Manager to remove any packages you don't want.

If you don't understand what something is, it's a very good idea to keep it.

Note that removing programs will not make your computer faster. It will only free up disk space. I remember removing the Gnome Power Manager on desktop machines, only to find that the computer would 'freeze' when you try to shut down; this was because the shutdown dialog would check with GPM as to whether your computer could suspend or hibernate, and it wouldn't find GPM and would just freeze.

So be careful, and if you can't troubleshoot these sorts of problems then just don't remove anything!

---

### Post by Rubi1200 on 2010-05-17
May I suggest you read this before deciding to remove anything:

[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-remove-any-application-that-s](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-remove-any-application-that-s)

As suggested before, if you don't use something just remove its entry from the menu.

---

### Post by Dayofswords on 2010-05-17
> **Rubi1200 said:**
> May I suggest you read this before deciding to remove anything:

[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-remove-any-application-that-s](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-remove-any-application-that-s)

i think they need to work on this not being an issue...

---

### Post by BoneKracker on 2010-05-17
If you are really of that mind-set, rather than starting with all the bells and whistles plus the kitchen sink, you could start with a minimal linux system and add just what you want.
[http://www.debian.org/](http://www.debian.org/)
[http://www.archlinux.org/](http://www.archlinux.org/)
[http://www.gentoo.org/](http://www.gentoo.org/)

If you are relatively new to Linux, I would not recommend that approach, though.  One of the nice things about Ubuntu is that it has a well-thought-out set of packages already installed and configured, without being really bloated.

Another possibility would be to try something like Xubuntu or Lubuntu.

---

