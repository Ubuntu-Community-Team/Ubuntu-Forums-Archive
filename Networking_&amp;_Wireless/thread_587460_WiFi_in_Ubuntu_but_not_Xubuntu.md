---
title: "WiFi in Ubuntu but not Xubuntu"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by tmweber on 2007-10-22
Hi,

I have a Dlink dwl-650 wireless card on my laptop.  When I run the Ubuntu live CD it finds the drivers and I can easily connect using network manager.  However, I had loads of trouble installing ubuntu on my laptop (two days worth of attempts) and I finally tried Xubuntu instead, which installed rather easily.  Now of course, Xubuntu doesn't recognize my wireless card (iwconfig returns nothing).  All the resources online point to using ndiswrapper and whatnot, but seeing as this driver is supported in the Ubuntu release, I think it should be easier.  I've tried installing ubuntu-desktop using apt-get, but that did not fix the problem.  What do I need to install to get something that works out of the box in Ubuntu working in Xubuntu?

Thanks,
Tim

---

### Post by Zeedok on 2007-10-23
If you've bought a card that has an installed driver it should work.

One caveat though, you need to be certain of the chipset included in your card - for example some slight model variation may have a different chip which can stuff things up.

Provided that is not your issue (and if the wireless card worked when you used the ubuntu live CD) then it's probable an issue which the configuration.

I'm afraid I'm a relatively recent refuge from WinXP so I'm ridiculously dependent on a GUI way of doing things (even in ubuntu). So here a couple of things to try . . .

If your Xubuntu version is Feisty then install WICD ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)).

The Gutsy version has the Network Manager should make setup fairly easy, though I have had problems with the WPA password - see this post: [http://ubuntuforums.org/showthread.php?t=584670&highlight=xubuntu+network+manager](http://ubuntuforums.org/showthread.php?t=584670&highlight=xubuntu+network+manager)

Either of these GUI methods should work for you.

Good Luck.

---

### Post by Zeedok on 2007-10-24
I have now installed wicd even on Xubuntu gutsy and it is easier to use than Network Manager.

Try it, you won't be sorry.

---

