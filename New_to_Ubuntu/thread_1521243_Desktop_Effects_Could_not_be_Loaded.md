---
title: "Desktop Effects Could not be Loaded"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by ramrakhio on 2010-06-30
Dear All,

Im really New user of UBUNTU, I Have just download the ISO image, then i tried that in my OFFICE's System, I got the wonderful effects of desktop like woobles, Zoom. I feel very good at that time, then i just burned the ISO image on CD, nd installed UBUNTU 10.4 in my Home System which is P4, Intel with D845 motherboard, Built-en VGA card, when Im loading the Desktop effects it says, desktop effects could not loaded,..... What should i Do...?

Im Absolutely New to Linux, I want to transfer my self from Windows to this.........

Pls Help...

---

### Post by hackerseraph on 2010-06-30
you might need to install video card drivers. its a very simple process.

go to your top menu bar click System > Administration > Hardware Drivers and see if it wants you to enable any.

---

### Post by ramrakhio on 2010-06-30
dear [hackerseraph]("http://ubuntuforums.org/member.php?u=375773")

There is nothing to show......

---

### Post by eriktheblu on 2010-06-30
I don't think your hardware can handle the desktop effects. I would suggest a new graphics card, but I doubt you could find one that would work with your motherboard.

---

### Post by carbine83 on 2010-06-30
I've looked up your graphics on the  Intel D845 motherboard, and it can't handle accelerated graphics at all. In another forum I found, people can't use Aero in Vista or W7 either, so it's not Ubuntu, it's the on board graphics. 

Might be able to pick up an older AGP Nvidia or something from e-bay? 

Something like this should do the trick 

[http://cgi.ebay.co.uk/64MB-Geforce-FX5200-Dual-DVI-AGP-8X-Graphics-Card-NEW-/270567795003?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3eff18e93b](http://cgi.ebay.co.uk/64MB-Geforce-FX5200-Dual-DVI-AGP-8X-Graphics-Card-NEW-/270567795003?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3eff18e93b)

If your graphics card did handle accelerated graphics, I feel this may cause you other problems, as setting 'extra' on desktop effects enabled the compiz theme manager, and that would slow your CPU right down anyway. If you get a Graphics card, that will take the load off the CPU.

Hope this helped!

---

### Post by warfacegod on 2010-06-30
> **carbine83 said:**
> I've looked up your graphics on the  Intel D845 motherboard, and it can't handle accelerated graphics at all. In another forum I found, people can't use Aero in Vista or W7 either, so it's not Ubuntu, it's the on board graphics. 

Might be able to pick up an older AGP Nvidia or something from e-bay? 

Something like this should do the trick 

[http://cgi.ebay.co.uk/64MB-Geforce-FX5200-Dual-DVI-AGP-8X-Graphics-Card-NEW-/270567795003?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3eff18e93b](http://cgi.ebay.co.uk/64MB-Geforce-FX5200-Dual-DVI-AGP-8X-Graphics-Card-NEW-/270567795003?cmd=ViewItem&pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3eff18e93b)

If your graphics card did handle accelerated graphics, I feel this may cause you other problems, as setting 'extra' on desktop effects enabled the compiz theme manager, and that would slow your CPU right down anyway. If you get a Graphics card, that will take the load off the CPU.

Hope this helped!

I have the Go5200. Same as that card but for laptops and I wish to hell I have better card. Faster GPU and more RAM on it. The drivers work great for it and Compiz runs okay all things considered. You ***won't*** be able to have say Compiz Cube enabled and watch a video in Fullscreen at the same time.

Don't get me wrong, it's a good suggestion but I'd look for something with more RAM. 256 MB or better.

---

