---
title: "help with memtest86"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Zpinkt on 2010-05-11
hey, I'm new to using ubuntu and when I first got it I downloaded a bunch of programs and some never showed up and others I never found out how to intall so a few days ago I decided to look for stuff that's never being used and delete (my disk space is running low) I left it there and when I came back it was running this memtest86 thing on a blue screen and I can't get out of there to use ubuntu.
please help me!
thnx to anyone who takes the time to help me out ^^

---

### Post by themusicalduck on 2010-05-12
When you boot the computer up, press shift when Grub starts to load and hopefully a menu will appear so you can see what options you have there.

Also, what did you remove? Anything kernel related?

---

### Post by Zpinkt on 2010-05-16
I don't think so, I just removed a bunch of games I had downloaded and also some text editors I had before I was told that openoffice is the most complete package for text, ppt and all that stuff.
when I boot it tells me I can push esc for more options and there it says that its going to the disks and then to kernel/memtest (or something like that) and I can edit that but nothing works so far

---

### Post by Zpinkt on 2010-05-16
this is what it says:
root ()/ubuntu/disks
kernel  /boot/memtest86+.bin

---

### Post by Zpinkt on 2010-05-20
Is there a way to get out of memtest?
when I try to boot (right before it gets into the memtest) it tells me I can hit esc and get options and there it says:
ubuntu memtest86+
windows loader
windows loader

when I hit edit ubuntu memtest86+
the commands listed in there are:

root /boot/disks
kernel /boot/memtest86+

can anyone tell me what I can type there instead of "kernel /boot/memtest86+" so that I can get out of that memtest loop?
cuz the only options under /boot/ (when hitting tab) are grub and memtest86+.bin and nothing under grub boots ubuntu.

---

### Post by jpeddicord on 2010-05-20
Merged back with your original thread; please don't make duplicates.

---

### Post by CharlesA on 2010-05-20
It looks like you deleted the kernel images, boot off a livecd and see what is in /boot/

---

### Post by Zpinkt on 2010-05-23
I have no idea what you've just told me to do -.-"
would you mind telling me how to do it?

---

### Post by CharlesA on 2010-05-23
Burn an ubuntu desktop iso to a cd and boot off it.

---

### Post by Zpinkt on 2010-05-24
thank you!

---

