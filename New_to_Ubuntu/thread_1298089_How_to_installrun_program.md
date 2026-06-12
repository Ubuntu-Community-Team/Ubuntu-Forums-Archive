---
title: "How to install/run program?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by woodyg on 2009-10-22
Hi,
as a total beginner I cannot seem to install/run a program I'm interested in. I've donwloaded a .deb file, right-clicked and selected "open with gdebi package installer", run the installation... but then nothing...

The program does not appear in any menu (program is not command line), and if I look up some of its files in usr/bin, then running the file result in nothing. nothing happens.

my hope when installing ubuntu was that it was now fairly user friendly, without the need to learn exotic commands and procedures. isn't it?

---

### Post by cariboo on 2009-10-22
It would help if you told us what package you installed, you can use the locate command to find where the package is installed. Open a terminal and type:

```
locate <packagename>
```

---

### Post by murderslastcrow on 2009-10-22
Yes. What program are you installing exactly? Usually this only happens if it's a package of libraries to be used by another program.

---

### Post by woodyg on 2009-10-22
I'm trying to install AVG antivirus (I know... everyone says I don't need, but I want it). Anyway, to continue from where I left off above... I then went to synaptic package manager, and now something called amavisd-new appears (interface between MTA and virus scanner). I somehow managed to install (this time within synaptic package manager), but still nothing appears anywhere. How am I supposed to use this installed program?

I tried to do the locate thing you mentioned above, but it just snaps back with the cursor on a new line. nothing happens there either.

---

### Post by clive littlewood on 2009-10-22
Hi

The normal method to install a.deb file is just to double click.

This will install and put a menu item in the appropriate list.

Is the program you require not in synaptic package manager ???

Clive

---

### Post by clive littlewood on 2009-10-22
Hi

I would install clamav from synaptic !!

Remember AV programs will only detect windoze virus so if your not using windoze why bother.



Clive

---

### Post by woodyg on 2009-10-22
it does not appear in any list... as far as I can see. How can I see a complete list of installed programs? As mentioned, it is now listed as installed in synaptic package manager. But I don't know how to run it...

---

### Post by murderslastcrow on 2009-10-22
I'm getting it now and installing to see if I can't reproduce the issue. It could simply be that your menu hasn't refreshed to reflect the changes currently. If that's the case, you could restart or even reinstall the package to see if it shows up.

Anyway, I'm assuming you've installed the package from the official site just like I'm doing from the following URL?

[http://free.avg.com/us-en/download?prd=afl](http://free.avg.com/us-en/download?prd=afl)

---

### Post by murderslastcrow on 2009-10-22
Hey buddy- here's your answer.

[http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux](http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux)

It doesn't have a GUI, so you have to launch it from the command line. avast! However does have a GUI, so it will show up in your list. Apparently the AVG folks think that only geeks will use their antivirus program on Linux.

Here's the link for avast! for Linux. [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

Registration is free, and only used so that they don't get people sucking up their bandwidth for no reason.

---

### Post by Kapitän Rotbart on 2009-10-22
Mind you, Avast! requires you to register for a new serial every 18 months or so to keep getting updates. I don't think AVG requires the same. Personally, running an anti-virus software via the CLI would be awesome (like who needs GUI for a system scan??). Aren't there good instructions for running AVG via the CLI in the Gnome Terminal for n00bs?

Personally I recommend using windeuce xp in a virtual machine with minimal internet use and you shouldn't need an anti-virus software.

---

### Post by woodyg on 2009-10-22
> **murderslastcrow said:**
> Hey buddy- here's your answer.

[http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux](http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux)

It doesn't have a GUI, so you have to launch it from the command line. avast! However does have a GUI, so it will show up in your list. Apparently the AVG folks think that only geeks will use their antivirus program on Linux.

Here's the link for avast! for Linux. [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

Registration is free, and only used so that they don't get people sucking up their bandwidth for no reason.

oh, was command line... was certain it wasn't. I just installed avast... easy peasy. I'm old enough to remember the old days before windows... dos commands and all that. not something I want back. 

on a side note... when using avast I noticed something I've seen elsewhere in ubuntu... my screen is not high enough (9" acer aspire one) for the popup window to fully display, and there seem to be no obvious way of moving the window up so I can see what is displayed at the bottom. in avast the "run scan" button is almost invisible near the bottom, and I barely managed to click it.

how to solve?

---

### Post by Bölvaður on 2009-10-22
> **woodyg said:**
> oh, was command line... was certain it wasn't. I just installed avast... easy peasy. I'm old enough to remember the old days before windows... dos commands and all that. not something I want back. 

on a side note... when using avast I noticed something I've seen elsewhere in ubuntu... my screen is not high enough (9" acer aspire one) for the popup window to fully display, and there seem to be no obvious way of moving the window up so I can see what is displayed at the bottom. in avast the "run scan" button is almost invisible near the bottom, and I barely managed to click it.

how to solve?

hold down the ALT key and move the window around with the mouse by clicking and holding the left mouse key down while you move the mouse &#8594; which moves the window around.

---

### Post by woodyg on 2009-10-22
ace! thanks for that.

---

### Post by Santosga on 2010-02-27
> **Bölvaður said:**
> hold down the ALT key and move the window around with the mouse by clicking and holding the left mouse key down while you move the mouse &#8594; which moves the window around.

I'm another newbie to both linux and netbooks - also an Acer One 10.1'). Thank you so much for this, I was already thinking about uninstalling Avast and installing ClamAV instead. This way, I'll give Avast a fair chance.

---

