---
title: "Belkin Wireless G Drive Help Needed"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by michaelvoss on 2008-04-26
I'm a total novice newbie and really want to use ubuntu. I've been working on making that happen with 8.04, but I'm stuck with the wireless card. 

I've tried tons of searches and seen all kinds of lists of supported cards and links to drivers but I can not get them to work. 

I'm able to install drivers using the ndiswrapper (I have a few installed now), but they all say no device present.

When I install the .inf file from my card's installation CD, it tells me that is an invalid driver.

I have a Belkin wireless g notebook card model F5D7010 and the driver I'm using from the CD is blkwgnv7.inf

I'd appreciate any help.

---

### Post by michaelvoss on 2008-04-26
Bump.

Surely as wild about ubuntu as the people are on this forum, somebody has can point me to the .inf file that I need.

When I go to the list of compatible cards, I get directed to places where I download compressed folders full of a bunch of files that aren't .inf which is what I thought I'm supposed to be installing.

---

### Post by michaelvoss on 2008-04-27
I'll bump it one more time...and then I'll probably give up on Linux. I can't believe that ubuntu is so undeveloped when it comes to wireless networking.

---

### Post by MattBD on 2008-04-27
I have an F5D7010uk card, and it has always worked out of the box with Ubuntu (although in Dapper, Edgy and Feisty it didn't support WPA), so I'm surprised yours doesn't. However, I bought mine in early 2007 and they may have changed the chipset between now and then. Mine uses the Ralink RT61 chipset, yours may be different. But the fact that your device isn't detected does at least mean you don't have to blacklist it, so that's one less step

Anyway, as well as the .inf files, you need the .sys files, and if there are .bin files you need them as well (you didn't mention whether you'd included these or not)

If you're inexperienced with Linux you might want to try installing the ndisgtk package, which is a graphical frontend for ndiswrapper.

---

### Post by alehorb on 2008-04-27
What you get from 'lspci' ?

You need to run the command in a terminal and paste the output here!
:confused:

---

