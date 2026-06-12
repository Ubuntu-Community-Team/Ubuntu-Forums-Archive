---
title: "Change icon size in dash?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by nuddernuby on 2011-06-19
Did I miss this in other threads?

How do we change the icon size in the dash? [11.04 - as opened from top left Ubuntu logo] In higher res it would be good to have smaller icons.

Thank you if you can help...

---

### Post by fooman on 2011-06-19
sadly,  as far as i know....you cannot change the icon size in the *dash*

you can however change the size of the icons in the *unity launcher* via compiz config settings manager (see: unity plugin)

---

### Post by nuddernuby on 2011-06-19
Thank you.

Yes I've done that already in Unity (although I think that the lower size limit could be even lower).

Thought it would be a better use of real estate if I could pack (many) more icons into the available dash space.

---

### Post by Frogs Hair on 2011-06-19
Fooman is correct , there is no way to change the icon size at the moment . I found a method to reduce the size of the bubble but only works for small monitors.[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by fooman on 2011-06-19
there is a way that you can force dash to go fullscreen,  which gives a whole lot more real estate if thats what you would like?

here is what to do:

first install dconf-tools (run in a terminal):

```
sudo apt-get install dconf-tools
```after it installs, press alt-f2 keys and type:

```
dconf-editor
```when the editor opens, go to > desktop > unity

with unity highlighted,  look on the right and click on the word "automatic" (to the right of "form-factor) ...you should see 3 choices: automatic, desktop and netbook

choosing "netbook" will force dash into full screen mode....leaving you alot of real estate.  it is actually handy when you navigate to something large *like showing all your installed applications*.  on a large monitor,  you can see A LOT more without having to scroll as much.

to change back,  just open dconf-editor again and this time choose "desktop" or "automatic"

hope that helps

---

### Post by nuddernuby on 2011-06-19
Thanks, Fooman. I have done all this. Suppose there is no use in pursuing it any further. The thought does linger in my mind though that somewhere, in some script, some parameter will dictate icon size...

Rgds

---

### Post by mccloudwf on 2011-10-15
Has any progress been made on this subject?  We have several clients running 11.04 and the unity dash icon size is one of the top complaints.  I installed a fresh 11.10 on my laptop and workstation. It would be very nice to make the icons smaller.

---

### Post by WaNaBePi on 2012-02-22
Yes, smaller icons please. Bump?

---

### Post by bhobw on 2012-06-05
Now using 12.04 and still have no way of changin the icon size in the Dash.

Is this being tackled by anyone?

I know it's hard coded in Natty but, PLEASE ...... we need to change the icon size in the DASH.

For us that have poor laptop resolution, it's urgent ....... 



BHOBW

---

### Post by bhobw on 2012-06-05
Keep up to date here:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/815440](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/815440)

---

### Post by edantes on 2012-08-04
In the meantime, wouldn't be possible to modify a css stylesheet by brute force?

---

