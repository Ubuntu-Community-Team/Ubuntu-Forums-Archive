---
title: "Customizing Panel in Natty"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by The1nk on 2011-07-11
Hey all,
  I've installed the newest Natty distro, and it's my first non-Windows OS. ^_^;; I've decided to go for the Ubuntu classic rather than Unity simply because I like the Applications menu better. Because of this, I now have a panel across the bottom of my screen, similar to a Taskbar (Windows). I've grown extremely accustomed to Windows 7 prior to switching to Ubuntu, and now I'm wondering if there's any way to hide the text on the Panel buttons (for open applications/windows).

  Any advice would be greatly appreciated.

  Thank you!

---

### Post by wildmanne39 on 2011-07-11
> **The1nk said:**
> Hey all,
  I've installed the newest Natty distro, and it's my first non-Windows OS. ^_^;; I've decided to go for the Ubuntu classic rather than Unity simply because I like the Applications menu better. Because of this, I now have a panel across the bottom of my screen, similar to a Taskbar (Windows). I've grown extremely accustomed to Windows 7 prior to switching to Ubuntu, and now I'm wondering if there's any way to hide the text on the Panel buttons (for open applications/windows).

  Any advice would be greatly appreciated.

  Thank you!
Hi, in classic right click on the panel I choose remove then it will put the menu back in the window of the application that is open.

---

### Post by alquery on 2011-07-11
> **The1nk said:**
> Hey all,
  I've installed the newest Natty distro, and it's my first non-Windows OS. ^_^;; I've decided to go for the Ubuntu classic rather than Unity simply because I like the Applications menu better. Because of this, I now have a panel across the bottom of my screen, similar to a Taskbar (Windows). I've grown extremely accustomed to Windows 7 prior to switching to Ubuntu, and now I'm wondering if there's any way to hide the text on the Panel buttons (for open applications/windows).

  Any advice would be greatly appreciated.

  Thank you!

Hey, 

Looking around on the internet, I found this project, [Talika]("http://sourceforge.net/projects/talika/files/"). Click on the link, click on the latest version (talika-0.50), and then click on either of the .deb files depending on your architecture. If you don't know your architecture, just install the one that doesn't give you an error. Once, it's installed, right click on the bottom panel and select Properties. Set the size to about Windows 7-style length (maybe 50, perhaps?) Then right click again and hit Add to Panel. Scroll down to Talika and click Add. On your current taskbar, go to the very left edge of your first window open. Right click on the little three lines there and select Remove From Panel. Then drag the similar lines on your new taskbar to where the old one was. You can also right click on the lines and configure the taskbar (making the space between the icons bigger, etc.) That worked for me on 10.10, should work for you on 11.04.

---

### Post by The1nk on 2011-07-12
> **alquery said:**
> Hey, 

Looking around on the internet, I found this project, [Talika]("http://sourceforge.net/projects/talika/files/"). Click on the link, click on the latest version (talika-0.50), and then click on either of the .deb files depending on your architecture. If you don't know your architecture, just install the one that doesn't give you an error. Once, it's installed, right click on the bottom panel and select Properties. Set the size to about Windows 7-style length (maybe 50, perhaps?) Then right click again and hit Add to Panel. Scroll down to Talika and click Add. On your current taskbar, go to the very left edge of your first window open. Right click on the little three lines there and select Remove From Panel. Then drag the similar lines on your new taskbar to where the old one was. You can also right click on the lines and configure the taskbar (making the space between the icons bigger, etc.) That worked for me on 10.10, should work for you on 11.04.


So, following these steps has left me with a broken Gnome-Panel (I think) :P

What's happening is the entire Panel is gone, and my desktop icons are jumping up, then down, repeatedly. It feels like the Panel is opening, crashing, and trying to open again.

Looking for a way to fix this, and I'll be fine without the buttons if I can just get my Panel working again xD

Thanks!

EDIT: Using the tactic described here, [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html), I've now got a working Panel again .. no buttons, though.

Thanks ;)

---

### Post by wildmanne39 on 2011-07-12
Hi, did you try what I mentioned in my previous post before you went through all the trouble to do what the other post mentioned?
If you had read further down that page it was for a very old version of ubuntu and natty is different. Also that remove command is very dangerous it can delete your entire system. I am sorry I do not know how to fix this now,and I am sure the person that posted that does not either.

---

### Post by alquery on 2011-07-12
> **The1nk said:**
> So, following these steps has left me with a broken Gnome-Panel (I think) :P

What's happening is the entire Panel is gone, and my desktop icons are jumping up, then down, repeatedly. It feels like the Panel is opening, crashing, and trying to open again.

Looking for a way to fix this, and I'll be fine without the buttons if I can just get my Panel working again xD

Thanks!

EDIT: Using the tactic described here, [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html), I've now got a working Panel again .. no buttons, though.

Thanks ;)

Sorry about inconveniencing you. Must be some change between version 10.10 and 11.04, or I didn't describe what I did well enough.

PS: thanks for asking this, I liked the "Windows 7" style so much I'm going to keep it!

---

### Post by The1nk on 2011-07-12
> **wildmanne39 said:**
> Hi, did you try what I mentioned in my previous post before you went through all the trouble to do what the other post mentioned?
If you had read further down that page it was for a very old version of ubuntu and natty is different. Also that remove command is very dangerous it can delete your entire system. I am sorry I do not know how to fix this now,and I am sure the person that posted that does not either.

Honestly, I did not follow through with what you had recommended because I do not completely understand what you noted it will do --> > **wildmanne39 said:**
> Hi, in classic right click on the panel I choose remove then it will put  the menu back in the window of the application that is open.

It will put the menu back in the window of the application that is open? I think you may be referring to how in the Unity desktop the menus (File, Edit, View, what-have-you) appear in the top panel, rather than in the application itself. This is unfortunately not what I was looking to change :P

Just to clarify -- What I'm looking to modify is that in the bottom panel, it currently shows "Taskbar Buttons" (similar to Windows XP and prior), with icon and label text. I was looking to modify that so that it wouldn't show any text whatsoever, just the icons.

Thanks for your suggestions! :)

---

### Post by wildmanne39 on 2011-07-12
Hi,your right I was thinking of the top bar in unity, sorry about that.

---

