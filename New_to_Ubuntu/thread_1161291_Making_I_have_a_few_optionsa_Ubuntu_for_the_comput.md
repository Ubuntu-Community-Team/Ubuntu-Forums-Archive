---
title: "Making I have a few options:a Ubuntu for the computer illiterate"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Jestersage on 2009-05-16
I want to image a Ubuntu onto a friend's Harddrive, and it needs to have about all the functions one would see on a typical XP machine. In short, a plain Ubuntu probably would not do.

I have a few options:
a) Using a reconstructor and throw in the stuff onto my own version
b) Using SuperOS
c) Using Ubuntu Extras Remix
d) Linux Mint

The reason I am asking is that I want it to be repository and upgrade compatible to Core Ubuntu as much as possible, while retaining DVD/MP3/Other format playback capability. Also, I am dealing with people who is less literate in terms of computers.

---

### Post by Marlonsm on 2009-05-16
I think Mint is the way to go.

---

### Post by clive littlewood on 2009-05-16
```
I want to image a Ubuntu onto a friend's Harddrive, and it needs to have about all the functions one would see on a typical XP machine. In short, a plain Ubuntu probably would not do.
```


install XP  !!!!!

Clive

---

### Post by Jestersage on 2009-05-16
> **clive littlewood said:**
> 
install XP  !!!!!

Clive


Other than that. (Besides, I prefer to support a Ubuntu over an XP)

---

### Post by mikewhatever on 2009-05-16
> **Jestersage said:**
> I want to image a Ubuntu onto a friend's Harddrive, and it needs to have about all the functions one would see on a typical XP machine. In short, a plain Ubuntu probably would not do.

The reason I am asking is that I want it to be repository and upgrade compatible to Core Ubuntu as much as possible, while retaining DVD/MP3/Other format playback capability. Also, I am dealing with people who is less literate in terms of computers.

Can you explain why Ubuntu proper wouldn't do. I think the default Ubuntu installation is more functional then Windows XP. What features do you need in particular?

---

### Post by Jestersage on 2009-05-16
> **mikewhatever said:**
> Can you explain why Ubuntu proper wouldn't do. I think the default Ubuntu installation is more functional then Windows XP. What features do you need in particular?

Running mp3, DVD, flash, and other propriety [sp] stuff, which by default is not installed, and have to add in repository (medibuntu) through CLI.

Note that the reason I am asking this is that I am dealing with a friend who properly cannot figure out how to use CLI or search for help online. Thus, basically, I will have to do what is essentially an OEM install.

I am planning the 8.04 LTS as it would save the hassle on my part.

---

### Post by s.fox on 2009-05-16
Hi,

Can you give the specifications of the machine you want to install on.  It would help us determine if your friends computer is more suited to Ubuntu,  Kubuntu or Edubuntu for example.

Thanks,

-Ash R

---

### Post by oldos2er on 2009-05-16
You can add Medibuntu without using the terminal, fwiw. See (in Gnome) System, Administration, Software Sources.

---

### Post by mikewhatever on 2009-05-16
> **Jestersage said:**
> Running mp3, DVD, flash, and other propriety [sp] stuff, which by default is not installed, and have to add in repository (medibuntu) through CLI.

I am rather baffled because Windows XP has none of these functionalities by default. Codecs are actually easier to install in Ubuntu, and you only need Medibuntu for DVD playback, and no, you don't have to use the CLI.

> Note that the reason I am asking this is that I am dealing with a friend who properly cannot figure out how to use CLI or search for help online. Thus, basically, I will have to do what is essentially an OEM install.

I am planning the 8.04 LTS as it would save the hassle on my part.

If you are going to set things up for them, why would they need to deal with CLI? Just get everything ready and run them through the interface basics.

---

### Post by Marlonsm on 2009-05-16
Right after installing, you could use:

```
sudo apt-get install ubuntu-restricted-extras
```
(or use synaptic to get the ubuntu-restricted-extras package)

so it will solve many of the problems (if not all of them).

So he won't have to touch the CLI.


I can safely say the Ubuntu is WAY more user-friendly than XP (maybe even Vista and Seven too), people just need to take a few mins to learn it.

---

### Post by Cheesemill on 2009-05-16
Check out [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

You can basically install and configure Ubuntu how you want (install codecs, apps, etc.) and then create a custom install CD for your friend.

Cheesemill

---

### Post by Jestersage on 2009-05-16
Okay, thanks. 

BTW, what's the difference between ubuntu-restricted-extras and Medibuntu?

And the reason I decide to go with Ubuntu is precisely I will have less of an headache in maintence.

[quote="mikewhatever"]
If you are going to set things up for them, why would they need to deal with CLI? Just get everything ready and run them through the interface basics.
[/quote]
I was thinking just in case I need to do OEM install... except forgetting that I will be setting up their data too.

---

### Post by Dougie187 on 2009-05-16
Medibuntu is a seperate ppa, or software repositiory. Not included by default in ubuntu, and it contains other things like skype for example.

Ubuntu-restricted-extras is just a package in the standard ubuntu repos.

---

### Post by Jestersage on 2009-05-16
Yeah, mainly the mediubuntu issues. But considering that chances are I will install everything...

---

### Post by theozzlives on 2009-05-16
> **Jestersage said:**
> I want to image a Ubuntu onto a friend's Harddrive, and it needs to have about all the functions one would see on a typical XP machine. In short, a plain Ubuntu probably would not do.

I have a few options:
a) Using a reconstructor and throw in the stuff onto my own version
b) Using SuperOS
c) Using Ubuntu Extras Remix
d) Linux Mint

The reason I am asking is that I want it to be repository and upgrade compatible to Core Ubuntu as much as possible, while retaining DVD/MP3/Other format playback capability. Also, I am dealing with people who is less literate in terms of computers.

I sold one of my oldest Ubuntu boxes (with a fresh install) to my roomate and her son (they are computer dumb, and Windows children to the max). The lady didn't even know what to do when it asked for a administrator password.

They got along fine, her customization to the desktop is ugly as sin, but hey it works for her.

---

