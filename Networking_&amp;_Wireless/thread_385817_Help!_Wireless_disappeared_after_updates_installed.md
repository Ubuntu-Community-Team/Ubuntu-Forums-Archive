---
title: "Help! Wireless disappeared after updates installed!"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by HumbleGod on 2007-03-16
So much for counting my chickens before they hatch...

Thanks to help in [_this thread_]("http://www.ubuntuforums.org/showthread.php?t=384185"), my Linksys WMP54GS wireless card (with Broadcom 4318 controller) was finally working. Then the automatic updates started flowing in (143 of them IIRC), and like the newbie that I am, I agreed to install them. And now, after rebooting, my wireless card doesn't even appear to exist in Ubuntu--it doesn't show up under Sys -> Admin -> Networking OR the menu for Network Manager, and nothing active shows up in [FONT="Courier New"]iwconfig[/FONT].

Has this happened to anyone else before? Any advice for resolving this?

Thanks!

---

### Post by whitefort on 2007-03-16
Arg...  I feel for you.

I installed Xbuntu Edgy and found that it couldn't see the PC's network card.  The kind folk here in the forum let me know that I needed to install something... the 'restricted' package, I think...  If no one appears with a more expert reply, let me know and I'll look up my other machine and see what I had to do to get it working.

Anyway, I did that, and after a bit of messing about, my card appeared and wireless started working. Yippee!

Then, an hour later, I did the upgrade - POW!  The card was gone again.

If your problem is the same as mine, it's because the update changed the Linux kernel to a later version, which means you have to manually download and install the restricted wireless drivers for that later version.

To be honest, I'm a newbie, and very bad at this - as I say, if no one else appears with a better solution, let me know and I'll check and let you know exactly what I had to installl.

---

### Post by HumbleGod on 2007-03-16
Well, it certainly did upgrade to a later kernel--I was using 2.6.17.10, upgraded to 2.6.17.11--so that's the likely culprit, although several other things updated so I'm not ruling anything out. And yeah, it all still works when I boot using 2.6.17.10. But I never used any "restricted" drivers AFAIK--the guide I followed (see above link) involved using the manufacturer's own driver.

The closest I found to a similar problem was in [this thread]("http://www.ubuntuforums.org/showthread.php?t=383743&highlight=update"), and I don't think either of the two drivers that caused that guy conflicts are to blame here. (Typing neither[FONT="Courier New"] rmmod prism2[/FONT] nor [FONT="Courier New"]rmmod orinoco[/FONT] caused anything to happen; the system apparently doesn't think they're here.)

Am I better off just sticking to 2.6.17.10 for now? I'd hate to have to lose wireless connectivity every time I update kernels....

---

### Post by Glenn Jones on 2007-03-16
Hey Guys

Yeah I had the same problem on my laptop when the new *.11 kernel was updated. I use linuxant to get my wireless working and I tried to update that to the .11 version but that didn't work either because it couldn't see my wireless card. I then  decided to go for the nuclear option and re-insatll ubuntu from the original cd I had with the .10 kernel. 

I've got my wireless card working (the blue light is on) but I live in a basement and share the wirless with the guy up-staris who has put a wep key on it. I configure my wirless using gnome-network manager, but after going nuclear I haven't got it. I know I need to download gnome-network-manager and something else, which I believe is network-manager. Can you guys remind me what this something else is? Also if I download it as a .deb file with that have all the dependancies? Why isn't this amazing tool included with ubuntu? 

Cheers

Glenn

---

### Post by HumbleGod on 2007-03-16
> **Glenn Jones said:**
> Hey Guys
I configure my wirless using gnome-network manager, but after going nuclear I haven't got it. I know I need to download gnome-network-manager and something else, which I believe is network-manager. Can you guys remind me what this something else is? Also if I download it as a .deb file with that have all the dependancies? Why isn't this amazing tool included with ubuntu? 

Yeah, there are a bazillion dependencies for those. Alternately (ha, a pun) if you have the 6.10 Alternate disc, it has network-manager, network-manager-gnome, and all the dependencies; just pull them off the disc.

---

### Post by Glenn Jones on 2007-03-16
Cheers. Where do I get this disk from? Is it on the Ubuntu web site?

---

### Post by HumbleGod on 2007-03-17
Yep, on the Downloads pages, pick a location near you to download from and click "Other Installation Options." Near the bottom of the following page are the downloads for the various Alternate CDs.

---

### Post by Glenn Jones on 2007-03-17
Thanks. This may seem like a stupid question but I can find the Dapper Alternate Cd but not the Edgy. Does this make a differece seeing as Im an Edgy user and all I want is the gnome-network-manager and the dependencies that go along with that?

---

### Post by HumbleGod on 2007-03-17
The 6.10 alternate should be visible with the other 6.10 discs. Here's [a list from Portland State University]("http://mirrors.cat.pdx.edu/ubuntu-iso/edgy/"), for example; you would probably want ubuntu-6.10-alternate-i386.iso (or the torrent version of that) near the top.

---

