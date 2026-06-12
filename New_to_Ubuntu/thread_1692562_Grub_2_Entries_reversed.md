---
title: "Grub 2 Entries reversed"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by noorez on 2011-02-21
I have just installed Ubuntu 10.10 on my mom's laptop for her to try but I'm having some problems with the grub 2 entries.

This was her original default setup according to gparted (live cd)
/dev/sda1: toshiba system volume
/dev/sda2: windows vista installation
/dev/sda3: hddrecovery

I changed to this to install ubuntu:
/dev/sda1: toshiba system volume
/dev/sda2: windows vista installation
/dev/sda3: hddrecovery
/dev/sda4: extended
    /dev/sda5: ubuntu install
    /dev/sda6: swap

it installed fine except that the grub entries for windows that are displayed are displayed incorrectly:

grub menu:
/** linux entries and memtest ...**/
windows vista recovery (loader)
windows vista (loader)

"window vista recovery" loads the actual os and the "windows vista" loads the recovery manager.

any ideas on why this happened?

---

### Post by yeats on 2011-02-21
I've seen that happen too with GRUB and Vista - no idea why.  I figure there's a way to edit the text labels and all would be well, but I've never gone to the trouble since it boots without an issue.

---

### Post by Keiran230 on 2011-02-21
You should just be able to edit **/boot/grub/menu.lst** and change the text labels. You can also change the default to boot if none is chosen, and how long the screen will be displayed before choosing one automatically.

---

### Post by oldfred on 2011-02-21
With grub2 it is not so easy.

Some say this works for many things, not sure about names.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If the new entry works.
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

 More info:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by scotty2 on 2011-02-27
Just had the same experience.  Previous install had used Grub but a fresh install of 10.10 used grub2.  Now vista and vista recovery entries have descriptive text swapped.  I was fortunate in that I expected vista to be second last on the list with vista recovery at the bottom so I soon tried the other entry.  However, this type of difficulty could be a barrier to newcomers to linux, falling at the first hurdle.  It does not take much to put people off and being led to believe that their windows install has been totally trashed...

---

### Post by Quackers on 2011-02-27
Well it happened to me in my first Ubuntu installation and it didn't frighten me off :-)  I just tried to boot both entries and discovered they were mis-labelled. Not a show stopper really!

---

### Post by scotty2 on 2011-02-27
Found some information on this problem which refers to os-prober.
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2359918.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2359918.html)

My reading of this suggests anyone with Vista and a recovery partition is likely to have this problem.  Any thoughts?  Any one tried replacing the 20microsoft file using the one suggested in the aforementioned thread?

---

### Post by Quackers on 2011-02-27
Not me, as I don't have a Vista installation any more. But I know a man who has :-) I'll see if he's busy at the moment.
Thanks for the bug. I hadn't seen that.

---

