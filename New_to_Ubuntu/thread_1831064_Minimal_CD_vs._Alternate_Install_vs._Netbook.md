---
title: "Minimal CD vs. Alternate Install vs. Netbook"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by Innigo on 2011-08-22
Hi Ubuntu folks,

I was given an old netbook with an external CD drive and no boot from USB option in the BIOS. Running with only 192Mb RAM, the full install failed. No surprise there. I read that one use for the alternate install was for systems with less than 256Mb RAM so I ran that and after a few problems due to CD errors using a CD-RW in a dirty old drive, I was rewarded with completed install of 10.04.3 LTS. :-)

Now obviously the performance is not mind blowing, so my question is this:

What is the difference in performance of the resulting installation on a low-end system for minimal, alternate and netbook?

My first choice was  "ubuntu-10.04-netbook-i386.iso" but it failed with what seemed like low memory error. So I tried the alternate install but now I'm wondering if I've coaxed it through a full install by using the alternate and now I have a system that is a bit bloated for the little old netbook I'm using. Would I get better performance if I was alble to re-install using either the netbook or MinimalCD installs?

---

### Post by Nytram on 2011-08-22
You'd be better off with Lubuntu - Ubuntu Light - which is designed for lower spec hardware and should run well on your netbook.

---

### Post by lykwydchykyn on 2011-08-22
The *alternate* install installs a normal Ubuntu, just using a text-mode installer.  

The *minimal* just installs a bare command-line system and lets you choose which desktop (if any) to install (that's what I understand, haven't used it).

The netbook version (is it even still around?) installs a desktop designed for the netbook.

On 192 Mb of ram, I would agree with Nytram -- you'd be best off selecting LXDE or Lubuntu, or some other lightweight window manager.  This can be done from the minimal install, I believe.

---

### Post by gmargo on 2011-08-23
> **lykwydchykyn said:**
> The *alternate* install installs a normal Ubuntu, just using a text-mode installer.  

The alternate install also has a handy "command-line-system only" installation mode, if you hit F4 at the opening screen.

---

### Post by Innigo on 2011-09-04
Thanks guys, it sounds like the best way would have been:
Alternate Install >  F4 at opening screen > Lubuntu  (or just Lubuntu standard install :-)

---

### Post by azertyh on 2011-09-05
> **gmargo said:**
> The alternate install also has a handy "command-line-system only" installation mode, if you hit F4 at the opening screen.

minimal = alternate "command-line-system only" isn't it?

---

### Post by gmargo on 2011-09-05
> **azertyh said:**
> minimal = alternate "command-line-system only" isn't it?

The major difference to me is probably that the so-called "minimal cd" does not contain any installable software. It requires a working network connection to do anything at all.  It's really a "network install cd".

In contrast, with the alternate cd, you can get a fully working system up and running, with no network or downloading required.

---

### Post by el_koraco on 2011-09-05
> **gmargo said:**
> The major difference to me is probably that the so-called "minimal cd" does not contain any installable software. It requires a working network connection to do anything at all.  It's really a "network install cd".


Well, yeah, the minimal CD is really the Debian "netinst CD". The alternate install is the standard text-based Debian installer. They're just branded differently.

---

