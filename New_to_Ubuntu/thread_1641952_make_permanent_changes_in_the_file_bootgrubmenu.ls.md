---
title: "make permanent changes in the file /boot/grub/menu.lst after the installation"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by danielij7 on 2010-12-09
I have seen a few threads on this, but I still don't know what to do.  I had to use F6 (other options) to get the CD to install.  The website says I'll need to "make permanent changes in the file /boot/grub/menu.lst after the installation has completed."  What changes do I make?  How do I make them?

I have *very* little knowledge of computer vernacular so please talk to me like I'm 3yrs old.  I'll know you're not being condescending, it's the only way I'll understand your instructions.  I have absolutely no experience with Linux, and very little with computers in general.

I am installing from a live installation CD onto a HP Desktop.

---

### Post by danielij7 on 2010-12-09
The installation has now finished and asked me to reboot.  I have, but now I have a black screen with a blinking cursor in the upper left corner of the monitor.  It won't go any further.

---

### Post by snowpine on 2010-12-09
Welcome to the forums!

There are some specifics missing from your post. The most helpful information you can provide is a) which Ubuntu release you are trying to install (10.10, 10.04, etc.) and b) which specific options you had to choose after pressing F6.

Ubuntu no longer uses a /boot/grub/menu.lst file, so "the website" you were reading is probably outdated. Starting with the 9.10 release, Ubuntu now uses GRUB2, [which is configured differently]("https://wiki.ubuntu.com/Grub2").

So basically if you back up a bit and describe to us exactly what problem you are having and which F6 options you needed to get around it, we can probably tell you how to make the change permanent. Don't worry that you are a beginner; these forums are a very friendly place. :)

---

### Post by danielij7 on 2010-12-09
Hi and thanks.  I'm installing Ubuntu 10.04 from CD.  Initially, when I tried to boot from the disk, the monitor would blink and tell me there was no signal after I selected install.  I used other options (F6) and chose nomode something and deleted quiet splash--.  It worked then during installation, but now that I have rebooted following the installation, I just have the cursor blinking on a blank black screen.

By the way, thanks a lot for your time and help!

---

### Post by danielij7 on 2010-12-09
I tried shutting down and restarting.  I'm getting a message on the monitor that there is "no signal" again, but I have heard the bongos from where the system has evidently started, but is not showing on my monitor.

---

### Post by snowpine on 2010-12-09
You're welcome!

I think you are talking about "nomodeset"; does that sound familiar? I have never dealt with this problem personally, but I found a pretty clearly-written tutorial that I think will help you: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

There are 2 steps you need to follow (details in the tutorial I linked to above). First you have to "temporarily set kernel boot options" so you can boot into Ubuntu in the first place. Next, you need to "permanently set kernel boot options." If any of the instructions are confusing to you, let me know which step you're stuck at, and I'll try to translate it into plain English for you. :)

---

### Post by danielij7 on 2010-12-09
OK, so I've tried multiple times now.  I am hitting e when the system boots and it (very quickly) flashes an error message that says something to the effect of "Error probing 001."  I think this is what it says anyway.  It is moving so fast I can just catch a glimpse of it.  Then, back to the ole monitor message "no signal" and it blanks out.

---

### Post by drs305 on 2010-12-09
The *'nomode' something* was probably "nomodeset".

As your system starts, hold down the SHIFT key. Hopefully the Grub 2 menu will display. With the first selection highlighted, press "e".

This will open the menuentry for editing.

Use the cursor key to move to the end of the "linux" line. It probably ends with "quiet splash". Use the cursor and DEL keys to remove "quiet splash" and replace them with "nomodeset".  

This is also where you should type in any other F6 options that you used to boot the CD.

Once you have typed "nomodeset"  (no quotes), press CTRL-x to boot and see if you now get a Desktop display.

Let us know if this works and we can tell you how to make this entry permanent.

---

### Post by snowpine on 2010-12-09
> **danielij7 said:**
> OK, so I've tried multiple times now.  I am hitting e when the system boots and it (very quickly) flashes an error message that says something to the effect of "Error probing 001."  I think this is what it says anyway.  It is moving so fast I can just catch a glimpse of it.  Then, back to the ole monitor message "no signal" and it blanks out.

I think you want to press 'Shift' first, then you can press 'e'. :)

---

### Post by danielij7 on 2010-12-09
OHHHH-

You guys are AWESOME!  It worked like a charm.  Thanks so much for your time!

---

### Post by snowpine on 2010-12-09
Yay! :)

---

### Post by drs305 on 2010-12-10
Have you added the "nomodeset" option permanently?

To do so, open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```
Add "nomodeset" to whatever you have in "GRUB_CMDLINE_LINUX_DEFAULT="

Example: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
If you don't have "quiet splash" or want to remove those items that is ok.

Save the file, and then update the Grub2 menu:
```
sudo update-grub
```

---

