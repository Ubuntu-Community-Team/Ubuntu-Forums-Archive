---
title: "Screen resolution custom/widescreen?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Fitzwilliam_Darcy on 2011-07-20
I'm new to Ubuntu and Linux and would like to know how to change the screen resolution to a custom user-specified size or just a common widescreen size, and also keep it that way.

(I'm using Oracle VM VirtualBox with Windows 7 as the host and Ubuntu 11.04 as the guest)

I can type in **xrandr -s 1024x768** into the terminal but it only gives me 4:3 ratio options.

How do I make it widescreen or custom, user-defined?
And how do I make the changes permanent? Every time I restart it, it reverts back to the original resolution.

---

### Post by androssofer on 2011-07-20
assuming you tried:

System---> Preferences----> Screen Resolution

if so this might help:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

I played with it when tryin to get mine to work on a tv...

**note** make sure you make the backup of the file, cus i ignored that and it was a headache to fix... haha.

---

### Post by Grenage on 2011-07-20
> **Fitzwilliam_Darcy said:**
> I'm new to Ubuntu and Linux and would like to know how to change the screen resolution to a custom user-specified size or just a common widescreen size, and also keep it that way.

(I'm using Oracle VM VirtualBox with Windows 7 as the host and Ubuntu 11.04 as the guest)

I can type in **xrandr -s 1024x768** into the terminal but it only gives me 4:3 ratio options.

How do I make it widescreen or custom, user-defined?
And how do I make the changes permanent? Every time I restart it, it reverts back to the original resolution.

1024x768 is a 4:3 resolution; while it's possible (lots of TVs do it) to use non-square pixels, are you sure that's the native res?

---

### Post by kenworth on 2011-08-29
I am having issues just getting anything above 800x600 on my toshiba laptop (W7 supports 1366x768) running Natty guest on W7 virtualbox host.. 

Androssofer's reference to an old post is useless. 11.04 does not have /etc/X11/xorg.conf. As most forum posts relate to latest or recent versions, maybe forum search could filter out the old crap that just gets in the way.

Cheers

---

### Post by bkratz on 2011-08-29
> **kenworth said:**
> I am having issues just getting anything above 800x600 on my toshiba laptop (W7 supports 1366x768) running Natty guest on W7 virtualbox host.. 

Androssofer's reference to an old post is useless. 11.04 does not have /etc/X11/xorg.conf. As most forum posts relate to latest or recent versions, maybe forum search could filter out the old crap that just gets in the way.

Cheers

With googlubuntu you can filter by date

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=googlubuntu&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=googlubuntu&as_qdr=all&sa=Google+Search&lang=en)

---

