---
title: "Optomize for Netbook"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-10-23
10.10 is really super slow on my Mini 10v.  How can I optimize it?  And I can't change distros because I use a broadcom wireless card that only works in ubuntu 10.10

---

### Post by Hippytaff on 2010-10-23
You might be able to use other lighter distros and ndiswrapper to get broadcom drivers working

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Like the signature btw...pretty much what I did :-)

---

### Post by Junel32 on 2010-10-23
H! Guys, am new here. I got 10.10 desktop installer in my laptop and it's working fine, I suppose. I still have to connect to the web though. I'd like to know its difference with the netbook version. Perhaps it's already stated in the site but I missed it though. :)

---

### Post by Hippytaff on 2010-10-23
> **Junel32 said:**
> H! Guys, am new here. I got 10.10 desktop installer in my laptop and it's working fine, I suppose. I still have to connect to the web though. I'd like to know its difference with the netbook version. Perhaps it's already stated in the site but I missed it though. :)

The netnook version is optimised for netbooks...things like resolution for smaller screens and its a bit lighter on resources :-)

[http://en.wikipedia.org/wiki/Comparison_of_netbook-oriented_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_netbook-oriented_Linux_distributions)

Oh...and welcome :-)

---

### Post by DZ* on 2010-10-23
> **TriBlox6432 said:**
> 10.10 is really super slow on my Mini 10v.  How can I optimize it?  And I can't change distros because I use a broadcom wireless card that only works in ubuntu 10.10

I'm posting this from mini 10v with Ubuntu 10.10. It came from Dell with its tweaked Hardy preinstalled. I don't think it is any slower now that it is running 10.10.

You could try Fedora. You'd need a cable connection first to enable rpmfusion repos ([http://rpmfusion.org/](http://rpmfusion.org/)) and install the driver,
```
yum install wl-kmod
```

---

### Post by Hippytaff on 2010-10-23
> 
 I don't think it is any slower now that it is running 10.10.


probably, but I think the optimisations are mainly to do with usability and only having packages that are required for what netbooks are designed for :-) but if you can run windoze xp on it then 10.10 and 10.04 should run just as well nay much better :-D

---

### Post by TriBlox6432 on 2010-10-23
Would a minimal install still have the broadcom driver automatically installed?  I could try that and build up from there? 

Basically, this is what I require:
A GUI (gnome if possible) with a nice looking theme (Shiki-Brave if possible)
Fast Web Browser
Ability to view PDFs
Email client (Thunderbird if possible)
Gnome Office
All codecs (ubuntu-restricted-extras)
VLC
Ability to connect to internet via wifi

That's all I can think of for now, probably more to come. 

I've also heard or people disabling drivers they don't use, and other crap that they don't use.  How do I do this?

---

### Post by kerry_s on 2010-10-23
normal desktop install
swap gnome-panel out for a dock, awn is nice
install maximus
change maximus to not undecorate

that should give you nothing but, your current app in view, fully maximzed.

---

### Post by TriBlox6432 on 2010-10-23
Thanks so much!!  Can you give me a step by step guide on how to make AWN look and act like yours?

---

### Post by kerry_s on 2010-10-23
i'm using the latest version avant-window-navigator-trunk:
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

lol, it's simple just play with it.
for the indicators you use 2, right click them to configure.

it's fairly standard, if your not sure just copy the pic's.

i'm very conservative & don't use a bunch of fancy settings, you might want a little more candy.

---

### Post by DZ* on 2010-10-23
> **Hippytaff said:**
> probably, but I think the optimisations are mainly to do with usability and only having packages that are required for what netbooks are designed for :-) but if you can run windoze xp on it then 10.10 and 10.04 should run just as well nay much better :-D

I didn't mean to imply that Dell's Ubuntu was somehow optimized. I'm simply saying that 10.10 isn't slower on Mini 10v than Ubuntu version that was put there by Dell.

---

### Post by Charles34 on 2010-10-23
> **TriBlox6432 said:**
> 10.10 is really super slow on my Mini 10v.  How can I optimize it?  And I can't change distros because I use a broadcom wireless card that only works in ubuntu 10.10
I'm interested in which broadcom wireless card you're using. I'm running Lucid on my laptop and Maverick on my netbook (Lenovo Ideapad S10-3T.) Both have broadcom cards in the 43xx series and both are working fine. I had to use a proprietary driver on Lucid but it's up and going just fine. Also, unless you're partial to the Unity interface on Maverick, I would recommend going to Lucid just for its stability and ease-of-use. I was running 10.04 netbook remix on a dell mini 9  with a 1.33ghz cpu and basement level graphics and I was still able to use window effects and the notorious rotating cube (that are unavailable on the "netbook" interface and glitchy on the "desktop" interface of 10.10 netbook edition.) Unless you have a touch screen, Unity can't touch Compiz.

   Anyway, what I was basically trying to say was if you have a broadcom in the 43xx series, you're not limited to 10.10.

---

### Post by TriBlox6432 on 2010-11-04
Thanks for the info guys.  Is there anything else I can do, however, just to make it run faster and not lag as much?

---

### Post by fabounet on 2010-11-04
use GLX-Dock as the dock, it's hardware accelerated, which saves your CPU ;-)

---

### Post by TriBlox6432 on 2010-11-04
No hardware acceleration on Netbook.  Sorry.

---

