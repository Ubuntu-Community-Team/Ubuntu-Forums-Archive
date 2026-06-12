---
title: "Dual boot not booting into MB"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Metal Mick on 2011-05-18
Hi all,

I posted this message in the MythBuntu forum a few days ago but got no response:

"...installed MB from WinXP via Wubi.

I booted, and answered a few MB questions like which graphics driver I wanted to use, and test for connection to the "backend."... When I answer these questions, and wait while language packs are installed, my machine then reboots, and after the regular bios post messages, I then have the option of selecting MB or WinXP."

- this looks like a Windows messge screen - the one that shows if there has been an interrupted boot sequence and you get the choice of Safe Mode, etc.

"...Selecting MB gives a very brief message - too fast for my old eyes to read - and I am then in another screen that looks a lot like a GRUB menu, but lacks MB. Only WinXP shows.

Can someone please suggest a next course of action?"

This has happened a couple of times as I played with whatever defaults I could to try to get things to work.

Would appreciate any help I can get - I'm looking into setting up a media centre PC, running MB as the OS.

Regards,

---

### Post by friv_livs on 2011-05-18
Why don't you use MB in its own partition?

What do you need in XP for the media-centre?

Grub is more dependable than wubi in my experience.

---

### Post by Metal Mick on 2011-05-19
> **friv_livs said:**
> Why don't you use MB in its own partition?

What do you need in XP for the media-centre?

Grub is more dependable than wubi in my experience.

Hi,

thanks for the reply. Specifically, I want to save myself some effort, should I feel MB is not what I am after; I only have one machine at present, and like the idea of simply uninstalling from Win, an unwanted MB install; if I make some error in MB and end up corrupting something or other, I can recover easily.

Once I have developed sufficient knowledge to know if MB is what I want, then I can get another machine and take things from there.

Cheers,

---

### Post by friv_livs on 2011-05-19
Can you use clonezilla or gparted?

I have no troubles with clonezilla backing up my manually partitioned dual boot to image on external drive, given about 2 hours each time.

Also change your title to "Wubi boot ..."

---

### Post by Metal Mick on 2011-05-21
> **friv_livs said:**
> Can you use clonezilla or gparted?

I have no troubles with clonezilla backing up my manually partitioned dual boot to image on external drive, given about 2 hours each time.

Also change your title to "Wubi boot ..."

Hi F-L,

done, re title change.

I also in the past day or so uninstalled MB 11.04 and tried a 9.04 CD I had lying around, and it worked first time.

I still have the same initial screen, but this time I when I select MB, I it boots properly. It would appear there is a some form of bug in the Wubi install for MB 11.04

Overcoming this will be the next step.

Cheers,

---

### Post by friv_livs on 2011-05-21
I can't help you any further.

here's some google search results though:

[HTML]http://www.google.com/search?client=ubuntu&channel=fs&q=mythbuntu+11.04+wubi+bugs&ie=utf-8&oe=utf-8[/HTML]

hope this helps,

Friv.

---

### Post by Metal Mick on 2011-05-23
Hi friv_livs,

that's okay. Many thanks for trying and also for the search.

cheers,

---

