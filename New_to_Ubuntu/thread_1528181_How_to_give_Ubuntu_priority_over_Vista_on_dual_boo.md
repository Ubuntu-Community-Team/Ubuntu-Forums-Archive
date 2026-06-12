---
title: "How to give Ubuntu priority over Vista on dual boot"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-07-10
I've successfully installed Ubuntu 10.4 on my Acer laptop and would now like to give Ubuntu priority over Windows Vista when I turn on the computer. One post re another distribution mentioned editing a file called /boot/grub/menu.lst, but there's no file by that name in that directory on my Acer.

Bob Thomson, Ottawa, Canada

---

### Post by Zip247 on 2010-07-10
check this post for your answer.  Make sure you read the 3rd entry for a gui program that will alter grub for you.  

If you would like to learn more about grub and how it works, read the link in the 2nd entry.

[http://ubuntuforums.org/showthread.php?t=1527096](http://ubuntuforums.org/showthread.php?t=1527096)

---

### Post by Rex Bouwense on 2010-07-10
If you are dual booting and installed Ubuntu second it should already have priority.  How did you install Ubuntu - as a dual boot or inside Windows?

---

### Post by bthomson100 on 2010-07-10
> **Rex Bouwense said:**
> If you are dual booting and installed Ubuntu second it should already have priority.  How did you install Ubuntu - as a dual boot or inside Windows?

I installed Ubuntu 10.4 from a DVD, I guess within Windows Vista since that was the only operating system there before. I set the bio to look at the DVD/CD drive first, it ran something off the DVD (which had Unbuntu 10.4 on it as an ISO file) and after that, I was given the choice of (first) Vista, then (second) Ubuntu on start-up. I just want to reverse this order now.

---

### Post by nmaster on 2010-07-10
did you do something like this?: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

if so, then your using wubi.  you'll need to change the setting in the windows control panel for the windows boot manager.  its not hard to do, but its been a while since i did it so i don't remember exactly what to do.

---

