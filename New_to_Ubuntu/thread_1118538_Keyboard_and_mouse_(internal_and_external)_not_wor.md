---
title: "Keyboard and mouse (internal and external) not working"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Davlav on 2009-04-07
Hello!

I installed Ubuntu on my work's laptop a few months ago and I liked it so much, I planned to install it on my personal laptop.
Unfortunately, it looks like there is an issue between the laptop and Ubuntu.

The laptop is an Acer Travelmate 4001.
I can start the LiveCD, but afterwards, the mouse and keyboard, internal or external, stop working.

I installed Fedora, but I prefer Ubuntu and I'd prefer it on my machine...

Any tips/ideas on what might be happening?

Thank you very much for your help!

David

---

### Post by roger_1960 on 2009-04-07
Hi

I had a similar issue with an Acer Aspire 5101.  It turned out to be a motherboard fault - not related to Ubuntu.  Solved it by completely removing, waiting a few minutes, and reinstalling the main battery (found this on another forum) - strange, but has now been OK for a year!

---

### Post by Davlav on 2009-04-07
Thanks Roger for your answer.

Unfortunately, It did not work.
I unplugged power and pressed the On/Off button for a while.
After booting, it did not improve.

I can use the keyboard to select the LiveCD option and choose it (arrows and Enter). When the system boots, I can move the mouse around, but the buttons do not work. Neither does the keyboard.

Ideas?

Thanks!

David

---

### Post by roger_1960 on 2009-04-07
Mmm...., did you actually physically remove the battery - didn't work until I did this.

---

### Post by Davlav on 2009-04-07
I did... :

---

### Post by roger_1960 on 2009-04-07
Hi again

Sounds like you are not alone:

[http://ubuntuforums.org/showthread.php?t=1001174](http://ubuntuforums.org/showthread.php?t=1001174)

[http://ubuntuforums.org/archive/index.php/t-1000229.html](http://ubuntuforums.org/archive/index.php/t-1000229.html)

Don't think I can help you as its not the same problem as I had...........

---

### Post by Davlav on 2009-04-08
Thanks for your help Roger!

I used the search function on the forums to find similar topics and I didn't found them...

I will study those threads!

Thanks,

David

---

### Post by Davlav on 2009-04-13
I found a solution for my problem.

It looks like old Acer machines used a chip integrating keyboard, mouse and battery functions that would not work properly.

On Debian, it is explained as Bug #37472 ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37472](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37472)).

As the problem is related to the battery, I fixed it through an 'Alternate' installation using the command "linux noacpi acpi=off" as boot option prior to the install ([http://ubuntuforums.org/showthread.php?t=257912](http://ubuntuforums.org/showthread.php?t=257912)).

Now I have a working Ubuntu machine without ACPI support, but with keyboard and mouse.

Thanks!

Best regards,

David

---

