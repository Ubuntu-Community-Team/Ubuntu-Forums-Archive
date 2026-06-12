---
title: "Installed Hardware Drivers on.."
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Zilee on 2010-09-17
Hey, I just installed Ubuntu netbook edition and I wanted to enable multiple desktop switching so I was forced to install the drivers for my nVidia 9500m gs. I installed the (current) ones. 

After the installation I restarded and the UI looked worse and less responsive, with less effects than before. The screen savers were processed much better but the rest of the UI was total crap. Which is weird since I was now using the drivers of my GPU.

Anyways, so I went to enable normal desktop effects and it doesn't save the radio button selection. I kept pressing normal and it didn't pick any by default. Naturally alt+tab didn't work to switch between desktops.

I know my card is good enough, what should I do?

---

### Post by Zilee on 2010-09-18
Anyone:-k?

---

### Post by Zilee on 2010-09-19
Bump, a link or anything to point me in the right direction would already be helpful. I did my search and couldn't find anything specific to my issue.

---

### Post by alzie on 2010-09-19
Can you give a bit more information?  What is the computer you are trying this on and what version of Ubuntu are you using? ie 10.04

---

### Post by Zilee on 2010-09-19
> **alzie said:**
> Can you give a bit more information?  What is the computer you are trying this on and what version of Ubuntu are you using? ie 10.04

I am using Ubuntu 10.04 Netbook Edition. I have installed it on my Asus laptop which has an dedicated nVidia Gefore card(9500m GS).

I hear that desktop effects are turned off by default(Radio buttons grayed out), so I installed Compiz to enable the effects. 

Once I head to Appearance >Desktop Effects I select the mode. Then it prompts me to install Hardware Drivers for my nVidia graphics card, two options: ver173 or (current). 

Once I install the driver I restart my machine. Everything looks worse than it used to, the Ubuntu splash at the start is bigger and doesn't have a blur, the desktop doesn't animate itself and the scrollbar doesn't have rounded corners(Other stuff too).

But the thing is, once that's taken care of I go back to desktop effects tab and it lets me select an option from the three available radio buttons, but it doesn't save or do anything. Every time I go back to the desktop effect's tab there is nothing checked.

---

### Post by sandyd on 2010-09-19
> **Zilee said:**
> Hey, I just installed Ubuntu netbook edition and I wanted to enable multiple desktop switching so I was forced to install the drivers for my nVidia 9500m gs. I installed the (current) ones. 

After the installation I restarded and the UI looked worse and less responsive, with less effects than before. The screen savers were processed much better but the rest of the UI was total crap. Which is weird since I was now using the drivers of my GPU.

Anyways, so I went to enable normal desktop effects and it doesn't save the radio button selection. I kept pressing normal and it didn't pick any by default. Naturally alt+tab didn't work to switch between desktops.

I know my card is good enough, what should I do?
the boot screen issues are ok, they should be there.
I don't think that the remix screen was ever designed to run with nvidia drivers, that may be the reason why its having issues.

---

### Post by cariboo on 2010-09-19
Open a terminal and type:

```
sudo nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf file, reboot, and see if that makes a difference.

The netbook interface uses [maximus]("http://packages.ubuntu.com/lucid/maximus") as a window manager, so compiz won't work. If you want to use compiz, you'll have to use gnome-desktop, which is selectable from the login screen.

---

