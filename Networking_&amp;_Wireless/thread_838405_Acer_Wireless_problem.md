---
title: "Acer Wireless problem"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Jiggy-Ninja on 2008-06-23
My laptop is an Acer Aspire 5520-5912, currently with Vista Home Premium but I'm trying out Ubuntu 8.04 on a LiveCD before I decide if I should switch.

I'm currently running the Vista OS because I can't figure out how to get Ubuntu to hook up with my wireless router. I can connect to the router through an Ethernet cable, but not wireless.

Some specs:

Wireless card: Atheros AR5007EG Wireless Network Adapter

Router: Belkin 54g F5D7230-4 Wireless G router
--Router is set to broadcast on 11g only.
--Wireless uses WEP encryption so my Nintendo DS can hook up with it.

On the Vista OS I had the wireless configured to use a static IP over wireless.

I've looked through the Network and Network Tools things in Ubuntu, but to no avail. I can't find anything about Wireless in either one. I also tried installing something like "ndisk" because the help suggested it, but I'm clueless on how to use it.

Other smaller, unrelated issues that would prevent me switching to Ubuntu:

1) Resolution. My current moniter runs with 1280 x 800 resulution, and 800 x 600 sucks hard in comparison. I can't figure out how to get the resolution higher than that though. I'd like to stay with my current resolution, but even 1024 x 768 would be fine. Just not 800 x 600.

Graphics card is nVidia GeForce 7000M

Moniter is 15.4" WXGA Acer CrystalBrite LCD (8ms/220nits)

2) What's the easiest (and most cost-effective) way to run the Zune software on Ubuntu? All the stuff I've found on Google or whatever is over a year old. Is it VirtualBox, WINE, or something else?

And don't give me **** like "Zune sucks" or "buy an Ipod". I'm stuck with my Zune, I like it, and I want to keep it.

3) As someone who wants to learn Japanese, I like the Language Bar in Vista that allows me to type in some text, say "sakura", and it can automatically convert the word to the appropriate hiragana (&#12373;&#12367;&#12425;), katakana (&#12469;&#12463;&#12521;), or even kanji (&#26716;). Is there a similar program for Ubuntu?

And finally, not really an issue, but an unrelated question

For my processor, my laptop's specs say "AMD Turion 64 x2 Mobile Technology TL-58 (1.9GHz, 2 x 512 KB L2 cache)". From the info I gathered at Acer's website, I think this means I could use the 64-bit version of Ubuntu. However, not knowing anything about computers that I can't find out by poking through menus and using context clues, I'd just like to make sure. What's the difference between 64-bit and 32-bit anyway?

---

### Post by jbraum on 2008-06-23
Try this works everytime w/my Acer (same wireless card)

[http://ubuntuforums.org/showthread.php?p=4999962](http://ubuntuforums.org/showthread.php?p=4999962)

---

### Post by ebmelle on 2008-06-23
The Ubuntu 64 bit version will perform fine, and run the 32 bit applications with no problem on your AMD X2.  The 64 bit OS can address much more memory, and is the future, but does not offer mush in enhanced performance a this time.

Regarding the video problem; installing the NVIDIA video driver (non-supported by Ubuntu), should solve the problem, but on cold boot you may have to delay the 'go' for booting a minute or so for the software to 'see' the drivers. (That has been my experience, but don't know why).

Cheers.

---

