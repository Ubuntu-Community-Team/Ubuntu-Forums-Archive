---
title: "Dual boot no longer works after Ubuntu update"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bradyg23 on 2009-08-17
Greetings,
I had Ubuntu and XP dual loaded on a laptop. Everything was working great until I downloaded and installed some Ubuntu updates. Now the XP option isn't working. Can anyone advise how to repair this?
 
Please be explicit, as I'm fairly new with Linux.
 
Thanks!

---

### Post by SolarOnline on 2009-08-17
It seems like the update has obviously changed some settings in the boot parameters.

You might find some help here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope this helps. It seems like quite a specific problem. It may be best to re-setup the duel boot from scratch as a last resort.

---

### Post by teutonic on 2009-08-17
> **bradyg23 said:**
> Greetings,
I had Ubuntu and XP dual loaded on a laptop. Everything was working great until I downloaded and installed some Ubuntu updates. Now the XP option isn't working. Can anyone advise how to repair this?
 
Please be explicit, as I'm fairly new with Linux.
 
Thanks!


Do you get the black and white 'dos' style menu inviting you to choose ubuntu or winXP when you boot up ?

I assume you do, and you choose winXP.  What exactly happens after that ? Does windoze try to boot at all ? Does the PC just reboot to the grub os menu selector again ?

If you can choose winXP and the PC tries to get there, keep tapping F8 as it boots and pick Safe Mode. Then if you can get to a safemode desktop you can do a restore point from start>help and support.

---

### Post by superprash2003 on 2009-08-17
also check out [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) , basically try reconfiguring grub

---

### Post by bradyg23 on 2009-08-18
I had posted this on behalf of a friend who was having the issue. I went to work with him yesterday to try to resolve the problem and found that his updates had just pushed Windows off the bottom of the page. When I arrowed down to find other options, Windows was still there.
 
I used your links and advice to clean up his GRUB so that he would only see the latest version and his Windows.
 
Thanks to everyone!

---

