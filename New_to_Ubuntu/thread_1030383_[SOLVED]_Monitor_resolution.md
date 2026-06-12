---
title: "[SOLVED] Monitor resolution"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-04
Hi Friends,

         I am new to Ubuntu and just installed ubuntu!!! The problem is i am having a 15 inch monitor but when i try to set the screen resolution system shows it as 14 inch and if i set the screen resolution to 1024 * 768 the picture is very tiny and if I go for 800 * 600 its too big. Normally I use 1024 * 768 in windows and it fits exactly in the window. Pls help me to fix this.

           I tried to change the resolution under System --> Preferences --> Screen Resolution. Is that the correct way of doing??? Thanks.

---

### Post by valros on 2009-01-04
The physical size of your monitor doesnt matter to Ubuntu, the possible resolutions do. With a 15 inch monitor 1024*768 should be the native(best viewed) resolution, its best to go with that unless its unreadable.

---

### Post by taurus on 2009-01-04
What kind of graphic card does it have and have you installed a driver for it, System -> Administration -> Hardware Drivers?

---

### Post by kestrel1 on 2009-01-04
Yes that is the correct place to change the sreen res.
Do you have proprietary drivers installed?
Check this under System - Administration - Hardware Drivers
Has the monitor been recognised correctly?

---

### Post by Jeyaganeshdj on 2009-01-04
Hi,

     I checked proprietary drivers and it says ATI/AMD proprietary FGLRX graphics driver is to be activated. I tried to activate it says an error msg systemerror: failed to lock and as /var/cache/apt/archives/lock. Other downloads thru update manager are running and is the error because of that? Thanks.

---

### Post by taurus on 2009-01-04
It means that you either have synaptic, add/remove, or adept running in the background.  Try it again later.

---

### Post by garrydog on 2009-01-04
Hi
I to have a screen resolution problem ,I have activated the ati/amd FGLRXT graphics driver as recommended ,trying to resize my desktop from 800x600 .
but I now have a black screen with "cannot display this video mode" ,and dont know what to do to get the moniter working again .
Can someone help please .

---

### Post by kestrel1 on 2009-01-04
garrydog:
If you boot to Recovery Mode & select xfix, that may solve it for you.

---

### Post by garrydog on 2009-01-04
Thanks for the reply ,but how do I boot in recovery mode .

---

### Post by gridd on 2009-01-04
> **garrydog said:**
> Thanks for the reply ,but how do I boot in recovery mode .

manually switch off then restart when you get to the install press the down arrow once to take you to recovery mode.

---

### Post by kestrel1 on 2009-01-04
If you don't get a grub menu, press ESC shortly after your computer POST's
From there select the recovery mode, normally second in the list & should look something like this:
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)

---

### Post by Jeyaganeshdj on 2009-01-04
Hi,

         I have installed the driver and the monitor works fine. Thanks for all ur replies.

---

