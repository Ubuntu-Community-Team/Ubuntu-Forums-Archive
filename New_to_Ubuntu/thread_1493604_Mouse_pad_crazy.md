---
title: "Mouse pad crazy"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Kroms on 2010-05-26
I have a hp g62-144dx.  It has a trackpad that allows you to double click on the top left corner and disable the track pad.

Dualbooting win 7 / Ubuntu Lucid Lynx.
haven't booted into windows since I have installed ubuntu.
Mouse working perfectly.  Installed a track pad virtual two finger scroll - Works perfectly.

Booted back into windows 7 for the first time, installed dreamweaver, and then back into ubuntu.  Once I got back in, the light on the trackpad is on like it's been disabled?

Now when I try the two finger scroll it goes crazy and jumps all over the screen.  :(

I tried disabling the two finger scroll, and that works, but i can't get it to work perfectly again.

Anyone have any advice?


Edit - if I am on a long page, it scrolls ALLLLL the way to the bottom, and sometimes back to the top on it's own.

---

### Post by Jakiejake on 2010-05-26
> **Kroms said:**
> I have a hp g62-144dx.  It has a trackpad that allows you to double click on the top left corner and disable the track pad.

Dualbooting win 7 / Ubuntu Lucid Lynx.
haven't booted into windows since I have installed ubuntu.
Mouse working perfectly.  Installed a track pad virtual two finger scroll - Works perfectly.

Booted back into windows 7 for the first time, installed dreamweaver, and then back into ubuntu.  Once I got back in, the light on the trackpad is on like it's been disabled?

Now when I try the two finger scroll it goes crazy and jumps all over the screen.  :(

I tried disabling the two finger scroll, and that works, but i can't get it to work perfectly again.

Anyone have any advice?


Edit - if I am on a long page, it scrolls ALLLLL the way to the bottom, and sometimes back to the top on it's own.

First Of all welcome to Ubuntu and the Ubuntu Forums
Have you tried a normal USB/PS2 Mouse???

---

### Post by Kroms on 2010-05-26
> **Jakiejake said:**
> First Of all welcome to Ubuntu and the Ubuntu Forums
Have you tried a normal USB/PS2 Mouse???
Thanks!  Love ubuntu.  Haven't thought about windows since.

I have, it works, but the issue is I don't always have room for a mouse.  I would totally love to do that, but I'd really love to get this working once again.

---

### Post by Kroms on 2010-05-26
I have also plugged in the mouse to see if I can disable the orange light on the trackpad.

The light turns on at boot.  It used to turn off and then stay off when fully booted into ubuntu.

I can turn it off fine in Windows, but that's because of the drivers I think?  I looked on HPs website, but did not see any drivers available for any Linux distros.

---

### Post by Jakiejake on 2010-05-26
> **Kroms said:**
> I have also plugged in the mouse to see if I can disable the orange light on the trackpad.

The light turns on at boot.  It used to turn off and then stay off when fully booted into ubuntu.

I can turn it off fine in Windows, but that's because of the drivers I think?  I looked on HPs website, but did not see any drivers available for any Linux distros.

Have you searched for hardware drivers
Go to System -> Administration -> Hardware Drivers

---

### Post by Jakiejake on 2010-05-26
> **Kroms said:**
> Thanks!  Love ubuntu.  Haven't thought about windows since.


And I guarantee you won't go back
I had windows 7 ultimate edition (I BETA Tested It) Then Moved To Linux Mint 8 (Dual Boot) Then removed Windows 7 after a week or so then moved to Ubuntu 10.04 a few weeks ago
Never Looked Back/Regretted It

---

### Post by michaelA1330 on 2010-05-26
System -> Administration -> Hardware Drivers try messing about with your mouse settings as well

---

### Post by Jakiejake on 2010-05-26
> **michaelA1330 said:**
> System -> Administration -> Hardware Drivers try messing about with your mouse settings as well

No Copping :confused::(:confused::(
Come on read the previous posts...

---

### Post by Jakiejake on 2010-05-26
Oh and install all updates
System  -> Administration -> Update Manager

---

### Post by Jakiejake on 2010-05-27
Oh I love doing this
BUMP :popcorn:

---

### Post by Jakiejake on 2010-05-27
FYI I found this on the known bugs for 10.04 section

> Scrolling with ALPS Laptop Touchpads
Various users who have ALPS touchpads have reported that scrolling no longer works in the final release. A bug report is already open on the case, and the current workaround is to run:
Code:
sudo rmmod psmouse
sudo modprobe psmouse proto=imps
If this works, you can make it permanent by putting:
Code:
options psmouse proto=imps
At the bottom of the file /etc/modprobe.d/options

You may as well try it

---

### Post by Jakiejake on 2010-06-02
BUMP :popcorn:

---

### Post by cooltd825 on 2010-06-03
I have the G62, bought it about a month and a half ago.  I noticed the same problem on this too.  I can get two finger scroll and two finger right click working just fine with a patched Synaptics driver in Windows 7, but in Lucid Lynx 64 bit I cannot get two finger vertical or horizontal scroll working.  

I've messed with settings and was able to turn off two finger scroll entirely, and my screen doesn't whack out and go insane when I try to use it, but that means I'm stuck with scrolling with a specific side region.  I'm not sure if you all are familiar with this laptop, but having a region to scroll on this trackpad is VERY difficult.  The trackpad is completely integrated with the palm rests, even being made of the same material.  This trackpad is made to be used with two finger scroll.  I'm also pretty certain that it's Synaptics, not ALPS.  

Going to Hardware Drivers brings absolutely nothing on this laptop, having all open source drivers for the components on here (Atheros FTW :D)

If I can help with anything else, just let me know.

---

### Post by cooltd825 on 2010-06-03
As a note, when I do the "rmmod psmouse" command suggested above, I can actually use the entire trackpad.

With this standard Synaptics configuration, the bottom....  5th of my trackpad won't accept input.  I'm not sure why, but somehow the range of sizes for it is off.

---

