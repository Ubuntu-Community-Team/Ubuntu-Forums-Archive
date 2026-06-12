---
title: "does Kubuntu basically work the same as ubuntu?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-29
I am just asking because yesterday I tried Fedora 10 on my laptop (because my wireless card is supported out of the box in fedora 10.. but found out that it doesn't very well and would have had to install MadWifi again anyway.... the kernal update had knocked my wifi out again.. I prefer Ubuntu anyway but really liked the KDE desktop)

SO to make a long story short, I had a Kubuntu 8.10 image disk handy and did a clean install (because I had already installed Fedora 10, but didn't like it as much as I do Ubuntu/Kubuntu)

I just wonder this because I need to re-install the restricted extras for audio and video playback it seems now and of course the madwif fix for my wireless card....

also something strange with Kubuntu I have come across so far, I installed Firefox 3 with the adept installer, then installed Flash.. I get video now with FF3 but no sound?  Does this have something to do with not having all the restricted extras and glstreamer installed or is this something else?

LOL Please bear with me  because I still very new to Linux as a whole and still learning everyday..

---

### Post by donkyhotay on 2009-01-29
The only real difference between ubuntu and kubuntu is that ubuntu uses gnome while kubuntu uses KDE. If you have ubuntu you can 'install' kubuntu by doing
```
sudo apt-get install kubuntu-desktop
```
while if you have kubuntu you can 'install' ubuntu by doing
```
sudo apt-get install ubuntu-desktop
```
then choose which one you want at the login screen.

---

### Post by cptrohn on 2009-01-29
So then if I have Intrepid installed and then after installing the KDE desktop all of the apps I already have will work with KDE then?

---

### Post by abn91c on 2009-01-29
> **cptrohn said:**
> So then if I have Intrepid installed and then after installing the KDE desktop all of the apps I already have will work with KDE then?
yes everything should work ok, some people don't like menu clutter of having both environments apps in one place.

---

### Post by cptrohn on 2009-01-29
> **abn91c said:**
> yes everything should work ok, some people don't like menu clutter of having both environments apps in one place.

Thank you for responding, yes I just installed the KDE desktop and everything works.... And I can see what you mean about the clutter!  Yikes!!


I really like the Dolphin file manager though, a little easier to use than nautilis is it that comes in gnome?

It's very nice.

---

### Post by editrix on 2009-01-30
> **cptrohn said:**
> Thank you for responding, yes I just installed the KDE desktop and everything works.... And I can see what you mean about the clutter!  Yikes!!

Just right click on the menu icon and you'll find the menu editor. I highly recommend you play with it, and note the code that actually launches the program. I learned a lot just tidying up the menu.

What I did was move the Gnome apps I wasn't likely to use to a subfolder under each category that I named Gnome Programs.

> **cptrohn said:**
> I really like the Dolphin file manager though... 

When you get some time, install (if it's not there already) and play around with Konqueror. It's been called the Swiss Army Knife of file managers. Makes Nautilus look sick (sorry Gnome lovers).

Oh, and one more thing: most of the GUI apps are really just pretty front ends to what's going on at the command line level. The difference between one app and another is usually just what programs they use, and how they bring them together. A good example is K3B. Look under Settings->Configure->Programs and you'll see what I mean.

---

