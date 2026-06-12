---
title: "Start Up Menu Removed?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by jedimasterchief on 2011-06-15
Ok, so I have a dell xp computer. It got a virus, so I installed ubuntu 9.1. I have had no issues with it, until recently, when I used a windows restored disk in an attempt to fix windows. I installed windows...Long story short, I want to run linux again, but since I am not given any boot options, like I previously was, I can't unless I boot from a liveCD. 

I thought it was a GRUB problem, but I re-installed GRUB. And that was not the Start Up Menu. I believe I need to re-install the start up menu. I have no idea how to use grub, or how to remove it. I've never seen it before. 

Does anyone know how to do that?

I know I partitioned the drive and installed ubuntu on part of it.

So now when I boot up my computer it comes to 

"[minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>  "

I want to somehow get back to having this menu appear when I start up with it saying xp, instead of 7.
[IMG]http://i21.photobucket.com/albums/b263/jedimasterchief9/Ubuntu-1010_0281.jpg[/IMG]

---

### Post by silex89 on 2011-06-15
[This guide]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") might resolve your issue :)


This kind of problem is very documented though, if you don't get results with it, do a little research and I'm sure the solution will appear :D



Best Luck! :D

---

### Post by local user on 2011-06-15
Hi .. 

read this it may help u 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by nzjethro on 2011-06-15
I had this same issue. Chances are you may have forgotten to run
```
update-grub
```
Not to worry, you can boot from a live CD, chroot in (if one of the above links isn't how tho chroot, [this will help]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/"), else google it, it's a pretty straight forward process), and run update-grub. This solved it for me!
:D

---

### Post by jedimasterchief on 2011-06-15
@silex89 i did that and I installed grub. And now I have the problem I posted about. It didn't help. 

@nzjethro I tried to follow steps to update. I believe I followed them correctly. Nothing changed. I'll try again. There was one time, when the terminal listed all of my OS, but I don't know how/why it did.

---

### Post by nirab on 2011-06-15
could you post the content you your grub.conf after your grub reinstallation ?

---

### Post by nzjethro on 2011-06-15
> **jedimasterchief said:**
> 
@nzjethro I tried to follow steps to update. I believe I followed them correctly. Nothing changed. I'll try again. There was one time, when the terminal listed all of my OS, but I don't know how/why it did.

The terminal listing your OS would be it successfully updating grub. If it's still giving you grief, it may be because your grub is the wrong version. Grub 1.98 (in your original screenshot) is Grub2, while I think 9.10 uses the original grub. Try installing the older version of grub (unsure how to do it sorry, but I'm sure there's heaps of google help out there).

Also, if you want to follow  [these]("http://ubuntuforums.org/showthread.php?t=1291280") steps, and post the results here, it'll clear things up a lot.

---

### Post by jedimasterchief on 2011-06-16
Thanks for the help guys. I guess apparently I had grub2, not legacy grub. So I followed these steps of installing grub2. [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+reinstall](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+reinstall) 

number 14. And I was able to use a USB and not a liveCD.

---

