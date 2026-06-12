---
title: "Ubuntu freezes before the login screen because I edited xorg.conf."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by deckerry on 2011-05-03
At first I was trying to fix a problem where every 2nd or 3rd I booted into Ubuntu, the windows were missing title bars and borders. But now, that's the least of my worries.

I changed xorg.conf to fix the problem (like it said here: [http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/)) and now my Ubuntu 10.04 LTS Lucid Lynx freezes every time I try to boot into it.

What's worse is that I can't simply boot into a safe mode because I cleaned up the boot loader menu so it only shows 2 options: 1 for Ubuntu and 1 for Vista. I used "Grub Customizer" to clean up the menu but I'm absolutely sure that program didn't cause this problem.

[COLOR="Red"]**_I know what I have to do, which is repair "xorg.conf." But I don't know how. Can anybody help?_**[/COLOR]

---

### Post by andrewthomas on 2011-05-03
[QUOTE=http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/]The following tutorial explains how to fix the Compiz Ubuntu Desktop Effects missing titlebar problem. If you've been toying around with **Ubuntu 7.04**][/QUOTE] 

This is some seriously out-dated info.

You should be able to boot from a Live-CD and mount your partition and delete the xorg.conf file.

---

### Post by deckerry on 2011-05-04
Waow. I should have tried that first. Thanks!

---

