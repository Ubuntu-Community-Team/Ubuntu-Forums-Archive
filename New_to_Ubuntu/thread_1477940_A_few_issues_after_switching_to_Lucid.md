---
title: "A few issues after switching to Lucid"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-05-09
Hello all!

I've been using Hardy for 2 years now, since its release and I must say I was happy with it. It worked flawless out of the box and was a great distro to learn Linux. Now, that the next LTS arrived I thought I should switch. So I did, but with a few glitches:
1. Network Manager is gone from the top panel. I heard is a bug and I hope it will be fixed soon, but if some of you can provide a solution, I'm open to suggestions. (I saw this thread [http://ubuntuforums.org/showthread.php?p=9262210#post9262210](http://ubuntuforums.org/showthread.php?p=9262210#post9262210) and it didn't help)
2. Updates don't appear anymore on the top panel (and I have the notification area). To find updates I must start the Update Manager manually from the Control Center.
3.Visual effects disappear suddenly, and I have to reconfigure compiz after I enable them again. (I think this has to do with the graphic cars, as I heard that nVidia cards have issues with Lucid - hope they will be fixed soon).
4.I have a build in webcam and the light is always on, so that means that the camera is always on. I've tried opening Cheese and then closing it, but it didn't work:light was (and is) still on.
Any suggestions to turn it off?

My system is an ASUS laptop, 1.6 GHz AMD Turion64 processor, 2 GB of RAM, and a nVidia GeForce Go 7600 video card. I use 32 bit Lucid.

Any help that you can provide would be greatly appreciated.
Cheers!

EDIT:
5. Screensaver would not work after I close the lid of the computer. Till I close the lid screensaver has no problem, if I close the lid and open it again screensaver would not come on, only a black screen (I had this problem in Hardy too).
6. In Hardy,If I wanted to play a game I would close compiz and replace it with metacity with the command 
```
metacity --replace
```.
In Lucid, if I do that, I loose all window borders (where the minimize and close buttons are)  and the ability to type anything (either in a terminal or in a document). I can close the files if I go to File - Close window, but I can't input any command in the terminal, and this is really annoying.

---

### Post by rasmus91 on 2010-05-09
> 1. Network Manager is gone from the top panel. I heard is a bug and I hope it will be fixed soon, but if some of you can provide a solution, I'm open to suggestions.

If i was you i'd reset the gnome panels... I know thats a bit annoying, but that would be my solution.

I don't really know about the rest. But for the Nvidia thingie, try going to "hardware drivers" and check if it it the recommended driver that is activated...

Good luck.

Rasmus

---

### Post by Troll_the_Great on 2010-05-09
> **rasmus91 said:**
> If i was you i'd reset the gnome panels... I know thats a bit annoying, but that would be my solution.

I don't really know about the rest. But for the Nvidia thingie, try going to "hardware drivers" and check if it it the recommended driver that is activated...

Good luck.

Rasmus

How do I reset the gnome panels, and what implies this action?
In "hardware drivers" the recommended driver is activated.

---

### Post by Troll_the_Great on 2010-05-10
Bump!

---

### Post by howefield on 2010-05-10
> **Troll_the_Great said:**
> How do I reset the gnome panels, and what implies this action?

Entering the following 3 commands in terminal will reset your panels to default. The way they are after a fresh install.

```
gconftool-2 –-shutdown
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

However, it may not be the panels that are the problem, the update manager may have been "switched off" in your startup applications. Have you checked that ?

---

### Post by Troll_the_Great on 2010-05-11
> **howefield said:**
> Entering the following 3 commands in terminal will reset your panels to default. The way they are after a fresh install.

```
gconftool-2 –-shutdown
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

However, it may not be the panels that are the problem, the update manager may have been "switched off" in your startup applications. Have you checked that ?
Update notifier is not switched off in startup applications. I don't know if the panels are the problem or not.
Can somebody help me with the other problems?

---

### Post by philinux on 2010-05-11
Update notifier is behaving correctly. The change was made in Karmic. When there are update it will launch update manager.

Was this an upgrade or clean install?

---

### Post by Troll_the_Great on 2010-05-11
> **philinux said:**
> Update notifier is behaving correctly. The change was made in Karmic. When there are update it will launch update manager.

Was this an upgrade or clean install?

It was a clean install. But update manager will not trigger if I don't open it. Are you sure that's the correct way of operating?

---

### Post by philinux on 2010-05-11
See here to change the default behaviour.

---

### Post by Troll_the_Great on 2010-05-12
> **philinux said:**
> See here to change the default behaviour.

Excuse my ignorance, but I don't know how to get to the menu from where you took the screenshot... :(

---

### Post by philinux on 2010-05-12
> **Troll_the_Great said:**
> Excuse my ignorance, but I don't know how to get to the menu from where you took the screenshot... :(

Ah ok. Open a terminal and run this. 

```
gconf-editor
```

---

### Post by SKhan on 2010-05-12
Just because you are having issues with ferrari doesn't mean that bullock cart is any better. Stick to latest LTS. issues will be solved. just get through the learning curve and everything will be ok. You at least have some previous linux experience, i have just started using it. I too am having some issues, but this is normal when you switch to something new.

---

### Post by Cathhsmom on 2010-05-12
I have some issues with Firefox (flash) after the Lucid, but I know it will get resolved with time. I could have either waited a month after the Lucid grand entrance to install, or install it and help with fixing all bugs (reporting that is, I am fairly new with Ubuntu).  I chose the later. For now, I have installed Lorentz (sp?) edition of Firefox so that I can report  my crashes to help get the problem resolved with the flash issue.

---

### Post by Troll_the_Great on 2010-05-12
OK, it set the auto launch interval to 0 (zero), so it will launch as soon as updates become available. And, should I understand that that little orange icon won't appear on the top panel anymore?

---

### Post by philinux on 2010-05-13
> **Troll_the_Great said:**
> OK, it set the auto launch interval to 0 (zero), so it will launch as soon as updates become available. And, should I understand that that little orange icon won't appear on the top panel anymore?

Correct. That went with Karmic and the new notification system.

---

### Post by Troll_the_Great on 2010-05-14
And about my other problems?

---

### Post by Troll_the_Great on 2010-05-16
Bump!

---

### Post by Norm24 on 2010-05-16
> **Cathhsmom said:**
> I have some issues with Firefox (flash) after the Lucid, but I know it will get resolved with time. I could have either waited a month after the Lucid grand entrance to install, or install it and help with fixing all bugs (reporting that is, I am fairly new with Ubuntu).  I chose the later. For now, I have installed Lorentz (sp?) edition of Firefox so that I can report  my crashes to help get the problem resolved with the flash issue.

Not intentionally hijacking this thread but how did you install Lorentz in Ubuntu?

---

### Post by Troll_the_Great on 2010-05-19
Bump!

---

### Post by Troll_the_Great on 2010-05-20
Bump!

---

### Post by lidex on 2010-05-20
Is NM working now? Make sure it's enabled in "System>Preferences>StartUp Applications"
See screens.

---

### Post by Troll_the_Great on 2010-05-21
> **lidex said:**
> Is NM working now? Make sure it's enabled in "System>Preferences>StartUp Applications"
See screens.

No, the applet is not working, and yes, it is enabled in StartUp Applications.

---

### Post by lidex on 2010-05-21
Do you have indicator-applet-complete, network-monitor, and notification-area added to panel from 'panel>right-click>add to panel'?

---

### Post by Troll_the_Great on 2010-05-24
> **lidex said:**
> Do you have indicator-applet-complete, network-monitor, and notification-area added to panel from 'panel>right-click>add to panel'?

I have the indicator-applet and the notification area added, but the network-monitor applet does not exist in Lucid. Am I wrong?

---

### Post by lidex on 2010-05-24
It's there, look below.

---

### Post by Troll_the_Great on 2010-06-03
> **lidex said:**
> It's there, look below.

I'm sorry to say, I don't have a network monitor there... :(

---

### Post by Troll_the_Great on 2010-06-04
Bump!

---

### Post by Troll_the_Great on 2010-06-06
Bump!

---

### Post by Troll_the_Great on 2010-06-07
Bump!

---

### Post by Fred2a on 2010-06-07
Regarding the change to the update method, you can change it back to the old way by running the following command in the terminal:

gconftool -s --type bool /apps/update-notifier/auto_launch false

That info came from the Lucid release notes:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by Troll_the_Great on 2010-06-08
> **Fred2a said:**
> Regarding the change to the update method, you can change it back to the old way by running the following command in the terminal:

gconftool -s --type bool /apps/update-notifier/auto_launch false

That info came from the Lucid release notes:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

Thanks for the tip. Any ideas for my other questions (1,4,5,6)?

---

### Post by beew on 2010-06-08
For the network manager, try remove the indicator applet (if you have it added to the panel) and see if it reappears. NM disappeared last night. Apparently I accidentally add another instance of the indicator applet to the panel and somehow nm get crowded out. I removed it and nm reappeared.

---

### Post by Troll_the_Great on 2010-06-08
> **beew said:**
> For the network manager, try remove the indicator applet (if you have it added to the panel) and see if it reappears. NM disappeared last night. Apparently I accidentally add another instance of the indicator applet to the panel and somehow nm get crowded out. I removed it and nm reappeared.

Tried that, didn't work... :(

---

### Post by Troll_the_Great on 2010-06-10
Bump!

---

### Post by Troll_the_Great on 2010-06-16
Bump!

---

### Post by grobar87 on 2010-06-16
> **lidex said:**
> Is NM working now? Make sure it's enabled in "System>Preferences>StartUp Applications"
See screens.

What theme you using? It's great!!:p

---

### Post by Troll_the_Great on 2010-06-20
Bump!

---

### Post by Troll_the_Great on 2010-06-22
Bump!

---

### Post by Troll_the_Great on 2010-06-28
OK, guys, last try. I tried everything I found on the internet to fix at least my network applet (like this thread for example: [http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html](http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html)), but nothing worked.
I will wait till the 10.04.1 gets released and if the problem still persists I'm giving up on this release. Shame is an LTS... :(
Do you know when 10.04.1 arrives? In June or July?

---

### Post by thane1 on 2010-06-28
x

---

