---
title: "Ipod Touch V.2 support - which audio player supports it?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by surelock22 on 2008-12-18
Hey,

I got my first Ipod, the Ipod Touch, ver.2 (with the volume buttons on the side and the built in "loud" speaker). When I went to the Amarok website, it said that it did not yet support the Ipod touch, and since I was under the assumption that Amarok is one of the better Audio players, I figured that it would have support for it.

Does anyone know which player DOES support the Ipod Touch v.2? I would hate to have to run Windows through Virtual Box and sync it via itunes. In fact, that would be almost impossible since my harddrive is filled with about 50 gigs of music.

---

### Post by jimmy the saint on 2008-12-18
None at this point.  Apple encrypted the itunesdb (itunes database) so that ONLY itunes can interface with it.  It was a move squarely aimed at preventing Linux users from interfacing with the newer ipods/iphone.  There are projects underway to break that hash so that we can use our music software again.  At this point there is very little you can do.  I guess apple thinks that by frustrating us, we will feel the need to reward them with even more money to buy a mac!!

Anyway, don't fret too much, as I said, there are projects underway to fix this.  I have it under good authority that progress is being made and we may be able to see a fix by or around New Years.

Edit:  Oh yeah, if you do use itunes via a virtual machine understand that you can update the database (add music and such) but you CANNOT restore the device or upgrade the firmware.  I would look into jailbreaking the device.  Doing so installs several Unix based tools that allow you to interface a little more with your linux box.  SSH for example.  Also you get a synaptic like package manager (Cydia) that allows you to install many apps that are not available in the app-store.

---

### Post by david_f1976 on 2008-12-19
> **jimmy the saint said:**
> I would look into jailbreaking the device.

As far as I'm aware it's not yet possible to jailbreak the Ipod Touch 2nd gen.

---

### Post by surelock22 on 2008-12-19
so is my best bet to take my extra laptop and make it a Windows music machine with itunes for now? I have a Windows laptop that is a bit inferior to my other (lets just say it has 2 USBv.1's and it runs a P3 where the other one is a P4 with 2 USBv2's AND a working Ethernet port), but the nicer laptop has Ubuntu running on it freaking awesome, and I'd hate to go and install Windows XP on that laptop just for itunes when there may be a crack for Amarok coming...

this is truly a bitch and I hate Apple for making stuff tougher for the open source-er-or's. 

maybe I should hate my work for giving me an ipod touch INSTEAD of an ipod classic with more gigs.

i am interested in jailbreaking the thing though. i will look into that, if possible.

---

### Post by ATL™ on 2008-12-19
I was actually wondering the same thing. I still have Windows installed when stuff like this happens though.

As far as jailbreaking it, you can't. You can jailbreak the 1st gen Touch though. Devs as far as I know, aren't even working on a 2nd gen jailbreak. They're putting their time into the iPhone 3G. I don't expect to see a 2nd gen jailbreak anytime soon.

---

### Post by surelock22 on 2009-01-01
anyone know if the problem that 2nd Generation ipod touch units had hookin up to Ubuntu / Linux based software has been fixed yet?

---

### Post by surelock22 on 2009-01-03
bump?

---

### Post by surelock22 on 2009-01-15
Any news?

---

### Post by Terl on 2009-01-15
I understand you want this to work, but you can google as well as anyone else.  I did a quick look about and, no, no luck yet.

This is one reason I do not buy anything this propietary as you always wind up stuck in the end.

Here's a forum discussing this as well:  [iPod touch in Linux]("http://forums.macrumors.com/showthread.php?t=381860").  To find more google for "ipod touch + linux"

---

### Post by surelock22 on 2009-01-17
Here's the deal: this is THE PLACE to get the goods as far as a well informed answer to any subject pertaining to Ubuntu and Linux, and I trust Ubuntu Forums' user's answers to such subject more-so than other sites. Why? Because I haven't been steered wrong yet. Do I know how to google? Well... gee... what's the internets and why should I email when the good ol' USPS works just fine! Cell phones / SMELL PHONES ! You damn kids with your loud Twisted Sister and MC Hammers. No respect.

By the way, I read via that link you gave me that someone used VB as a way to send itunes through a shared folder via Win XP. Does anyone think this is a decent way to double cross my Ubuntu PC into accepting itunes and have it work properly. Again, we're talking about the ipod touch.

Touche'.... (too-SHAY!)

---

### Post by jimmy the saint on 2009-01-17
You can manage your ipod touch through itunes in a windows installation in virtual box.  In fact, you can install itunes in wine and do the same thing.  You will be unable to use any linux native music players to manage your music until the hash algorithm is successfully reversed.

---

### Post by mark_vinton on 2009-01-19
hey i bought a 2G iPod touch about a month ago.  i had already installed an XP virtual box VM just kinda playing around so then i installed itunes, installed the virtualbox guest additions and sent my music to itunes through a "network folder".  honestly, it doesn't work that bad.  it's still a pain in the *** because i think banshee is an awesome, unbloated music player and it pains me to use iTunes, but when in Rome i guess...

anyhow, yeah you don't have to use any more space than, say, your 10GB installation folder and then point iTunes toward your existing library.

hope this helps.

btw, make sure you set a USB filter when running xp for your ipod device or Ubuntu will snatch it.  also, and i don't know if this matters, but under virtualbox's settings, i checked "enable IO APIC" and it really seemed to speed up the sync rate.

*edit*  i'm pretty sure there is no wine/iTunes implementation that works with the Touch yet.

---

### Post by Doby on 2009-01-20
I have installed itunes in my virtual box and set the filter for my ipod touch v2 but when I open itunes I get two errors, 1. audio device not found(or something((I don't have my virtual box sound setup)) 2. Itunes could not connect to the Iphone because an unknow error occured(0xE000035).  Any ideas on the second one, I know how to fix the first one just choose not to.

---

### Post by tomasd on 2009-01-26
> **surelock22 said:**
> Here's the deal: this is THE PLACE to get the goods as far as a well informed answer to any subject pertaining to Ubuntu and Linux, and I trust Ubuntu Forums' user's answers to such subject more-so than other sites.

Agreed, I was looking for "ubuntu ipod touch gen 2" and this was the first result, so if people discuss the matter here I believe more people will find their answer.
Looking forward to the jailbreak[-o<

---

