---
title: "Resolution problems"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by disabled20191128 on 2011-07-17
Hello,

After installing ubuntu 8.04 on one of my other computers, I rebooted and went trough the BIOS screen and GRUB, then my screen displayed this message : "out of range" and everything went black, I waited and then the login screen appeared. Now the resolution isn't right, it's at 960x600, this is the highest setting in the monitor resolution menu. Is there a way to change it to 1024X768?

---

### Post by Bucky Ball on 2011-07-17
8.04 LTS is no longer supported. I suggest you upgrade to 10.04 LTS, the current long-term support release.

Option #1 and the easiest way to do this is open 'Software Sources', go to the 'Updates' tab and make sure you have 'Long term support releases only' checked in 'Release Update'.

Then open update manager and you should see the option to upgrade to 10.04 at the top. Do the upgrade on a wired connection if possible. It can take some time depending on your connection speed.

Option #2 would be to just do a clean install of 10.04 LTS over the existing 8.04.

8.04 LTS ran out of support in April. LTS releases are supported for three years, server version five. ;)

---

### Post by amjjawad on 2011-07-17
> **Dennisgre said:**
> Hello,

After installing ubuntu 8.04 on one of my other computers, I rebooted and went trough the BIOS screen and GRUB, then my screen displayed this message : "out of range" and everything went black, I waited and then the login screen appeared. Now the resolution isn't right, it's at 960x600, this is the highest setting in the monitor resolution menu. Is there a way to change it to 1024X768?

Hello :)

Hope you won't mind my question but ... why Ubuntu 8.04? it's not supported anymore ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)).

If your computer is old, there are many other alternatives!

As for your question, I have never used 8.04 so I'm sorry if I can't help!

---

### Post by amjjawad on 2011-07-17
> **Bucky Ball said:**
> Option #2 would be to just do a clean install of 10.04 LTS over the existing 8.04.


+1

MUCH better than Upgrading!

---

### Post by Bucky Ball on 2011-07-17
> **amjjawad said:**
> +1

MUCH better than Upgrading!

I've done the upgrade from 8.04 to 10.04 via Update Manager on three of our four machines and one for a friend on a computer I built for them and all worked fine. Just took a little time. ;)

---

### Post by amjjawad on 2011-07-17
> **Bucky Ball said:**
> I've done the upgrade from 8.04 to 10.04 via Update Manager on three of our four machines and one for a friend on a computer I built for them and all worked fine. Just took a little time. ;)

I know it works but in some other cases it won't so better safe than sorry :)

---

### Post by disabled20191128 on 2011-07-17
Ok, good idea i'm going to do it right now using the ubuntu 10.04 live cd.

---

### Post by amjjawad on 2011-07-17
> **Dennisgre said:**
> Ok, good idea i'm going to do it right now using the ubuntu 10.04 live cd.

Just make sure you BACKUP your important files BEFORE doing anything ;)

---

### Post by Bucky Ball on 2011-07-17
> **amjjawad said:**
> I know it works but in some other cases it won't so better safe than sorry :)

True.

> **Dennisgre said:**
> Ok, good idea i'm going to do it right now using the ubuntu 10.04 live cd.

Let us know how you go.

> **amjjawad said:**
> Just make sure you BACKUP your important files BEFORE doing anything ;)

+1. Best way to download ISO is via torrent as checks mdsum in the process. ;)

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by disabled20191128 on 2011-07-17
Before upgrading i decided to go and look in  /usr/share/applications, there are always nice applications in there and after searching a little bit, I found the "Screens and Graphics" application. It helped me to reconfigure my monitor settings. So now my resolution is fine. I didn't upgrade immediately because that computer is pretty old: about 700mb of ram and an intel celeron CPU, i thought that ubuntu 10.04 would slow it down.

Thanks for everything

---

### Post by amjjawad on 2011-07-17
> **Dennisgre said:**
> computer is pretty old: about 700mb of ram and an intel celeron CPU, i thought that ubuntu 10.04 would slow it down.

Thanks for everything

It will be slow but not very slow if you go for 10.04.

Lubuntu 11.04 will run super fast on your machine if you'd like to give it a try. After all, you can try it from the LiveCD before installation.

Good luck and glad you sorted it out :)

---

### Post by Bucky Ball on 2011-07-18
I like Xubuntu myself and probably work fine on that machine. Good luck and glad you fixed.

FYI: If you go System>Preferences>Main Menu you can also see what's installed and add or remove from menus. ;)

---

