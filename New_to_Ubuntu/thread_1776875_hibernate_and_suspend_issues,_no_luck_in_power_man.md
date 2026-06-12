---
title: "hibernate and suspend issues, no luck in power management, 11.04"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by superpbeck on 2011-06-06
Still a young grasshopper in this field of Linux.  I'm having issues with hibernate and suspend.  Actually, as soon as my computer goes idle, I have to hard reboot.  Even with a screensaver activated, it will only be a screensaver for a couple of minutes and then the screen will go black.  No buttons wake it up.  I'm probably going to consider playing in oncoming traffic if this continues.

---

### Post by wildmanne39 on 2011-06-06
> **superpbeck said:**
> Still a young grasshopper in this field of Linux.  I'm having issues with hibernate and suspend.  Actually, as soon as my computer goes idle, I have to hard reboot.  Even with a screensaver activated, it will only be a screensaver for a couple of minutes and then the screen will go black.  No buttons wake it up.  I'm probably going to consider playing in oncoming traffic if this continues.
Hi, you can go into the screen saver settings make sure your screen saver is set not to come on and go into power management and set both the options in there to never go to sleep, I also have two screensaver settings on mine for some reason so make sure if you do, that both of them are set this way. I have not been able to let mine go into sleep because then I have to restart because it messes up my screen.

---

### Post by superpbeck on 2011-06-07
> **wildmanne39 said:**
> Hi, you can go into the screen saver settings make sure your screen saver is set not to come on and go into power management and set both the options in there to never go to sleep, I also have two screensaver settings on mine for some reason so make sure if you do, that both of them are set this way. I have not been able to let mine go into sleep because then I have to restart because it messes up my screen.

Gotcha.  Thanks.  Hopefully this gets fixed in the near future.

---

### Post by el_koraco on 2011-06-07
> **superpbeck said:**
> Still a young grasshopper in this field of Linux.  I'm having issues with hibernate and suspend.  Actually, as soon as my computer goes idle, I have to hard reboot.  Even with a screensaver activated, it will only be a screensaver for a couple of minutes and then the screen will go black.  No buttons wake it up.  I'm probably going to consider playing in oncoming traffic if this continues.

what kind of computer do you have? Am i assuming right in thinking it's an Asus?

---

### Post by superpbeck on 2011-06-07
> **el_koraco said:**
> what kind of computer do you have? Am i assuming right in thinking it's an Asus?

You are on the ball.  I have an Asus G73jh laptop.

---

### Post by el_koraco on 2011-06-07
[There's some work to do.]("http://ogrim.no/2010/12/suspend-problem-in-ubuntu-10-10-on-asus-n73jf-and-others/")

---

### Post by superpbeck on 2011-06-07
> **el_koraco said:**
> [There's some work to do.]("http://ogrim.no/2010/12/suspend-problem-in-ubuntu-10-10-on-asus-n73jf-and-others/")

Thanks.  I'll have to test this out.  It's not a huge problem since I messed around in power management and turned everything off, but I'd like to have a screensaver and not have to reboot my computer every time.

---

### Post by el_koraco on 2011-06-07
I did this on my sister's laptop, and it worked. to stop the computer from suspending when the screensaver is activated, you just need to go to the Power management (System Settings, under the shutdown icon menu - Screensaver), and untick the "Put display to sleep when idle" to Never. 

Applying these changes should help you be able to suspend.

---

### Post by el_koraco on 2011-06-07
here.

---

### Post by superpbeck on 2011-06-07
Yea, I did that in power management, I just need to make those files.  I'll post afterwards and provide a field report.

---

### Post by el_koraco on 2011-06-07
Yo!

---

