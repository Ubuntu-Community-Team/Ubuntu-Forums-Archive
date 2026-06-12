---
title: "Making an old machine perform"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Vinnie V on 2010-11-13
I just installed 8.10 (the only version that I could get to finish an install) on an older computer, and it runs slooooooooowly. I want to know 2 things:

1) What programs that were part of the general install can I remove to increase efficiency?
2) Is there a Linux build that would be more suited to an older/slower machine


Thank you.

---

### Post by racie on 2010-11-13
It depends on the specs....

 If you're looking for *buntu distros, I'd try Xubuntu or Lubuntu.

If you're looking for a comparison of different light Linux distros, this is a great web page: [http://www.tuxradar.com/content/whats-best-lightweight-linux-distro](http://www.tuxradar.com/content/whats-best-lightweight-linux-distro)

*edit*  Oh and let me just say that (relating to the URL I gave you) I've tried SliTaz myself and was very impressed.  :D

---

### Post by Guitar John on 2010-11-13
I had good luck with Puppy Linux on an old Dell 3500 from 1999.

---

### Post by Vinnie V on 2010-11-13
> **Guitar John said:**
> I had good luck with Puppy Linux on an old Dell 3500 from 1999.

I tried Puppy Linux, but it seemed like I was missing something, you have to save your changes each time you shut down?

And I did not figure out how to save it to the HD. Each time I thought i did it, it would not boot from disk...

---

### Post by PhilGil on 2010-11-14
Another vote for Puppy, I've run it on some very elderly machines and it never fails to impress. If your computer is somewhat higher speced, I'd give Lubuntu a try. I'm running it on my netbook; it's impressively snappy and it inherits Ubuntu's excellent hardware support.

---

### Post by PhilGil on 2010-11-14
> **Vinnie V said:**
> I tried Puppy Linux, but it seemed like I was missing something, you have to save your changes each time you shut down?

And I did not figure out how to save it to the HD. Each time I thought i did it, it would not boot from disk...

[http://www.puppylinux.com/hard-puppy.htm](http://www.puppylinux.com/hard-puppy.htm)

---

### Post by thegammaray on 2010-11-14
+1 for Lubuntu. There's nothing wrong with Puppy (it will almost certainly run faster), but I'd stick to the more user-friendly distributions if they'll run tolerably. Lubuntu is built on the same base as Ubuntu, and uses the same package management systems; in my experience, Ubuntu-based distros are the easiest to find help with, in no small part because of these forums.

---

### Post by Vinnie V on 2010-11-14
I am downloading Lubuntu now to try that. Do I need to do a custom install of it, or should I be ok with the standard build? Can I use the latest version, or do I need to look for a different one?

---

### Post by PhilGil on 2010-11-14
> **Vinnie V said:**
> I am downloading Lubuntu now to try that. Do I need to do a custom install of it, or should I be ok with the standard build? Can I use the latest version, or do I need to look for a different one?
I'd try 10.10 first as both LXDE and Lubuntu are in rapid development. If the installer craps out on you -- it's possible as you had trouble with the installer on newer versions of Ubuntu -- you may want to try Debian Squeeze LXDE. They have an optional old school command line installer that's pretty easy to navigate. Also, Debian is relatively easy for an Ubuntu user to adjust to.

---

### Post by Finalfantasykid on 2010-11-14
How much memory does this computer have?

If it has 128 - 256 I would suggest Lubuntu

If it has 256 - 512 I would suggest Xubuntu with Gnome compatability disabled.

---

### Post by Paqman on 2010-11-14
> **Vinnie V said:**
> 
1) What programs that were part of the general install can I remove to increase efficiency?
2) Is there a Linux build that would be more suited to an older/slower machine


If you want a lightweight system it's probably easier to start with a minimal install and build up, instead of starting with a full fat version and stripping down.

Check out the link in my sig. It's a script that can be used to install very lightweight but fully functional versions of Ubuntu, Kubuntu, Xubuntu or Lubuntu.

---

### Post by cascade9 on 2010-11-14
> **Paqman said:**
> If you want a lightweight system it's probably easier to start with a minimal install and build up, instead of starting with a full fat version and stripping down.

Check out the link in my sig. It's a script that can be used to install very lightweight but fully functional versions of Ubuntu, Kubuntu, Xubuntu or Lubuntu.

+1, minimal and then adding stuff is a lot easier. 

Not that you can get a 'lightweight' KDE4.X anymore with ubuntu since 10.04 AFAIK, since the 'kde-minimal' or 'kde-core' packages dont exist for maverick. :( Then again, KDE4.X on an older machine wouldnt be a nice idea anyway....

---

### Post by thegammaray on 2010-11-14
> **cascade9 said:**
> +1, minimal and then adding stuff is a lot easier.

A minimal install will give a more lightweight system, but it's probably not easier. I'd recommend that option only if you're dissatisfied with a standard Lubuntu install. KISS whenever possible, IMHO.

---

### Post by robert shearer on 2010-11-14
> **Vinnie V said:**
> I tried Puppy Linux, but it seemed like I was missing something, you have to save your changes each time you shut down?

And I did not figure out how to save it to the HD. Each time I thought i did it, it would not boot from disk...

Its not meant to boot from (hard-)disk.
What it saves is user data and configurations.
Each boot is from the live cd (and into ram)and then it finds and implements the configs and allows you to access your stored data.This gives you your personalised desktop/os.

As Puppy runs as root by default this method provides a useful blend of security (the os is new each boot so malware cannot reside on hard-disk) and performance.

Ram is cleared on power down. Data and configs are saved to Hard-disk. Simple.

---

### Post by theozzlives on 2010-11-14
try [this]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

