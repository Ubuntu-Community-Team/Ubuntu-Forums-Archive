---
title: "New to the world of Ubuntu"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by boldhoof on 2011-01-15
Hi

Hello to everyone, I am new to the world of Ubuntu / Linux but known of it for years, just never tried it. I have just installed as a dual-boot with Windows XP, as I want to make sure its for me, so far, 2 hours in I am impressed. I have 750mb ram, and all seems okay. The only issue at times seems to response by the mouse when I want to change tabs on screens, sometimes it seems to take a few secs longer to open the tab.

---

### Post by Paqman on 2011-01-15
Do you mean switching between tabs in your web browser, or somewhere else like the file browser? If it's your web browser, which one are you using?

---

### Post by davidmohammed on 2011-01-15
what is the specification of your PC

RAM, Processor, Graphics?

---

### Post by boldhoof on 2011-01-15
> **Paqman said:**
> Do you mean switching between tabs in your web browser, or somewhere else like the file browser? If it's your web browser, which one are you using?

Sometimes in the web browser like now, this forum open and BBC site, browser is Firefox, which was with the install. If I open System Monitor and click a tab it sometimes seems to take a few seconds to change. I have checked the mouse option and it seems set fine.

---

### Post by boldhoof on 2011-01-15
> **davidmohammed said:**
> what is the specification of your PC

RAM, Processor, Graphics?

750mb ram, AMD processor, basic graphics card, not sure how to check via Ubuntu.

---

### Post by ericrichards420 on 2011-01-15
its easy, goto system>administration>System Monitor and click on the system tab

---

### Post by kn0w-b1nary on 2011-01-15
My way to resolve speed issues:
1. Switch to Opera or SwiftFox for browsing.
2. Switch to XFCE4 instead of Gnome.
3. Use Ubuntu Tweak and BleachBit to do some cleanup.
4. Install prelink.

Hope this helps.
Am using 512mb of RAM so I have tried these.

---

### Post by abdulapopoola on 2011-01-15
Welcome to the great world of Ubuntu and open source, have fun as you experiment!

---

### Post by boldhoof on 2011-01-15
> **kn0w-b1nary said:**
> My way to resolve speed issues:
1. Switch to Opera or SwiftFox for browsing.
2. Switch to XFCE4 instead of Gnome.
3. Use Ubuntu Tweak and BleachBit to do some cleanup.
4. Install prelink.

Hope this helps.
Am using 512mb of RAM so I have tried these.

Thanks for the tips. I understand how to switch browsers, but as far points 2 - 4 not sure, although do understand install prelink, not sure about the rest.

---

### Post by kn0w-b1nary on 2011-01-15
when you login to Ubuntu, the graphics you see consist of
whats called a Desktop Environment. Your login screen says
at the bottom "Ubuntu Desktop/Netbook Environment" which is
also known as Gnome. It is kinda bloated and can hog RAM.
Open up Synaptic Package Manager and search "xfce4-session"
Install and logout. Now make sure that the box says something
like xubuntu or xfce. Login. things will look different
will be faster. Google "Ubuntu Tweak" and "BleachBit" and
download the files. Once installed, you will have the ability
to delete file to speed up ur computer.

Hope this helps!

[EDIT]: open a terminal and type (without quotes) "sudo apt-get install prelink"
Then reboot.

---

### Post by boldhoof on 2011-01-15
> **kn0w-b1nary said:**
> when you login to Ubuntu, the graphics you see consist of
whats called a Desktop Environment. Your login screen says
at the bottom "Ubuntu Desktop/Netbook Environment" which is
also known as Gnome. It is kinda bloated and can hog RAM.
Open up Synaptic Package Manager and search "xfce4-session"
Install and logout. Now make sure that the box says something
like xubuntu or xfce. Login. things will look different
will be faster. Google "Ubuntu Tweak" and "BleachBit" and
download the files. Once installed, you will have the ability
to delete file to speed up ur computer.

Hope this helps!

[EDIT]: open a terminal and type (without quotes) "sudo apt-get install prelink"
Then reboot.

Many thanks for your help, I have done the xfce4-session install and logout, then picked xfce, certainly looks different, and seems to be faster. I think I will leave the other recommendations till the morning. Many thanks for your help.

Also thanks also to everyone who has replied so quickly to my post, thank you, I really appreciate everyone's input.

---

### Post by NightwishFan on 2011-01-15
I do not think prelink will help, and I hear reports of it causing problems on newer releases. Just safely avoid that tip if you want my advice.

I think it is just normal responsiveness stuff and not really a bug. If you have come from Windows Xp, WinXp is an old old system for older computers. Ubuntu is a modern one for newer computers (that happens to run ok on older ones). I agree with trying Xubuntu or XFCE but I think Gnome (default ubuntu) is the best choice.

Try perhaps to disable desktop effects in System -> Preferences -> Appearences -> Desktop Effects. If you have an old GPU they might already be disabled.

---

### Post by kn0w-b1nary on 2011-01-15
> **boldhoof said:**
> Many thanks for your help, I have done the xfce4-session install and logout, then picked xfce, certainly looks different, and seems to be faster. I think I will leave the other recommendations till the morning. Many thanks for your help.

Thanks...

For increased login speed in XFCE4...
Open the menu,
open the submenu "settings"
click "Xfce 4 Settings Manager"
click on "Session and Startup"
open the tab titled "Application Autostart"
Uncheck items like:
xfce4-tips
Update Notifier
Skype
Notes
Clipman

By doing this (and removing compiz), my login time went from 20 seconds to 5!

Good Luck!

---

### Post by Paqman on 2011-01-15
> **boldhoof said:**
> Sometimes in the web browser like now, this forum open and BBC site, browser is Firefox, which was with the install. If I open System Monitor and click a tab it sometimes seems to take a few seconds to change. I have checked the mouse option and it seems set fine.

It's hard to know exactly what could be causing this. Is the system slow generally, or do you only see it in the case you describe?

If it's a bit sluggish overall, have you installed the drivers for your graphics card? Go to System > Admin > Hardware drivers and see if there's anything in there for you.

---

