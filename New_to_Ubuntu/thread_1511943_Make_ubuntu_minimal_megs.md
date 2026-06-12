---
title: "Make ubuntu minimal megs?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by DonaldJ on 2010-06-17
Just fer the heck of it, when I ran Windows OS's I tried to shave the OS down to only what programs I wanted.  Has any one minimized Ubuntu 910 down to bare-bones OS..?  How many bytes did you get it down to, and still functioning proper?

How do you delete all the unnecessary default pix and sound files in Ubuntu 910?

Are there any foreign language files that could be erased?

If you eliminate a lot of the OS, does that speed-up the operation of the OS?..

How do you get into the areas of the OS to erase things?..

Why are there things in the OS that don't let you erase them, like a few email addresses?..

When you boot-up or shut-down Ubuntu 910, does it connect to any email addresses automatically..?  If it does, how do find and block all such connections?..

Are there any special scanning softwares for Ubuntu that tell you all the Internet stuff that's happening in the OS, and lets the user control it all..?

---

### Post by lisati on 2010-06-17
You could try a minimal install. 
> 
If you eliminate a lot of the OS, does that speed-up the operation of the OS?..
If you start deleting parts of the OS there's a good chance that it won't work properly, if at all.

> How do you get into the areas of the OS to erase things?..

Try the Software Center and Synaptic Package manager.
> When you boot-up or shut-down Ubuntu 910, does it connect to any email addresses automatically..?  If it does, how do find and block all such connections?..
I'm guessing here that you are referring to 9.10 - AFAIK  there never was or never will be a 910. And even if there was, I'd be surprised if contacted email addresses without the user's knowledge.
> Are there any special scanning softwares for Ubuntu that tell you all the Internet stuff that's happening in the OS, and lets the user control it all..?
Short answer: Try xsane.

---

### Post by halitech on 2010-06-17
> **DonaldJ said:**
> 
Are there any special scanning softwares for Ubuntu that tell you all the Internet stuff that's happening in the OS, and lets the user control it all..?

> **lisati said:**
> 

Short answer: Try xsane.

I don't think they were referring to scanning from a scanner but tracking all internet connections and being able to allow or deny connections.

---

### Post by ddrichardson on 2010-06-17
> **DonaldJ said:**
> Just fer the heck of it, when I ran Windows OS's I tried to shave the OS down to only what programs I wanted.  Has any one minimized Ubuntu 910 down to bare-bones OS..?
I can't imagine why I'd do it that way around. Install a minimal system ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) then add what you need. Voila, minimal system.

---

### Post by cascade9 on 2010-06-17
> **DonaldJ said:**
> Just fer the heck of it, when I ran Windows OS's I tried to shave the OS down to only what programs I wanted.  Has any one minimized Ubuntu 910 down to bare-bones OS..?  How many bytes did you get it down to, and still functioning proper?

How do you delete all the unnecessary default pix and sound files in Ubuntu 910?

Like lisati and ddrichardson said, that is the hard, and risky, way. Minimal install is the way to go. 

> **DonaldJ said:**
> 
If you eliminate a lot of the OS, does that speed-up the operation of the OS?..


Yes. Not using 9.10, and this test was with xubuntu, not ubuntu, but it gives you an idea of how much you can speed things up with a minimal install- 

[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

---

### Post by lykwydchykyn on 2010-06-17
It depends on your definition of "functioning properly".  If you really want to free up space, skip Ubuntu entirely and go for tinycore linux, it's only 10 Mb.

Granted, it doesn't do much...

---

### Post by sdennie on 2010-06-17
> **lisati said:**
> 
I'm guessing here that you are referring to 9.10 - AFAIK  there never was or never will be a 910.


It's possible that you didn't get the memo but, Ubuntu 910.04 will be called Licentious Lemur.

As for network scanning, you will probably want to look at tcpdump, nmap and the granddaddy of them all, wireshark.

---

### Post by Paqman on 2010-06-17
If you want an easy way into using the Minimal ISO, check out the script in my sig. It'll help take you from a minimal install to a useful system.

From my experience it's absolutely no problem to get a Gnome desktop down to about 1.2GB on the disk and running well under 100MB of RAM. My script will also help you out with trying alternative desktop environments like LXDE (the basis of Lubuntu).

---

### Post by wojox on 2010-06-17
Real ugly but it works after installing the mini.iso

```

sudo apt-get update && sudo apt-get install 
gdm xorg gnome-core gnome-codec-install 
indicator-session-applet update-manager 
firefox-3.5-gnome-support gnome-themes 
network-manager gdebi

```

---

