---
title: "AR5007 (recognized as AR242x) with Ubuntu 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Yarcofin on 2008-11-01
Hello everyone, I'm sorry this probably gets asked a few dozen times per week, but I have been searching the internet for weeks and trying different things to get my wireless card working in both 8.04 and 8.10, but so far nothing has worked. I decided to come here as a last-hope, so I hope my thread doesn't get immediately trashed.

I'm a complete beginner trying to make the transition from Vista to Ubuntu, so please bear with me and if you explain something please give step-by-step idiotproof instructions.

- I installed Ubuntu 8.10 with Wubi (dual-boot)
- Previously 8.04 detected restricted drivers with my wireless card, but 8.10 seems to be an improvement because I have no restricted drivers, only "Support for Atheros cards" under my hardware.
- I have a Compaq Presario A900 and I am using 32 bit.
- Is my wireless supposed to detect automatically? How to I check for available networks? It might in fact be working already but I just have no idea how to connect. My laptop has a button to turn wifi on/off... it's blue when on and orange when off. In Ubuntu it stays orange no matter what I do.

Here is my problem:

I have tried all of the following sets of instructions:
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)
[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
[http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/)
[http://ubuntuforums.org/showthread.php?t=680209](http://ubuntuforums.org/showthread.php?t=680209)

None of them worked. I get errors when trying to put in the code. I have tried installing both ndiswrapper and madwifi but neither worked.

All of the "how to"s I've read use commands like wget [http://.](http://.).. but obviously if my wireless isn't working I can't download any programs or updates! In my attempts, I instead downloaded them in Windows from the internet and took them into Ubuntu on a USB stick, but when I try to install I get errors.

I'm fairly certain that my problem is that I don't have something called "build essential". All instructions to get this assume that you already have wireless and again use a command line that will try to connect to the internet for updates.

I have found the build essential (deb) file online... but I have no idea how to install it.

Can someone please explain how to get the .deb file for build essential in the correct place, or if my problem is something else?

---

### Post by Yarcofin on 2008-11-01
I have now also tried the following without success, after reading it on another post:

sudo vi /etc/modprobe.d/blacklist ath_pci
and
sudo vi /etc/modprobe.d/blacklist ath_hal

I get an incomplete list of blacklisted devices/drivers, and reboot.

Still no connections and nothing shows up under iwconfig.

I think I need to try "linux-backport-module" next, can someone explain how to do that **without downloading from the internet using wget command**. Give me the link to the file, but assume that in the terminal that I have placed the file on my desktop. And let me know whether or not I need this "build essential" for that as well.

---

### Post by Spartacus84 on 2008-11-01
I'm having a similar problem. I have a Compaq Presario f756nr with the AR5007eg and I've tried everything I've seen.

I think you can get the linux-backport-module by just using Synaptic Package Manager.

---

### Post by Yarcofin on 2008-11-01
> **Spartacus84 said:**
> 
I think you can get the linux-backport-module by just using Synaptic Package Manager.

Emphasis on the lack of wireless connectivity.

---

### Post by farhill on 2008-11-01
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) worked for me. However, be warned that it's not a very beginner friendly solution.

It also requires build-essential. If I'm not mistaken, this is included on the install CD, so you shouldn't need network to install it. Insert the CD and go to repositories under settings in synaptic.

If you want help with the errors you encountered, you'll need to describe them more specifically. "I get errors when trying to put in the code." doesn't give enough information for anyone to help you. Which "code" and which error ?

Any solution is likely to require downloading stuff from the internet. You don't have to use wget (using your web browser is fine), but you'll probably have to boot windows or use a wired network. I'd suggest using a wired network if at all possible. You can manually download package files and then tell the ubuntu package management tools to use them, but it's definitely not the simplest thing.

edit:
the backports package should also be included on the install CD, so you don't need network access for that.

---

### Post by Yarcofin on 2008-11-01
I don't have an install CD, I used Wubi which downloaded and installed Ubuntu directly... should build essential be hidden somewhere in there?

I can't burn a CD because I don't have any CD-Rs available
I can't get a wired network because I'm at university and all we have is wireless, and I don't have an ethernet cable anyway.

Once I get build essential installed, if things still aren't working I will post screenshots of what I get in the terminal.


Edit:
I went into Synaptic and got build essential to show up on the list and tried to apply it, but when I try to install it's asking me for the non-existant CD that I don't have.

---

### Post by farhill on 2008-11-01
Just a quick update, I tried the  linux-backports-modules-intrepid-generic method and it works fine so far. I'd suggest using this rather than building your own driver. It means you don't need build-essential, and you don't have to worry about rebuilding and re-installing your drivers every time you update.

> **Yarcofin said:**
> I don't have an install CD, I used Wubi which downloaded and installed Ubuntu directly... should build essential be hidden somewhere in there?

Probably. I would  guess that wubi puts an iso image somewhere, or something with the equivalent contents. I have no experience with it personally, but [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) appears to confirm it. Find the ISO, mount it, and you should be good to go.

Failing that, you could always manually download the iso under windows and mount it.
> 
I can't burn a CD because I don't have any CD-Rs available
I can't get a wired network because I'm at university and all we have is wireless, and I don't have an ethernet cable anyway.

Both ethernet cables and blank media should be available for very little money. I'd expect your university bookstore stocks them, at a moderately offensive markup compared to online prices ;)

---

