---
title: "Upgrading graphics card Ubuntu 10.10"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by StormcrowofRohan on 2011-04-27
I'm a new Linux user and I'm not saavy with the workings quite yet, but I've heard two sides when referring to graphics cards. One side tells me that Nvidia is the best bet and ATI cards are nothing but an issue. On the other hand I have a few people telling me the opposite.
 
I am running Ubuntu 10.10 Maverick Meerkat and have been having issues with my old ATI Radeon x1600 Sapphire (128MB, I think). I installed the suggested package and everything seems fine. It's just that I would like to install a new card and actually run it to it's full extent and not just have it recognized.
 
As far as Invidia cards, without my current setup info(I'm not near my computer), could anyone suggest some relatively recent desktop cards with somewhat high compatibility with my OS and also older hardware? I'm thinking I may upgrade to a 512 MB.
 
I am completely new to Nvidia and know nothing about the cards. It gives me a headache searching their website. I'm not sure what all the Tesla, ION, GeForce stuff is! lol I just need a good list of recent cards
 
I'll post my other hardware, minus the current video card when I get back to my desk.
 
Thanks in advance
SoR

---

### Post by will547_us on 2011-04-27
I hope this helps

See LowSky's reply [http://ubuntuforums.org/showthread.php?p=10709195](http://ubuntuforums.org/showthread.php?p=10709195)

Cheers, Will

---

### Post by cek on 2011-04-27
nVidia's linux support is much, much better than ATI's.  Generally you'll here ATI is slightly better in the price for performance category, however if linux support is at all a concern, nVidia is the clear choice.

Here's a helpful article on the nVidia chipsets, since I agree they are VERY confusing:

[http://www.hardwaresecrets.com/article/132](http://www.hardwaresecrets.com/article/132)

---

### Post by K_45 on 2011-04-27
Each person will tell you different. I would say don't buy a GPU for Linux unless you want to play modern games or run certain software that could take advantage of the card. If that doesn't apply the built in chip is fine, and for an IGP, I'd go with ATI. My HD 4250 is running fine with the fglrx proprietary driver.

---

### Post by wolfen69 on 2011-04-27
Do you have a AGP or PCIx slot? Anyway, I would go with nvidia. Since 2004, nvidia has never let me down, no matter what distro I used.

---

### Post by Fedz on 2011-04-27
> **wolfen69 said:**
> Do you have a AGP or PCIx slot? Anyway, I would go with nvidia. Since 2004, nvidia has never let me down, no matter what distro I used.
I second that ... same here with me never a problem on any PC I've installed Ubuntu on ... nvidia are well known for their linux support & compatibility but each to their own :)

---

### Post by StormcrowofRohan on 2011-04-27
Motherboard: Foxconn 761GXK8MB,4 PCI slots 
             (capabilities: isa, pci, pnp, apm)
Processor: AMD Athlon 64 4000+
RAM: 2GB

I think that's about all the info I can provide given my limited knowledge...

---

### Post by K_45 on 2011-04-27
You'd want an 8400GS - but choose the right model. Silent needs airflow in you case, and the fan models vary in quality.

---

### Post by bodhi.zazen on 2011-04-27
Arguments about ATI vs nvidia is like Linux vs Windows or Gnome vs KDE.

When purchasing any hardware, google search to make sure your OS supports it ;)

As long as you are using a supported {ATI,Intel,Nvidia} card you are fine, likewise as long as you are using an unsupported {ATI,Intel,Nvidia} card it will sort of suck (*cough* GMA500 *cough*)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

The only "problem" with those lists is that they are somewhat optimistic. The gma500 for example works, but it takes some effort =)

---

### Post by albert s on 2011-04-27
I have an 8400GS PCI-e with a built in fan, IIRC it has inbuilt 512MB as I went for it cos my mobo can only handle 1G so I wanted to try and keep it for other stuff,
I watch normal DVDs and do a little streaming and all is well with the world,
I had a few issuses at the very beginning to get it set up properly for my monitor, but I got a new 21" widescreen at xmas and it fired up straight out of the box.  :D
couldnt be happier with my graphix card if truth be told, and Im a noob with all this stuff too.

---

### Post by albert s on 2011-04-27
ps, to find out what your PC is running currently and everything that is in there you can open a terminal and type

```
sudo lshw
```

it will ask for your password, type it in, nothing will show up but dont worry, then hit return and all your computer guts will be shown to you.
HTH,

---

### Post by StormcrowofRohan on 2011-04-27
Thanks for all the replies! :)  I used "sudo lshw", but it spits so much out it takes me an hour to filter out my actual devices. I'm not computer savvy enough to be able to read it, yet. rofl

---

### Post by K_45 on 2011-04-27
Try

```
sudo lshw -html > results.html && firefox results.html
```

---

### Post by xd20 on 2011-04-27
I have an 8400gs PCI and it doesn't work with ubuntu at all.  In fact, whenever it's in my computer, ubuntu fails to load, only leaving a bunch of error codes.  The only way I can load ubuntu with the card in the computer is if I turn on my onboard graphics, which I hate completely.

So 8400gs isn't exactly the safe bet for ubuntu.  I've been trying to resolve the issue for 6 months on this community forum and no one has come up with a decent suggestion aside from "get a new computer" or "get a new graphics card"

---

### Post by StormcrowofRohan on 2011-04-27
I'm sorry to hear that about your card.  

I'm still shopping for one myself and it's tough figuring out what exactly you need, if it's better than the one you have, and if it will run on your OS...  

I'm sure there are other things to consider as well, but I'm having to study graphic cards to really make an intelligent decision. lol

I was checking out the 8400 GS, but I find it is older than my old one. lol  So, I'm considering the GeForce GT 240.  The 8400 GS looks like it came out in 2007, while the 240 came out in '09.  

EDIT:

Nevermind on the GT 240, it's not compatible.  So, I guess I need to either locate a 9800 GT or...I have no idea.  Is it just me or is it a pain in the butt trying to get an Nvidia card that's compatible? lol

---

### Post by K_45 on 2011-04-27
> **StormcrowofRohan said:**
> I'm sorry to hear that about your card.  

I'm still shopping for one myself and it's tough figuring out what exactly you need, if it's better than the one you have, and if it will run on your OS...  

I'm sure there are other things to consider as well, but I'm having to study graphic cards to really make an intelligent decision. lol

I was checking out the 8400 GS, but I find it is older than my old one. lol  So, I'm considering the GeForce GT 240.  The 8400 GS looks like it came out in 2007, while the 240 came out in '09.  

EDIT:

Nevermind on the GT 240, it's not compatible.  So, I guess I need to either locate a 9800 GT or...I have no idea.  Is it just me or is it a pain in the butt trying to get an Nvidia card that's compatible? lol

 Problem is you only have PCI slots, and that 240 only comes in PCI-E.   

EDIT: Seems like the 8400GS is your only choice for something even vaguely new.

---

### Post by xd20 on 2011-04-28
Don't get an 8400gs PCI card.. it won't work with ubuntu... at all.. you won't even make it to the GUI, just a nonstop loading screen.  That's my issue.

---

