---
title: "New User needs assistance changing brightness settings on Laptop"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by DocMcFail on 2011-08-17
Hi folks, new to Ubuntu and Linux in general. First time poster. I recently got a new laptop Gateway NV59C, and installed Ubuntu onto it. It duel boots with windows and is the type that can be removed like any windows application, probably off topic but just want to clarify my exact version.

The problem I am currently having, probably a common one is I cannot for the life of me figure out how to change the brightness settings for the LCD monitor. I've searched high and low on the internet searching all ways for the information but to no avail. Fn and nither the brightness keys or using Fn Up or Down do nothing to change the brightness. Also changing the brightness via Windows 7 doesn't change the brightness when Ubuntu is active. I have Ubuntu on my desktop and that was no issue in changing the brightness, my laptop as you can see is a different story.

Is there any universal sudo code or terminal input command regardless of the brand/model of the laptop? Any information or help will be greatly appreciated.

---

### Post by androssofer on 2011-08-17
> **DocMcFail said:**
> Hi folks, new to Ubuntu and Linux in general. First time poster. I recently got a new laptop Gateway NV59C, and installed Ubuntu onto it. It duel boots with windows and is the type that can be removed like any windows application, probably off topic but just want to clarify my exact version.

The problem I am currently having, probably a common one is I cannot for the life of me figure out how to change the brightness settings for the LCD monitor. I've searched high and low on the internet searching all ways for the information but to no avail. Fn and nither the brightness keys or using Fn Up or Down do nothing to change the brightness. Also changing the brightness via Windows 7 doesn't change the brightness when Ubuntu is active. I have Ubuntu on my desktop and that was no issue in changing the brightness, my laptop as you can see is a different story.

Is there any universal sudo code or terminal input command regardless of the brand/model of the laptop? Any information or help will be greatly appreciated.

Welcome to the forums! and the wonderous world of Ubuntu! :-).

if u click the ubuntu logo on the very top left, then search for "screensaver" then the screen saver program shud b listed. open that, then sumwer on tht it will say "power management" click that, and it should give you options for your brightness and similar things.....

***note*** (for the record)the Ubuntu installed as a windows program is called "wubi" and is less stable than installing it onto the hard drive as an OS on its own, so perhaps that is causing some issues....

---

### Post by HermanAB on 2011-08-17
$ xbacklight -set 50

Read the man page.

You can also do it with xrandr, but that method doesn't work as well.

---

### Post by ofnuts on 2011-08-17
> **DocMcFail said:**
> Hi folks, new to Ubuntu and Linux in general. First time poster. I recently got a new laptop Gateway NV59C, and installed Ubuntu onto it. It duel boots with windows and is the type that can be removed like any windows application, probably off topic but just want to clarify my exact version.

The problem I am currently having, probably a common one is I cannot for the life of me figure out how to change the brightness settings for the LCD monitor. I've searched high and low on the internet searching all ways for the information but to no avail. Fn and nither the brightness keys or using Fn Up or Down do nothing to change the brightness. Also changing the brightness via Windows 7 doesn't change the brightness when Ubuntu is active. I have Ubuntu on my desktop and that was no issue in changing the brightness, my laptop as you can see is a different story.

Is there any universal sudo code or terminal input command regardless of the brand/model of the laptop? Any information or help will be greatly appreciated.On my Kubuntu distro this is part of the power management stuff (perhaps because the display is one of the big power drains on a laptop). One click from the battery icon on the system tray...

---

### Post by Toz on 2011-08-17
You might also want to have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984") for another solution. Have a look at post #54 where a solution is listed involving kamal's customized kernel ([https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")) and a kernel parameter.

---

### Post by ofnuts on 2011-08-17
> **Toz said:**
> You might also want to have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984) for another solution. Have a look at post #54 where a solution is listed involving kamal's customized kernel ([https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-mjgbacklight")) and a kernel parameter.

Hey folks, is it that hard on a regular Ubuntu with Gnome/Unity? On KDE, it's two clicks (see attachment)

---

### Post by Toz on 2011-08-17
It all depends on whether your system properly acknowledges the brightness functionality. In a lot of cases, especially with Intel-based video cards, the brightness won't change using userspace application controls like the one you've shown since the brightness functionality is broken at the kernel level. Kamal has done alot of work in trying to fix the intel driver for upcoming kernel releases and releases a modified version of the kernel with his fixes included. The Gateway NV59C system that the OP has, I believe has an intel video card.

But now I'm curious. What kind of system and video card do you have?

---

### Post by ofnuts on 2011-08-17
> **Toz said:**
> It all depends on whether your system properly acknowledges the brightness functionality. In a lot of cases, especially with Intel-based video cards, the brightness won't change using userspace application controls like the one you've shown since the brightness functionality is broken at the kernel level. Kamal has done alot of work in trying to fix the intel driver for upcoming kernel releases and releases a modified version of the kernel with his fixes included. The Gateway NV59C system that the OP has, I believe has an intel video card.

But now I'm curious. What kind of system and video card do you have?That's a Lenovo Thinkpad T410. lspci says:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```(yes, single graphics card on that one)

---

### Post by DocMcFail on 2011-08-18
Hello folks, thanks for all the replies. I've been able to fix the brightness issue by using compiz fusion and allocating some hotkeys to it. I had to do an uninstall / reinstall of the Wubi Ubuntu file and things seem to be running smother this time. Dunno why it wouldn't let me do that the first time, but it works now. Again thank you all for the replies and support info. Being a brand new user it helps to know I can count on knowledgeable people!

-DocMcFail

---

