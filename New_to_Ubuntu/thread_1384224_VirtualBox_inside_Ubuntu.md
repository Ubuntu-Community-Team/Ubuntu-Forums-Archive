---
title: "VirtualBox inside Ubuntu"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by zeltera on 2010-01-18
I installed virtualBox on my laptop that use as OS Ubuntu 910. I created a vrtual pc that runs windows xp (I need sometimes XP). I installed guest additions - this should give me custom resolutions and resize for the XP window. 

But... I have only one resolution: 640x480, and no full screen. On full screen I see the XP window small on the middle of the screen, and not full screen.

What should I do to fix this?

Thanks,
Ady

---

### Post by SushiR on 2010-01-18
Set your desired resolution in Windows XP display settings...

---

### Post by zeltera on 2010-01-18
the only resolution I have is 640x480. I cannot change it. 

I run virtual box on other computer (win 2003), and everything works just fine. But on my laptop (ubuntu) the resize is not working (I think that this is becauze I cannot change the resolution - I have only one option: 640x480).

---

### Post by halitech on 2010-01-18
> **zeltera said:**
> the only resolution I have is 640x480. I cannot change it. 

I run virtual box on other computer (win 2003), and everything works just fine. But on my laptop (ubuntu) the resize is not working (I think that this is becauze I cannot change the resolution - I have only one option: 640x480).

do you mean you only have 640x480 for options in Ubuntu for the screen size? if so, this is why you can't change the resolution in Virtualbox. You will need to get more options in Ubuntu before worrying about the virtualbox install of xp.

---

### Post by 3rdalbum on 2010-01-18
Install the Guest Additions within Windows to activate the virtual graphics card driver.

---

### Post by e-Gee on 2010-01-18
after installing guest additions did you restart xp vbox

---

### Post by zeltera on 2010-01-18
The Ubuntu is ok. No problems with the resolution on ubuntu. All the problems I have are only inside the XP (in virtual box machine).

**I instaled the Guest Additions inside XP**.
**I restarted the XP. (I even restarted the Ubuntu)**.
The problem is still there. I posted here because I don't know what else to try. I'm not a n00b, I'm using in many activities virtual machines (virtualBox or VirtualPC), but **the XP machine** I run under ubuntu makes me troubles. 

Thanks for all the answers and, if someone has some solution, please answer.

---

### Post by John Bean on 2010-01-18
I've occasionally had this problem with XP - both native and in VirtualBox - when it doesn't correctly detect the monitor (not the video card) for whatever reason and defaults to VGA. The fix I have used used is to change the monitor settings to something more realistic; sometimes just removing it in Hardware Manager to force a re-detect will do the trick, but if it still doesn't you can select it manually.

Once the monitor is set to something resembling reality then all resolutions supported by the video card are made available.

---

