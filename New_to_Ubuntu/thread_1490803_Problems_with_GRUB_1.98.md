---
title: "Problems with GRUB 1.98"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by MrRandom12 on 2010-05-22
In a vain attempt to change the default OS boot, after doing something (It probably had to do with GRUB re-installation) the usual GRUB boot menu has disappeared and was replaced by a command prompt, when I type in
```
boot
```
it will say
```
error: no loaded kernel
```
So I'm not exactly sure how to get back to the old menu. When details come back to me I'll say it.

Guides I was following.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If this is in the wrong section you can move it. But after searching the internet I didn't find any solutions.

Edit: I realized that I mistakenly did the "How to restore the GRUB boot loader", and accidentally messed up while doing it by mounting and installing into the /sda5/ instead of the /sda6/ that my laptop is using. In the middle of doing it I saw the Vista boot loader thing and was going to do that since it seemed simpler. When I restarted my computer it started to do that.

---

### Post by -humanaut- on 2010-05-22
Seems like your gonna have to boot into a LiveCD and configure your grub.conf file to correct your system.

---

### Post by w1ll1am on 2010-05-22
Hello I am not too sure what it is you are trying to do but if it is to reinstall grub and then change the default OS that it boots into do the following.

 Boot from a live CD or flash drive once loaded open the Termianl and type the following

   sudo grub  (you may have to use root grub)

   find /boot/grub/stage1

This returns a location. If you have more than one, select the installation that you want to provide the grub files for.
Then whatever was returned for the find command use it in the next line.

   root (hd?,?)

Use the values from the find command. If find returned (hd0,1) then you would enter root (hd0,1)

  setup (hd0)

Enter the command to install grub to the mbr (Master boot recorder)


Finally exit the grub shell

  quit


To chose what OS to boot too read this thread

[http://ubuntuforums.org/showthread.php?t=1457570](http://ubuntuforums.org/showthread.php?t=1457570) 

Hope this helps let me know

---

