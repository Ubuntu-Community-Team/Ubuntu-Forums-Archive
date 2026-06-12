---
title: "Weird problem with Linksys WMP54G"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by NikoKun on 2007-06-06
Hi,

I've had 7.04 installed for a couple week or so now, working as good as can be expected and I've enjoyed it. Problems here and there, but I've worked through them, most caused by my inexperience...

Today I had to buy a wireless card since I can't wire network cables into my new room... -_-  Anyway all I could get was a Linksys card... So now I have this (overpriced) Linksys WMP54G wireless PCI card installed, and it works fine in my windows dual boot, as I am making this post from windows, but now Linux refuses to work.

The only time I've been able to use linux, was when I booted up normally and really fast disabled networking.

All other times, the system just locks up and stays there.

I've even tried to reinstall Ubuntu 7.04 entirely thinking it was just some driver problem... but EVEN the CD locks up while trying to boot into that... It freezes at the nautilus loading screen thing after the 3rd icon or so.

Can anyone help me solve this one?

I can see in this forum other people have had some issues with Linksys as well... Is there nothing I can do?  I'd really hate to return this card to walmart, and I'm dirt broke right now... I can't believe linksys just wont work in linux, there has to be SOME way to get it working... @_@

Anyway,  Thanks in advance! >_</

---

### Post by NikoKun on 2007-06-06
I'm guessing I don't read enough before I make a post... @_@


Until I can check the card itself, I'm assuming I have the version 4.1 card... though I'd have to check it...  Since the ver4 doesn't seem to have any freeze problem and the 4.1 does.
Edit: the install CD has ver4.5 written on it... god dam...@_@

So just found this:
> Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too.

Um... can anyone help me repair this problem?  I'm not really sure how to fix this problem, now that I've already caused it... lol

dang I wish I would have known this issue before I installed the card... @_@

---

