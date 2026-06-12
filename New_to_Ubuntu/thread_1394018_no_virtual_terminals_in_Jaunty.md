---
title: "no virtual terminals in Jaunty"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by shawnisalk on 2010-01-30
Hi,

I've recently discovered that I'm supposed to have a number of virtual terminals available to me via ctrl-alt-f#. This is exciting because I get mighty tired of having to resize terminal windows every time.

[By the way, I'm using Ubuntu 9.04]

However, when I hit ctrl-alt-f1-f6 I get either a blank black screen or (more frequently) a screenful of colorful vertical lines (like I get on startup).

I've scoured the forums for info. This is what I've discovered so far:
The getty processes are happily running, and ctrl-alt-f7 brings me back to the desktop.
There is no "vga=" option set in grub's menu.lst.
Also, I'm using the standard video driver.

And this fix didn't work:
sudo modprobe vga16fb
sudo modprobe fbcon

More info:
When I switch to one of the virtual terminals and provide login info, name [enter], password [enter]
and then switch back with ctrl-alt-f7
and run who -all
I see that I am logged in at that terminal.
It's just not displaying.

Does anyone have an idea? I'm awfully frustrated at this point and would kill (well, not really) for a solution.

Any help would be greatly appreciated by me.

Thanks,
Shawn

---

### Post by NightwishFan on 2010-01-30
What sort of graphics hardware are you using?

---

### Post by shawnisalk on 2010-01-30
ATI RS482 (Radeon Xpress 200m)

---

### Post by NightwishFan on 2010-01-30
Did you try using any alternate drivers in System -> Administration -> Hardware Drivers?

Also try temporarily disabling compiz to see if that helps.

---

### Post by Rob@ThePCWiz.info on 2010-01-30
Delete Post Button?

---

### Post by shawnisalk on 2010-01-30
NightwishFan--I didn't, but I will. Thanks. (I'm just waiting for a system backup to finish :) )

---

### Post by shawnisalk on 2010-01-30
Rob--Thanks. I am able to login at the other virtual terminals, I just can't see what's going on because of those pretty lines (yes, the same ones you mention).

I did try switching between them, and that hasn't helped so far.

One thing I'm going to try is defining the vga=791 option in Grub's menu.lst config file which config's the terminal display to 1024x768. A post in another thread suggested this might be what's needed, so I'll give it a shot.

---

### Post by shawnisalk on 2010-01-30
Well, it turns out that there aren't any other drivers in Sys>>Admin>>HWare Drivers

I'll try disabling compiz if the vga=791 doesn't work

Thx,
Shawn

---

### Post by shawnisalk on 2010-01-30
Neither adding the vga= option to menu.lst, nor killing all of compiz's processes did the trick.
Also, again, there are no alternate hardware drivers installed.

However, maybe I'll try the one from the manufacturer and see if that works.

Any more thoughts?

---

### Post by shawnisalk on 2010-01-30
I tried installing the proprietary video driver, but that didn't change anything.

Anybody have any more thoughts?

---

### Post by Rob@ThePCWiz.info on 2010-01-31
> **shawnisalk said:**
> Rob--Thanks. I am able to login at the other virtual terminals, I just can't see what's going on because of those pretty lines (yes, the same ones you mention).

I did try switching between them, and that hasn't helped so far.

One thing I'm going to try is defining the vga=791 option in Grub's menu.lst config file which config's the terminal display to 1024x768. A post in another thread suggested this might be what's needed, so I'll give it a shot.
eek, i thought the post i put up there was kinda stupid of me, as i felt that i should have read through the whole post again... I'm a bit dyslectic and don't read things properly all the time.

---

### Post by shawnisalk on 2010-01-31
No worries. I think I'm just lucky enough to have a buggy video card.

It seems to me that in those virtual terminals there are only two things happening:
1. a login process
2. a display

If the login process works (it does) then the only thing left is the display.
If the display is configured properly (software) and it still doesn't work, 
then all that's left is the hardware.

Sadly, I suspect there is no solution for this issue except to buy another computer.

---

### Post by Rob@ThePCWiz.info on 2010-01-31
shawn, just get a new video card... I have a NVidea GEforce4 and it works after some SLIGHT and i mean VERY SLIGHT configuration. as in you need to edit a certain file (not sure what one) and add in your resolution (the highest it started at with me was 800x600)

---

### Post by peterbe on 2010-02-01
I have basically the same problem on an Averatec 3280 laptop - console screens tty1-tty6 show up as an array of colored blotches, I can log in and type commands, but can't see what I'm typing. I can get back to X with Alt-F7. This one of a number of problems I have described in Launchpad bug #495553.

I think this is due to misconfiguration of the fbcon module. This is on Lucid 10.04 with Grub 2 - so there isn't a menu.lst file to configure, and I don't know how to configure the text fonts or resolution in Grub 2. Since this is a laptop, I don't have the option of changing a display board. ;)

(I'm typing this on a Jaunty system).

---

