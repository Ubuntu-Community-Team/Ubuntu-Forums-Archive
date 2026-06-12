---
title: "Update woes, locked me out"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Truemedia on 2010-07-30
I think I am responsable for this, not entirely sure.
When i was trying to install something called the gnome menu bar (an ubuntu copy of the menu bar in os x) while following the instructions there was an error with a resource not existing. By accident before i deleted this I removed something else and couldn't recall what it was. 

From after that everytime the update manager poped up, when i clicked install an error message poped up saying something was missing.

I was going to look into the issue today until for no apparent reason it let me update everything again. After the update manager had finished, everything went to a wierd windows 95 theme, and it asked me to restart, so i did after i got some work done on the internet.

When it restarted i got a horrific grub> on a black and white screen staring at me with a message above asking to press tab for a list of bash-like functions?

This screen didnt indicate anything was wrong, but something obviously is, and I thought because i dont have ubuntu through wubi any more, and bootloader + ubuntu installed on an external hard drive not even anythimg to do with windows I would be safe from this kind of problem. 

Does anyone have an idea of what i deleted, and how i can restore it without reinstalling grub or ubuntu? Thanks

---

### Post by Truemedia on 2010-07-31
Iv'e searched the forums, but everyone seems to be having very different problems, and mine was caused by a simple mistake. I will post the long grub message on here if it gives anyone an idea of what is wrong.

EDIT: this is the message im getting (see below)

> GNU GRUB    version 1.98-1ubuntu7

Minimal bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

---

### Post by Truemedia on 2010-07-31
I mite try reinstalling grub on my external hard drive and seeing what I can do on the livecd, since that is the only thing I can think of that might effect this. I'll post what I did if I manage to resolve this.

---

### Post by varunendra on 2010-08-04
Your post looks unclear. Please mention clearly:

[LIST]
[*]What is the native OS in your computer? Is it functional yet?
[*]Does your native (internal) hard disk contain more than one OS? If yes Which ones?
[*]You have installed Ubuntu in an external drive in its own partition (not through WUBI). Correct?
[/LIST]

To reinstall Grub2, [see how to]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). Make sure you install it on the MBR of the hard disk (sdx), not on a partition (sdx1, sdx2,...etc.).

If not sure about what to do, connect the external drive, boot off a ubuntu live cd, run [Boot Info Script]("http://bootinfoscript.sourceforge.net/") (courtesy- Meierfra) & post its result here.

---

