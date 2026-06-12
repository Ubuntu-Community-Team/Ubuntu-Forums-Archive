---
title: "Ubuntu with 1.5 GB RAM - how far can I go?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Anuovis on 2011-03-03
Hello,
I am using 10.04 now with 2Ghz dual core processor and only 512 MB of RAM. The system is a bit sluggish at times, especially when I try to run more applications at once but I do not have big needs (web, office apps, music, movies) and get by fine most of the time.

Planning to upgrade it to 1.5 GB now but I am a bit worried whether that will be enough for the upcoming 11.04 and beyond. 

From your own experience and the trends of Canonical, how long could I use Ubuntu after the upgrade?

Would it be wise to switch to Xubuntu instead? Is it just a lighter graphical interface with lighter apps or would I lose something more by doing that? I do not care much about flashy desktop effects, more about functionality.

And I know a new laptop might be better but at present I can not see any need to really upgrade it, barring the need to have a decent OS inside.

---

### Post by TeoBigusGeekus on 2011-03-03
I'd go for Lubuntu. You could even get away with 512mbs with it.

---

### Post by maqtanim on 2011-03-03
512MB is a low requirement for Ubuntu. Currently I am using 1GB to run Ubuntu 10.04. with 1.5GB it should run smoothly couple of few years. 

Xubuntu is a good choice for you, if you donot want to upgrade the RAM. And Lubuntu is a better option!

---

### Post by Mark Phelps on 2011-03-03
There's no reason to suspect that newer versions of Ubuntu will demand significantly more RAM than the current versions.

RAM is fairly cheap these days.  Upgrading your RAM certainly won't hurt -- and it is likely to improve performance -- a bit.

But, don't expect miracles.  I went from a PC with 2GB of DDR 400 RAM to a machine with 4GB of DDR3 1600 RAM, and while it is faster, it's not a LOT faster.

---

### Post by Anuovis on 2011-03-03
Is it difficult to go for Xubuntu for a Linux newbie? I have been having all sorts of problems and what helped me the most was the huge amount of articles, resources and tutorials by the Ubuntu community. So many people use it all around, it is easy to find answers to problems. Also, many books and such.

Would I suffer in this regard by going to Xubuntu? Also, are there any Ubuntu apps you can not use with Xubuntu?

---

### Post by Rex Bouwense on 2011-03-03
As has already been stated, RAM is cheap these days but I am operating right now on an old Dell Inspiron 1000 with only 512 Mbs of RAM.  My operating system is Ubuntu 10.04 Lucid Lynx and for basic computing it has been working just fine. While changing from Ubuntu to Xubuntu and increasing your RAM may increase your speed and the learning curve for Xubuntu is not that great you have to ask yourself do I like what I have and if you do keep it.  If you are unhappy go for the change.

---

### Post by vaah on 2011-03-03
> **Anuovis said:**
> Is it difficult to go for Xubuntu for a Linux newbie? I have been having all sorts of problems and what helped me the most was the huge amount of articles, resources and tutorials by the Ubuntu community. So many people use it all around, it is easy to find answers to problems. Also, many books and such.

Would I suffer in this regard by going to Xubuntu? Also, are there any Ubuntu apps you can not use with Xubuntu?
 No i don't think you would, going to xfce or lxde is easy. You don't need to reinstall the whole thing, instead, type in:
```
sudo apt-get install xubuntu-desktop
```
then you can select xfce as your session at login screen. If you don't like it just go back and choose gnome at login screen again. :)

---

### Post by Kirboosy on 2011-03-03
Ok, since you are running 32 bit you can only go to 3.25 Gb of RAM (that is if your motherboard can handle it)

What kind of Dual Core processor is it?

---

### Post by Anuovis on 2011-03-03
Thank you all for the answers.


> **Caboose885 said:**
> Ok, since you are running 32 bit you can only go to 3.25 Gb of RAM (that is if your motherboard can handle it)
It can only go up to 2GB. I am using one slot with 512 chip, so I can plug in another with 1GB or pull this one out and install 2x1GB but I doubt 500 MB will make a huge difference anyway.

It's an oldish Dell Inspiron 6400 laptop.

> What kind of Dual Core processor is it?
Intel Centrino Duo

---

### Post by Dragonbite on 2011-03-03
I have 2 systems I run Ubuntu on (Pentium 4 @ 2.4 GHz w/2.5 GB of RAM and Pentium M @ 1.6 GHz and 1 GB of Ram).

Both of these systems I haven't had to "turn down" or go with "lesser resource" applications (e.g. use Xfce instead of Gnome, use Abiword instead of OpenOffice).

Moving from 512 MB or Ram to anything over 1 GB will make a noticeable difference, but above that the difference is not as drastic or visible.

Ubuntu should run fine.  People are getting so spoiled with massive systems when older ones still work fine.

Plus, on my current P4 system I have Windows 7 installed as well.  If I ever start not appreciating my Ubuntu all I have to do is fire up Windows 7 and I'll be appreciating Ubuntu all over again (once I can get the system to reboot...)!

Before my current P4 I had a P4 @ 2GHz with 512 MB of Ram and it was useable. Wasn't the fastest, but also wasn't ground to a halt.

So I would do the RAM upgrade and look at your video card as well. That makes a difference on the "look and feel" aspects.

---

### Post by Kirboosy on 2011-03-03
> **Anuovis said:**
> Thank you all for the answers.



It can only go up to 2GB. I am using one slot with 512 chip, so I can plug in another with 1GB or pull this one out and install 2x1GB but I doubt 500 MB will make a huge difference anyway.

It's an oldish Dell Inspiron 6400 laptop.


Intel Centrino Duo

Ah! I just sold my e1505 (the exact same laptop but a different number) I had 4 Gb of RAM in it and Ubuntu detected 3.25 (in the BIOS it saw all 4)

What BIOS revision are you running? (It should pop up when you boot the laptop A**)

---

### Post by matt_symes on 2011-03-03
Hi

If you getting a lot of hard drive thrashing due to swapping just buy more ram. There will be plenty of life left in it then.

Dragonbite's post is spot on.

Kind regards

---

### Post by beew on 2011-03-03
If you are planning to upgrade it to 1.5 G of ram you can easily run a full Ubuntu desktop (ie, no need to go the route of Lubuntu or Xubuntu if ram is your concern). I have only 1 G in a 6 year old Dell Latitude D410 and it is running Compiz in full glory and it is incredibly fast too (Ubuntu 10.10 and 10.04) The only problem is watching hd video, it gets really hot after a bit but I don't think this is a ram issue only. Dell apparantly was sued in a class action suit for its laptops overheating, this is one of those. Of cause you can't play fancy games in a machine like that regardless of OS, it is not what it is made for anyway.

Well in my experience 512 m would be a little low (but I have heard people who say otherwise), I have an even older machine with only 512M of ram. I also installed Ubuntu 10.10 on it but with the option of dropping down to openbox if needed. I tried Lubuntu on it and don't find it to be any better than Ubuntu+ (openbox if needed)
route. I don't like Lubuntu personally, find it too buggy and too many things missing (like the search function in Synaptic, you need to install it from Synaptic because they take it out, supposedly to make the distro "lighter"?)

---

### Post by ankspo71 on 2011-03-03
Hi,
I predict 1.5 GB of ram will be sufficient enough for Linux for a couple/few years to come. My wife's AMD Sempron 1.8ghz with 1.5 GB of ram is enough to handle everyday tasks with Ubuntu (she's a windows XP user, but she has already let me try Ubuntu with her on her computer). I'm satisfied with my Pentium-4 3.0ghz with 2GB of ram running Kubuntu too - at least for now.

If you have an older computer, and since memory will be cheaper for older computers, I recommend getting as much ram as you can without exceeding your motherboard's specifications, that way you'll have enough memory to do memory intensive things for a longer time to come.

Don't forget to count the number of pins on your existing memory card (count both sides together), and check the labels on the card to identify it, before you do any purchasing. Also search Google for your computer's make and model so you can find some specifications, such as memory card type, number of memory card slots (dimm slots), and maximum allowable memory.

Hope this helps.

---

### Post by Anuovis on 2011-03-03
Thanks for all the tips. I will definitely do some research before buying more memory. One thing though... does it matter whether the maker is different for another chip, if all else (pins and such) matches?

> **Caboose885 said:**
> Ah! I just sold my e1505 (the exact same laptop but a different number) I had 4 Gb of RAM in it and Ubuntu detected 3.25 (in the BIOS it saw all 4)

I am pretty certain my motherboard can not support more than 2Gb physically, at least Dell says so. Have you bypassed that?

---

### Post by kn0w-b1nary on 2011-03-03
3.25 gig of RAM is all a 32-bit system can handle.

1.5 gig of RAM is enough to use Gnome, but I use Xubuntu with 512 mb of RAM and it works great, and is faster than if i was using Gnome.

Just my 2 cents.

---

### Post by Kirboosy on 2011-03-03
2 Gb is really the maximum you will need. The only reason I ran 4 in my laptop was because I had a 2Gb. stick given to me (even though I already had two installed) Rather than letting it collect dust I installed it in my computer...

Anything over 1Gb. will be the sweet spot for your computer. The only time you might see an improvement with more than 2 Gb is if you are playing Games or something GPU intensive. Since your GPU draws off your RAM you will notice improvements then. 

Is yours graphics Intel, NVIDIA, or ATI? (I had ATI in mine and it was terrible ever since Ubuntu 10.04+. They never did fix that issue either.)

---

### Post by matt_symes on 2011-03-03
Hi

> 3.25 gig of RAM is all a 32-bit system can handle.

Eh? What about installing a pae kernel et al.

Kind regards

---

### Post by kn0w-b1nary on 2011-03-03
> **matt_symes said:**
> Hi

Eh? What about installing a pae kernel et al.

Kind regards

Oops, Using my old Windows knowledge. :oops:

---

### Post by LowSky on 2011-03-03
remove the 512mb, and add 2gb... 

also gighertz mean nothin these days. there are chips that run at 1.3ghz that will out run older 3.0 ghz chips.

if you want a faster system think of using less resources. use less intensive apps and dont run desktop effects

---

### Post by Anuovis on 2011-03-03
> **Caboose885 said:**
> The only reason I ran 4 in my laptop was because I had a 2Gb. stick given to me (even though I already had two installed) Rather than letting it collect dust I installed it in my computer...

Does it mean I could push my laptop like that as well?


> Is yours graphics Intel, NVIDIA, or ATI? (I had ATI in mine and it was terrible ever since Ubuntu 10.04+. They never did fix that issue either.)
ATI. And it has terrible support for both Windows and Ubuntu. 

On Ubuntu it is enough to display 2D things and some non-intensive 3D stuff. But I do not need the latter anyway, so not that of a problem for me.

Windows have no normal official support now, had to rely on 3rd party drivers. Ubuntu often handles it better.

---

### Post by Dragonbite on 2011-03-03
> **LowSky said:**
> remove the 512mb, and add 2gb... 

also gighertz mean nothin these days. there are chips that run at 1.3ghz that will out run older 3.0 ghz chips.

If you think about it, most Netbooks are pretty capable and they're running at around 1.6 GHz (Intel Atom) and most are single-core (now they are turning dual-core, but before now).  

I know there are other performance factors, but looking at the GHz, it doesn't need to be in the 2,3,4+! range.

---

### Post by philinux on 2011-03-03
> **Anuovis said:**
> Hello,
I am using 10.04 now with 2Ghz dual core processor and only 512 MB of RAM. The system is a bit sluggish at times, especially when I try to run more applications at once but I do not have big needs (web, office apps, music, movies) and get by fine most of the time.

Planning to upgrade it to 1.5 GB now but I am a bit worried whether that will be enough for the upcoming 11.04 and beyond. 

From your own experience and the trends of Canonical, how long could I use Ubuntu after the upgrade?

Would it be wise to switch to Xubuntu instead? Is it just a lighter graphical interface with lighter apps or would I lose something more by doing that? I do not care much about flashy desktop effects, more about functionality.

And I know a new laptop might be better but at present I can not see any need to really upgrade it, barring the need to have a decent OS inside.

See here.

[http://ubuntuforums.org/showthread.php?p=9517069#post9517069](http://ubuntuforums.org/showthread.php?p=9517069#post9517069)

---

### Post by Kirboosy on 2011-03-03
> **Anuovis said:**
> Does it mean I could push my laptop like that as well?



ATI. And it has terrible support for both Windows and Ubuntu. 

On Ubuntu it is enough to display 2D things and some non-intensive 3D stuff. But I do not need the latter anyway, so not that of a problem for me.

Windows have no normal official support now, had to rely on 3rd party drivers. Ubuntu often handles it better.

Well you could try but honestly 2 would be the max you need. You will see vast improvement. 

That ATI card (x1400 I believe) has terrible 3D gaming reviews. It will never be a "gaming laptop" so 2 Gb would be fine. (especially running Ubuntu ;) )Really your 1.5 Gb plan would work fine as well. 

Right now the reason you have video problems is because your card is choking out your RAM because you have so little available.

[This RAM will work with it]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820148161")

or this is what I had...

[Crucial]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820148162")

In my opinion [this is the better RAM than mine]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233079")

---

### Post by Anuovis on 2011-03-03
> **Caboose885 said:**
> That ATI card (x1400 I believe) has terrible 3D gaming reviews. 
Right now the reason you have video problems is because your card is choking out your RAM because you have so little available.

True, that card is not recommended for serious gaming. But I don't, so no problem there.

Thanks for all the input everybody, much appreciated. Marking as solved.

---

