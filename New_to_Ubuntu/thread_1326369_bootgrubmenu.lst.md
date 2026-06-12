---
title: "/boot/grub/menu.lst???"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by sudeepk on 2009-11-14
I just installed a ubuntu 9.10, i have a dual boot of vista and ubuntu. Now i want to edit the boot menu list. But i cant find the /boot/grub/menu.lst in the newer version. How can i edit it ??

---

### Post by edok on 2009-11-14
sudo gedit /boot/grub/menu.lst ??

---

### Post by Paqman on 2009-11-14
It doesn't exist any more, the new version of Grub did away with it.

Check the thread [here]("http://ubuntuforums.org/showthread.php?t=1302743") for tips on working with Grub2

---

### Post by Paqman on 2009-11-14
> **edok said:**
> sudo gedit /boot/grub/menu.lst ??

You should never use sudo gedit. Sudo is for command line apps, you should use gksu for graphical apps.

---

### Post by slakkie on 2009-11-14
> **Paqman said:**
> You should never use sudo gedit. Sudo is for command line apps, you should use gksu for graphical apps.

or kdesudo.. Although I also use sudo for graphical apps.

---

### Post by Paqman on 2009-11-14
True, I should have been specific:

Xubuntu/Ubuntu = gksu
Kubuntu = kdesu

---

### Post by edok on 2009-11-14
> **Paqman said:**
> You should never use sudo gedit. Sudo is for command line apps, you should use gksu for graphical apps.
so in cli *sudo gedit /xxx/xxx/file.ext* is wrong ?

---

### Post by Paqman on 2009-11-14
> **edok said:**
> so in cli *sudo gedit /xxx/xxx/file.ext* is wrong ?

Yes, because gedit is a graphical app. Whereas:
```
sudo nano /file/name
```

...would be fine, because nano is a command line text editor. You can read more about why on the [Psychocats Graphical Sudo]("http://www.psychocats.net/ubuntu/graphicalsudo") article.

---

### Post by edok on 2009-11-14
> **Paqman said:**
> Yes, because gedit is a graphical app. Whereas:
```
sudo nano /file/name
```

...would be fine, because nano is a command line text editor. You can read more about why on the [Psychocats Graphical Sudo]("http://www.psychocats.net/ubuntu/graphicalsudo") article.
cool! sudo nano for cli from now on, everyday something new is learnt!
Could you pls specify where/how to use sudo gedit with an example?

---

### Post by Bucky Ball on 2009-11-14
You wouldn't use it. You would use:

```
gksudo gedit
```

As mentioned, for the terminal it's 'sudo'. If you are going to open a GUI from a terminal it's 'gksudo'.

---

### Post by Paqman on 2009-11-14
To simplify the rule even further: [LIST]
[*]If it's an app that runs *inside* the terminal, use sudo.
[*]If it launches its own window, use gksu/kdesu
[/LIST]

Incidentally: gksu and gksudo is the same thing.

---

### Post by oldfred on 2009-11-14
Back to the OP's original question some simple changes can be done with SUM, it is still being updated for grub2.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by anewguy on 2009-11-14
Please excuse a couple of dumb questions:

(1) Does grub2 get installed if someone only does the upgrade, not an install of 9.10?

(2) I'm a little confused here - there is a setting that can be added to the kernel line to help some people with Intel graphics chips, but to keep an example simple, what does one do if they only wanted to do something like add NOSPLASH to kernel line?  

(3) From what VERY little looking at it I've done so far, it looks like it builds the menu on the fly now instead of from a fixed file.  Is this correct?

Thanks in advance!

Dave :)

---

### Post by ranch hand on 2009-11-14
I would leave SUM alone until it is fully compatible with grub2.  There have been some interesting conflicts created resulting in the need to remove grub2 and reinstall.

It is true that I have not heard on any in the last week so it may be safe.

---

### Post by ranch hand on 2009-11-14
> **anewguy said:**
> Please excuse a couple of dumb questions:

(1) Does grub2 get installed if someone only does the upgrade, not an install of 9.10?

(2) I'm a little confused here - there is a setting that can be added to the kernel line to help some people with Intel graphics chips, but to keep an example simple, what does one do if they only wanted to do something like add NOSPLASH to kernel line?  

(3) From what VERY little looking at it I've done so far, it looks like it builds the menu on the fly now instead of from a fixed file.  Is this correct?

Thanks in advance!

Dave :)
The menu is built from /boot/grub/grub.cfg.  That file does get over written every time "sudo update-grub" is run.

Grub2 is installed when you do a clean install of 9.10.  Upgrades stick to grub-legacy, at least in theory.

I would try any such addition by hitting "e" to edit your menu in grub2.  This way you can see if it works without any changes being actually made to system files.

If the entry works, I would make a custom menu file.  If you use the symbolic menu entry, it never needs editing again (we have had 3 kernel updates in 3 days in 10.04testing and my entries just boot to the newest one every time).

You could also add that to the /etc/default/grub file.

Which ever you did you would have to run "sudo update-grub" for the changes t otake effect.

---

### Post by anewguy on 2009-11-14
Thanks for the explanation!  I'll have to do some looking and thinking to see it all fit together.  The reason I asked about it is that I answered 1 post, and created just a generic one, regarding something I found on the net that seems to help people with 9.10 and Intel graphics chips.  I used the "old way" in those posts to reference how to make the change permanent once they had tested it via an edit at grub.  I guess I'll just wait for someone to post back wanting to know how to do it on an install instead of an upgrade.

Thanks again!

Dave :)

---

### Post by Paqman on 2009-11-15
> **ranch hand said:**
>   Upgrades stick to grub-legacy, at least in theory.


During the upgrade you should have had an option about whether to chainload from Grub legacy into Grub2. If you check yes then you actually end up with both, Grub loads Grub2 which boots your system. To get rid of Grub legacy you'll need to run the command:
```
sudo upgrade-from-grub-legacy
```

---

