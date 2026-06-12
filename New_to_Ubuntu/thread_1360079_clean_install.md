---
title: "clean install?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by liekomg on 2009-12-20
I have a dell mini 10v with xp installed. I tried ubuntu 9.10 via wubi to test drive it and see how it runs. It runs smoothly with no problems. I'm thinking of doing a clean install of Ubuntu 9.10 on my netbook for school/traveling use, meaning use office suite and web related programs. Is this a good idea? Right now, I'm defraging my hardrive and cleaning out any junk files and whatnot so installing won't take longer. Does anyone have any opinions on doing a clean install of Ubuntu 9.10 on a netbook? I have another computer with windows that I use for gaming and major school stuff.

---

### Post by cartisdm on 2009-12-20
Absolutely.  Are you going to do a clean install w/ a dual boot or go entirely Ubuntu?

---

### Post by Extract_Here on 2009-12-20
That sounds like a good idea. I would recommend going to Ubuntu.com and getting the netbook download.

---

### Post by raymondh on 2009-12-20
> **liekomg said:**
> I have a dell mini 10v with xp installed. I tried ubuntu 9.10 via wubi to test drive it and see how it runs. It runs smoothly with no problems. I'm thinking of doing a clean install of Ubuntu 9.10 on my netbook for school/traveling use, meaning use office suite and web related programs. Is this a good idea? Right now, I'm defraging my hardrive and cleaning out any junk files and whatnot so installing won't take longer. Does anyone have any opinions on doing a clean install of Ubuntu 9.10 on a netbook? I have another computer with windows that I use for gaming and major school stuff.

Do you plan to install via WUBI or install Ubuntu in its' own partition?

If thru wubi, remember that the performance of Ubuntu will depend on the condition/health of windows as Ubuntu will be a 'file' within windows.

If in it's own partition, you can:

- use the slider to allocate partition sizes between XP and Ubuntu or,
- use XP disk utility to create a 'unallocated' space.  During the install, you can select "use continuous free space" or,
- Create the partitions beforehand and select Manual.

Have fun.  happy ubuntu-ing.

---

### Post by liekomg on 2009-12-20
I'm going for just Ubuntu 9.10 installed, because I don't plan on dual booting Windows and Ubuntu. Windows XP on my netbook is really sluggish even with optimizer programs. I tried ubuntu netbook remix; it's not my taste and it seems that both uses the same amount of memory, so neither is faster or slower than the other. Desktop version is the way to go for me.

That and I have absolutely no idea on how to set partitions on a hardrive; I even tried looking at guides and I just dont want to risk messing up installation, so I feel that just doing a clean install would be easy. I won't be using windows on my netbook much anyway, also it's slow and bulky.

---

### Post by cartisdm on 2009-12-20
> **liekomg said:**
> I'm going for just Ubuntu 9.10 installed, because I don't plan on dual booting Windows and Ubuntu. Windows XP on my netbook is really sluggish even with optimizer programs. I tried ubuntu netbook remix; it's not my taste and it seems that both uses the same amount of memory, so neither is faster or slower than the other. Desktop version is the way to go for me.

That and I have absolutely no idea on how to set partitions on a hardrive; I even tried looking at guides and I just dont want to risk messing up installation, so I feel that just doing a clean install would be easy. I won't be using windows on my netbook much anyway, also it's slow and bulky.

I'm running Linux Mint on my netbook without any performance problems at all.  I also ran Ubuntu 8.10 for a little while and it was just as good so I think you'll be happy!

Let us know how the install goes

---

### Post by raymondh on 2009-12-20
> **liekomg said:**
> I'm going for just Ubuntu 9.10 installed, because I don't plan on dual booting Windows and Ubuntu. Windows XP on my netbook is really sluggish even with optimizer programs. I tried ubuntu netbook remix; it's not my taste and it seems that both uses the same amount of memory, so neither is faster or slower than the other. Desktop version is the way to go for me.

That and I have absolutely no idea on how to set partitions on a hardrive; I even tried looking at guides and I just dont want to risk messing up installation, so I feel that just doing a clean install would be easy. I won't be using windows on my netbook much anyway, also it's slow and bulky.

I'd like to recommend separating your /home from root (known as /).  /Home is where your personal files, settings, configuration files, etc reside.  That way, should you need to re-install for any reason, you just reformat/re-install root whilst still retaining your original configurations.

[Here's a tutorial]("http://www.psychocats.net/ubuntu/installseparatehome") for you to review should you decided.

Good luck.  have fun.

---

### Post by liekomg on 2009-12-20
The clean install worked out very well. Now, how do I change my usb back into a default drive to remove the ubuntu installer?

---

### Post by twright on 2009-12-20
> **liekomg said:**
> The clean install worked out very well. Now, how do I change my usb back into a default drive to remove the ubuntu installer?
If you write click on it in Ubuntu there is a format option - do this is you don't want to save any files else just delete the files added (use ctrl+h to get all of them, including the hidden ones).

---

### Post by liekomg on 2009-12-20
I'm sorry to be a bother, but I reformatted my usb drive and it's still called Install Ubuntu (G:), how do I set it's default name? It's a SanDisk Cruzer usb flash drive.

---

### Post by audiomick on 2009-12-20
go to places> computer.
you will see the drive listed there.
A right click should offer you "rename", or you can go into properties and rename it there.

---

### Post by liekomg on 2009-12-20
It's named properly on Ubuntu, but on windows it's still called install ubuntu, and it wont let me rename it. It doesn't have the installer in it, but it's still called just that. It's annoying lol

---

### Post by audiomick on 2009-12-20
That is annoying. Sorry I can't check it in xp. My old laptop doesn't start anymore, and the new one has Vista (Virus Inside, Switch To Apple :) ) on it.

---

