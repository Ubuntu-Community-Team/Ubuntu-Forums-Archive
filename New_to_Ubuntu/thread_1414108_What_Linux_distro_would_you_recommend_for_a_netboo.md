---
title: "What Linux distro would you recommend for a netbook?"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by czepluch on 2010-02-23
Hi all.

Been a long time since I last visited this forum because ive done a lot of work that required windows apps. But now I have bought a Lenovo IdeaPad S10e, and I want a light linux distro on it to make it run smoother. So my question is which distro would be best? I'm thinking of installing Ubuntu Remix,but is there a better one or would you recommend using normal Ubuntu?

Thanks.
-Jacob

---

### Post by snowpine on 2010-02-23
Ubuntu Netbook Remix if you like the "launcher" or plain old Ubuntu if you like the Gnome desktop.

And of course, use the Search feature to see what kind of problems/issues other users with the same hardware have experienced. :)

At this point in history, all of the major distros (Ubuntu/Debian/Fedora/Arch/etc.) have pretty good netbook support. So go with what you like (I'm typing this from Fedora 12 on my Asus eee). :)

---

### Post by kerry_s on 2010-02-23
just grab unetbootin, do a couple of usb's & try it, see what you like.

---

### Post by PhoHammer on 2010-02-23
Do you want something "light" or do you want something more suited to a small display?

I vote #! Crunchbang Linux for the first and UNR or Ubuntu with Gnome Shell for the latter.

---

### Post by 416inversed on 2010-02-23
I went with Ubuntu-Netbook-Remix (UNR) as it has several packages optimized for netbooks not included in ubuntu-desktop; similarly, Ubuntu desktop includes some packages that are generally superfluous to netbooks.

I preferred kubuntu-netbook over the Launcher of straight UNR, but I kept UNR after disabling the Launcher interface. Now I run just about everything out of the 'Main Menu' panel applet or in a drop-down terminal (guake).

---

### Post by thecliff on 2010-02-23
Ubuntu Netbook Remix or SLAX [if you like KDE].

---

### Post by czepluch on 2010-02-23
Thanks for the answers. I think that i will go with UNR if it is possible to diable the "launcher" and just use a plain desktop like in the desktop version of Ubuntu.?

---

### Post by snowpine on 2010-02-23
> **czepluch said:**
> Thanks for the answers. I think that i will go with UNR if it is possible to diable the "launcher" and just use a plain desktop like in the desktop version of Ubuntu.?

Why not just install the desktop version of Ubuntu in the first place? The only unique "feature" of UNR is the launcher.

---

### Post by czepluch on 2010-02-23
> **snowpine said:**
> Why not just install the desktop version of Ubuntu in the first place? The only unique "feature" of UNR is the launcher.

Thought remix ran a bit lighter than desktop version. Just started formatting to Remix now, so hopefully I can do almost the same things in remix as in desktop version, or am i wrong?

---

### Post by raydeen on 2010-02-23
I went with the stock 9.04 install to an SDHC card (found all the hardware on my eee 900). It performs very nicely.

*** Beware of 9.10 though if you have a solid state drive in your netbook. There is some evidence that Grub 2 will murder the SSD.

[http://forum.eeeuser.com/viewtopic.php?id=78939]("http://forum.eeeuser.com/viewtopic.php?id=78939")

The explanation is given further along in the thread.

---

### Post by czepluch on 2010-02-23
> **raydeen said:**
> I went with the stock 9.04 install to an SDHC card (found all the hardware on my eee 900). It performs very nicely.

*** Beware of 9.10 though if you have a solid state drive in your netbook. There is some evidence that Grub 2 will murder the SSD.

[http://forum.eeeuser.com/viewtopic.php?id=78939]("http://forum.eeeuser.com/viewtopic.php?id=78939")

The explanation is given further along in the thread.

Dont have SSD, so i should be fine. ill go with Remix and try it out judt for fun then. i am only using my netbook at school, so wont matter that much to me if it isnt as good at desktop version. Thanks for the helt everyone :)

btw: it is good to be back in the ubuntu comunity :)

---

### Post by Kixtosh on 2010-02-23
> **czepluch said:**
> ... But now I have bought a Lenovo IdeaPad S10e, and I want a light linux distro on it to make it run smoother. ...This suggestion may be a bit late, but have you considered Xubuntu? It's supposed to be lighter than regular Ubuntu, and is recommended for machines with more modest specifications and netbooks certainly have more limited resources than standard laptops or desktops. I doesn't seem to involve much "sacrifice" of capabilities either, AFIK.
 
[http://www.xubuntu.org/about](http://www.xubuntu.org/about)
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by KegHead on 2010-02-23
Hi!

I'm using the standare 9.10 on a Dell mini 9 w/no problems.

Keghead

---

### Post by slooksterpsv on 2010-02-23
I had an Acer Aspire One 751h, and UNR ran perfect (after getting the GMA 500 pulbso graphics working correctly). Even Hulu ran perfect on UNR.

---

### Post by snowpine on 2010-02-23
> **czepluch said:**
> Thought remix ran a bit lighter than desktop version. Just started formatting to Remix now, so hopefully I can do almost the same things in remix as in desktop version, or am i wrong?

They are the same except for the user interface (launcher vs. gnome desktop) and minor differences in which applications are preinstalled (but they use the same repositories, so you can install whatever apps you like).

You can see the exact differences yourself by comparing these lists:

[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

Netbook Remix does *not* have lower system requirements (except for slightly less disk space due to the different application list), as you can see here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

In my limited experience, performance is roughly the same for supported hardware, and UNR is much, much slower if your graphics card is unsupported.

---

### Post by 416inversed on 2010-02-23
In my hands-on experimenting, I found the difference in adding ubuntu-desktop to ubuntu-netbook-remix were only these generally superfluous packages:
```
brasero firefox-3.5-gnome-support firefox-gnome-support gdm-guest-session libavahi-ui0
libbeagle1 libgtk-vnc-1.0-0libwmf0.2-7-gtk rdesktop totem-mozilla tsclient ubuntu-desktop
vinagre vino xsane xsane-common
```I never ran the inverse of what ubuntu-netbook-remix has that ubuntu-desktop doesn't, but I presume it's more than just netbook-launcher & maximus.

UNR is a good starting point for netbooks that you can then add & subtract from until you get the right flavor of Ubuntu for you.

---

