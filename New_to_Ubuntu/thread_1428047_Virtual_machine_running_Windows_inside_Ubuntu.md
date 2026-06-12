---
title: "Virtual machine running Windows inside Ubuntu"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by random turnip on 2010-03-12
Hey, i want to delete my Windows partition to save some HDD space more than anything, that isn't the problem.  I'm not quite ready to go pure Ubuntu, and still need Windows for things like my iPhone...

I know you can run Ubuntu through a virtual machine in Windows, i was wondering if you can do it the other way round, is there a virtual machine program that runs in Ubuntu?
If not, would the Windows one run through Wine?

I assume after installing Windows (i have a disk lying around my house somewhere) i would just be able to install all drivers and what not off the internet like normal or use the drivers disk for my laptop that i'm yet to find.



Long post, but my main questions are:
[LIST]
[*]Is there a virtual machine that'll run Windows in Ubuntu?
[*]If not will the Windows one run in Wine?
[*]Is installing Windows on there the same as installing it normally?[/LIST]

---

### Post by Beowulf.1000 on 2010-03-12
Yes you can run Windows inside Ubuntu. I just set this up on both my desktop and my laptop this past week. But I would keep dual boot for now, because graphics is sub par with a virtualized Windows. I also had problems getting a virtualized Windows 7, no success, luckily I had a legal copy of Windows XP. Some have been able to do Win 7 though. I also tried a virtualized Ubuntu in Windows 7 but that sucked compared to native Ubuntu running virtualized Windows XP.

There is an entire Virtualization forum here so that is a good place to go. But in short, fire up your package manager and search for virtualbox (VB), then install it, plus the 'guest addition' package for it. It will then show up in your Accessories menu. Then, running VB, you create a new virtual machine using the menus, put your Windows install CD in your drive, click Start for the new machine, Windows installs. Shazam, you have a virtual Windows running in Linux.

With the guest additions, you can do some cool stuff. Like Ctrl+f to go full screen Windows and it looks just like normal Winblows. Or Ctrl+L (or Ctrl+H, I forget) and Windows apps run in 'seemless' mode and appear as windows on Linux desktop, very cool and weird at the same time.

But beware, virtualized Windows has pretty shabby (I would say useless) playback of e.g. *full screen* youtube videos (smaller normal sized playback is acceptable), so keep your Windows partition and dual boot for now. Virtual Windows does not make use of your 3D acceleration of your graphics card, etc. so forget most funky gaming (better to go with Cedega for linux from Transgaming for that-- runs great, I used to use it for Diablo II and World of Warcraft and it ran those games better than native Windows, no kidding).

I tried VMware also, a free alternative to virtualbox, but vmware sucked imho. virtualbox is from Sun Microsystems, they know their stuff. They also have a $ version of virtualbox called PUEL, compared to the OSE free version. PUEL allows seamless USB access I have heard.

In the virtual Win XP I was able to easily download and install the drivers for my Brother 2170w printer, etc. The Virtualized Windows makes use of NAT for internet, so it simply bootstraps on your Linux networking so no config of networking required in the virtual Windows. And the virtual Windows did normal Windows updates, etc. For me, it is great, I have access to a couple of Windows programs that there simply is not acceptable alternative in Linux -- like Movie Magic Screenwriter (I hate Celtx, sorry) and Sibelius 6 for music notation and composition (because I just can not figure out JACK and Sibelius 6 is incredible and has incredible orchestral sounds).

Have fun, play safe :)

---

### Post by howefield on 2010-03-12
> **Beowulf.1000 said:**
> virtualbox is from Sun Microsystems, they know their stuff. They also have a $ version of virtualbox called PUEL, compared to the OSE free version. PUEL allows seamless USB access I have heard.

Just to clarify, the difference between PUEL (Personal Use & Evaluation License) and OSE (Open Source Edition) versions isn't "$". Both versions are free.

PUEL includes some closed source code that isn't in the OSE version, giving Virtualbox added functionality.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by Beowulf.1000 on 2010-03-12
Okay thanks for clarifying. Looks like PUEL can be free, or not, depending.
  [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)
Most people can use it free from what I read at the above link, but for commercial use like in a business environement it looks like it could cost $. I think I will migrate to PUEL once I feel comfortable with not losing my existing virtualized WinXP during the switchover.

---

### Post by howefield on 2010-03-12
> **random turnip said:**
> I assume after installing Windows (i have a disk lying around my house somewhere) i would just be able to install all drivers and what not off the internet like normal or use the drivers disk for my laptop that i'm yet to find.

Don't go spending too much time looking for that driver disk ;)

Virtualbox will supply your guest system with a set of Virtualised drivers. You can improve on these by installing guest additions after you create your guest. Guest additions include a better graphics driver that will allow you better screen resolution, amongst other things.

> Is installing Windows on there the same as installing it normally?

Yes. Drivers excepted as above.

---

### Post by JKyleOKC on 2010-03-12
> **Beowulf.1000 said:**
> Okay thanks for clarifying. Looks like PUEL can be free, or not, depending.
  [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)
Most people can use it free from what I read at the above link, but for commercial use like in a business environement it looks like it could cost $. I think I will migrate to PUEL once I feel comfortable with not losing my existing virtualized WinXP during the switchover.This excerpt, copied from the VirtualBox site, clarifies when it's necessary to buy a commercial license. I found it quite interesting!

[I]   6. What exactly do you mean by personal use and academic use in the Personal Use and Evaluation License? 

    Personal use is when you install the product on one or more PCs yourself and you make use of it (or even your friend, sister and grandmother). **It doesn't matter whether you just use it for fun or run your multi-million euro business with it.** Also, if you install it on your work PC at some large company, this is still personal use. However, if you are an administrator and want to deploy it to the 500 desktops in your company, this would no longer qualify as personal use. Well, you could ask each of your 500 employees to install VirtualBox but don't you think we deserve some money in this case? We'd even assist you with any issue you might have.
[/I]
It seems to say that you don't have to buy a license unless you're installing it in a company system. I added the emphasis on this aspect...

Incidentally, I'm running WinXP in VirtualBox under Xubuntu and have no problems at all with it.

---

### Post by Beowulf.1000 on 2010-03-12
Okay, so I was just about to install virtualbox PUEL to the 500 pcs in my house (I do a lot of rendering farm stuff with video)-- so do I need to pay for it? haha, just kidding!

---

### Post by pricetech on 2010-03-12
I'm using the OSE version on both my desktop and my laptop (with XP virtualized) and it works just fine.

I'm not recommending against the PUEL version, I just don't need its extra functionality in my particular case.

---

### Post by pricetech on 2010-03-12
> **Beowulf.1000 said:**
> Okay, so I was just about to install virtualbox PUEL to the 500 pcs in my house (I do a lot of rendering farm stuff with video)

Nice farm.

---

