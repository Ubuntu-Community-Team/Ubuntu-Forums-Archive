---
title: "Need AGP Nvidia video card"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-15
I need a AGP Nvidia video card that has drivers that will load automatically in Ubuntu 10.10. I'm new to linux, my video card is freezing, so I need a new video card and it has to be simple to set up and cheap, did I say cheap? yes I did. Someone said Nvidia 5XXX and some people said 6XXX and above. I don't need much of a card just one that is simple to set up.

---

### Post by jerrrys on 2011-02-16
lots of cheap agp cards here

[http://computers.shop.ebay.com/Graphics-Video-Cards-/3762/i.html?Interface=AGP%7CAGP%2520%252F%2520PCI%7CAGP%25202x%7CAGP%25204x%7CAGP%25208x%7CAGP%2520Pro%7CAGP%2520Pro%25208x&rt=nc&Chipset%2520Manufacturer=NVIDIA&_catref=1&_dmpt=PCC_Video_TV_Cards&_fln=1&_ssov=1&_trksid=p3286.c0.m282]("http://computers.shop.ebay.com/Graphics-Video-Cards-/3762/i.html?Interface=AGP%7CAGP%2520%252F%2520PCI%7CAGP%25202x%7CAGP%25204x%7CAGP%25208x%7CAGP%2520Pro%7CAGP%2520Pro%25208x&rt=nc&Chipset%2520Manufacturer=NVIDIA&_catref=1&_dmpt=PCC_Video_TV_Cards&_fln=1&_ssov=1&_trksid=p3286.c0.m282")

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=agp&as_qdr=all&sa=Google+Search&lang=en#894](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=agp&as_qdr=all&sa=Google+Search&lang=en#894)

---

### Post by BicyclerBoy on 2011-02-16
As this is a Multimedia & Video forum...

There is no AGP video card that supports VDPAU.
There are PCI video cards for the PCI interface.

8400GS PCI with 512MB
9400GT PCI 512MB
9500GT PCI 512MB

TV OTA DVB-T H264 1080i is okay with the **8400GS** card using simple (1x temporal) de-interlacing filter.

Spend real money on this card & **it is wasted**..get a new mobo..

At least a PCI video card can still be used in a (most) modern mobos.

No HDMI interface, no digital audio.
AFAIK PCI will struggle to display HD1080i **without** VDPAU.

---

### Post by Jon Anderson on 2011-02-16
I have been looking in ebay and it looks like I can buy any Nvideo Card I want. So Im looking for something that is inexpensive But it has to be easily installed as far as the drivers are concerned . Ideally just install it and it can be recognised and drivers installed and set up. It probably is asking for to much but Im new to linux and Ive read a few descriptions of installing drivers and I dont have a clue.  My old Via/s3g is freezing the screen. I need very little when it comes to a video card, I dont do games, I watch some you tube . So simple and inexpensive is the word.

---

### Post by Jon Anderson on 2011-02-16
Sorry has to be a APG card

---

### Post by NightwishFan on 2011-02-16
[QUOTE="Wikipedia"]As of 2009, AGP cards from Nvidia have a ceiling of the GeForce 7 Series[/QUOTE]

Here is what I learned.

---

### Post by nynoah on 2011-02-16
Until Nvidia decides to support the Linux community I will not support them.  Nvidia has decided lately that they will not release drivers for any of their Optimus style boards to the linux community.  

My personal recommendation is until Nvidia starts to support us, don't support them.  You can do as you please.  But I would recommend ATI just because of this issue.

---

### Post by overdrank on 2011-02-16
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by mc4man on 2011-02-16
> did I say cheap? yes I did. Someone said Nvidia 5XXX and some people said 6XXX and above. I don't need much of a card just one that is simple to set up.
Most likely a 6000 series card will be ok for you, you can use the nvidia-current drivers on 6000 and up. (the 173 drivers can also be used but generally the current ones work better. There is also nouveau drivers which also may suit your needs/hardware just fine.
I wouldn't bother w/ a 5000 series or older at all
(Have 7600 & 7800 that works fine here but probably more than you need to spend

When looking at you should ck. to see if the card needs/has an external power connnector, if so make sure it's available in your case/wiring, otherwise you'll be disappointed when it shows up.

>  is until Nvidia starts to support us, don't support them
From my perspective (desktops and laptops) nvidia has supported linux just fine and likely will continue to do so. Could care less if their drivers are closed source..

---

### Post by 3rdalbum on 2011-02-16
> **nynoah said:**
> 
My personal recommendation is until Nvidia starts to support us, don't support them.  You can do as you please.  But I would recommend ATI just because of this issue.

ATI's driver is missing features too. In fact, it's also missing a huge chunk of performance compared to Nvidia's driver.

To the OP: If you didn't mind going ATI, then there's a manufacturer called PowerColor which makes recent ATI cards in AGP versions; however these are probably not going to be very cheap. You could try finding a GeForce 7xxx card in AGP which should work fine in Ubuntu, or if you have any spare PCI slots (not PCI-E) you can follow the suggestion from an earlier poster about finding an 8xxx card in PCI.

---

### Post by nynoah on 2011-02-16
> From my perspective (desktops and laptops) nvidia has supported linux just fine and likely will continue to do so. 

No Nvidia is not.  Nvidia will not release the drivers for the Optimus style chips.  It is a nightmare for people who want to buy a new laptop.  Optimus is everywhere and it does not play well with Ubuntu.  Nvidia has always been good to the linux community.  But not lately.

---

### Post by BicyclerBoy on 2011-02-17
@ Optimus..

Do not blame nVidia for your purchase decision. You bought a windows licence.

nVidia never stated that Optinus would have linux support, in fact they have clearly & repeatedly stated no linux support.

It would be hard to find a hardware manufacturer that has supported linux as well as nVidia.
It would be hard to find a more of a near-useless driver mess than ATI..

Optimus is not an ideal arrangement just a complicated work-around.

Some Optimus laptops can work in discrete graphics only mode with Linux e.g. Lenovo Thinkpad T510.
You should have done the research before rewarding the windows only market.

---

### Post by cascade9 on 2011-02-17
> **3rdalbum said:**
> To the OP: If you didn't mind going ATI, then there's a manufacturer called PowerColor which makes recent ATI cards in AGP versions; however these are probably not going to be very cheap. You could try finding a GeForce 7xxx card in AGP which should work fine in Ubuntu, or if you have any spare PCI slots (not PCI-E) you can follow the suggestion from an earlier poster about finding an 8xxx card in PCI.
 
 No, dont even think about it. AMD/ATI is not offereing support for AGP Radeon HD card for linux. 

> **mc4man said:**
> Most likely a 6000 series card will be ok for you, you can use the nvidia-current drivers on 6000 and up. (the 173 drivers can also be used but generally the current ones work better. There is also nouveau drivers which also may suit your needs/hardware just fine.
I wouldn't bother w/ a 5000 series or older at all
(Have 7600 & 7800 that works fine here but probably more than you need to spend

+1. In particular on 'I wouldnt bother with 5000/FX series at all (and also, see below) 

> **mc4man said:**
> From my perspective (desktops and laptops) nvidia has supported linux just fine and likely will continue to do so. Could care less if their drivers are closed source..

They are OK, but not fantastic. 71.xx simply will not work with newer xorg versions. 96.xx is still getting support for current xorg, but they are lagging a bit behind. Canonical doesnt seem at all interested in putting the newer 96.xx drivers into the repos. Plently of people have been caught by that...they see 96.x drivers in synaptic, etc, but they wont work, you have to add a PPA or manually install the drivers. (nice work, canonical.....) 

IMO its just a question of time untill 96.xx rivers wont work with newer xorg versions. 5000/FX seires cards will go the same way sooner or later.

6XXX (or 7XXX) AGP nvidia cards are a better choice then 5000/FX, if only because of the drivers and possible future developments. 

> **BicyclerBoy said:**
> @ Optimus..

Do not blame nVidia for your purchase decision. You bought a windows licence.

nVidia never stated that Optinus would have linux support, in fact they have clearly & repeatedly stated no linux support.

It would be hard to find a hardware manufacturer that has supported linux as well as nVidia.
It would be hard to find a more of a near-useless driver mess than ATI..

Optimus is not an ideal arrangement just a complicated work-around.

Some Optimus laptops can work in discrete graphics only mode with Linux e.g. Lenovo Thinkpad T510.
You should have done the research before rewarding the windows only market.

*snicker* 

Research? Unless you know about optimus (not everybody is a hardware nut) its not obvious what laptop is using optimus, and what laptops arent. Even if you know about optimus its not always obvious....

Seen where the manufacturers list that the nVidia XXXm versions inm the laptop is using optimus? Ohhh, thats right, you wont.....they dont talk about it.

Seen where on the nvidia optimus page they clearly state "no linux support'? Ohh, thats right, they dont- 

[http://www.nvidia.com/object/optimus_technology.html](http://www.nvidia.com/object/optimus_technology.html)

Seen where nvidia states that XXXm could be part of an optimus setup? Ohhh, thats right, they dont. 

So if you find a laptops with optimus, check the website of the manufacturer it (generally) just say 'Nvidia GT435m'. OK, so then you go to the nvidia site, search for GT435m, and look, there are drivers.  Its a VERY easy 'mistake' to make. 

If there is no BIOS switch, then you have to use a hack to disable the nvidia card. IF there is a hack avaible, plenty (I'd go so far as to say 'most') laptops with optimus has no work around. 

I'm not quite as 'anti-nvidia' over this optimus issue as nynoah, btu I'm seriously unimpressed.

---

### Post by BicyclerBoy on 2011-02-17
I agree the Optimus mistake is easily made but..

If I was to spend US1K+ on a laptop I would google linux + laptop_model first. 
That costs US$0.00 & takes about 5 minutes.

The last place to find information, in my country at any rate, is a laptop computer shop.

This thread is way off topic now..

---

### Post by Jon Anderson on 2011-02-17
You have high jacked my thread, I need a nvidia card that is easy to install and cheap(I hope). Im running a VIA/s3g unichrome pro on my board, it freezes and I would like to try vesa mode but dont know how to do it. I would use the via if I could find undated drivers for the card and If I had a clue how to set it up. otherwise I need a card that will set up the easiest possible way and Im on a budget.

---

### Post by jerrrys on 2011-02-17
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+install+vesa&as_qdr=all&sa=Google+Search&lang=en#878](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+install+vesa&as_qdr=all&sa=Google+Search&lang=en#878)

---

### Post by TopgunB on 2011-02-17
From the manual on the Ubuntu web site!!
3.2.2. 3D Nvidia Video Card Driver
No Nvidia Video cards have 3D acceleration enabled automatically with Ubuntu, because the
manufacturer does not release open source drivers. However, it is possible to activate 3D acceleration.
The process depends on which type of video card you have.
1. If you have an older TNT, TNT2, TNT Ultra, GeForce1 or GeForce2 card, install the
  nvidia-glx-legacy and nvidia-settings packages from the Restricted repository (see Chapter 2,
 Adding, Removing and Updating Applications [p. 21]).
2. Alternatively, if you have a newer card, install the nvidia-glx package from the Restricted
  repository (see Chapter 2, Adding, Removing and Updating Applications [p. 21]).
3. To enable the new driver, run the following command in a terminal:
sudo nvidia-glx-config enable
58
Configuring Your System
4.
You may adjust the settings of the new drivers by running the application nvidia-settings (see
Section 1.2, “Start a Program Manually” [p. 49]). If you wish, add a menu entry for this
program (see Section 1.1, “Menu Editing” [p. 49]).
3.2.3. 3D ATI Video Card Driver
Many ATI video cards work well with Ubuntu automatically. To check that 3d acceleration works
with your card, see Section 3.2.1, “Introduction to 3D Video Acceleration” [p. 58
]
. If it does not
work, this procedure should activate it.
1. Install the xorg-driver-fglrx package from the Restricted repository (see Chapter 2, Adding,
  Removing and Updating Applications [p. 21]).
2. You now need to configure the computer to use the new driver so run this command in a
  terminal:
sudo dpkg-reconfigure xserver-xorg
3. When the dialogue appears and asks whether to do automatic detection of your video, pick Yes.
4. When asked to select a driver, pick fglrx.
5. Follow the remaining instructions as appropriate.
6. Restart your machine for changes to take effect.
3.3. Keyboard Layouts
This section deals with adding keyboard layouts to your system, and switching between them

---

### Post by BicyclerBoy on 2011-02-17
There is a "proper" driver for the unichrome graphics ...

Are you running any version of the unichrome driver ??

---

### Post by cascade9 on 2011-02-18
@ BicyclerBoy- google wont always help with optimus. Lots of laptops have the same model number over several different versions. But enough on optimus....

*edit @ TopgunB- I'm pretty sure that those instructions are outdated. Got a link to the original page? 

> **Jon Anderson said:**
> You have high jacked my thread, I need a nvidia card that is easy to install and cheap(I hope). Im running a VIA/s3g unichrome pro on my board, it freezes and I would like to try vesa mode but dont know how to do it. I would use the via if I could find undated drivers for the card and If I had a clue how to set it up. otherwise I need a card that will set up the easiest possible way and Im on a budget.

Hijacked LOL. 

Like I've said in other threads (this is, what, thread number 3 on the same subject?) AGP is obsolete, and pretty much discontinued. So what may be avaible easily in one place is hard to find somewhere else. If you need a hand finding a AGP card in yoru area, posting your location is a good start. 

nVidia 6200 AGP is your easiest, safest choice, should be avaible from some supplier in your area, and will run with the least amount of sodding around.

---

### Post by Jon Anderson on 2011-02-19
> **BicyclerBoy said:**
> There is a "proper" driver for the unichrome graphics ...

Are you running any version of the unichrome driver ??

My video card is VIA/s3g unichrome pro. The drivers that are recommended by Xorg is the 1:0.2.904+svn-0ubuntu1 and by my synaptic package manager, that is what is asked for and it is the one that it uses. I spent a lot of time looking for the drivers for the VIA and the one that is suppose
 to work doesn't. The computer freezes and you have to reboot.

---

### Post by BicyclerBoy on 2011-02-19
I was think of [http://www.openchrome.org/trac/wiki/About](http://www.openchrome.org/trac/wiki/About)

I'm not sure if this is available in any ppa repos.

---

### Post by Jon Anderson on 2011-02-20
> **BicyclerBoy said:**
> I was think of [http://www.openchrome.org/trac/wiki/About](http://www.openchrome.org/trac/wiki/About)

I'm not sure if this is available in any ppa repos.

 I got no ware trying to find a driver for my VIA/s3g unichrome pro. The openchrome drivers were in the Unbutu 8.04 and maybe later ones but somewhere along the way they gave up on openchrome and moved to Xorg drivers and I can tell you they don't work in my Ubuntu 10.10 and I have to assume that the openchrome drivers wont work ether, otherwise why replace them. Also the last update on the openchrome was a year and a half ago. Drivers for the On board via would have been the simplest way.

---

### Post by BicyclerBoy on 2011-02-20
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

has                  xserver-xorg-video-openchrome               1:0.2.904+svn839-0ubuntu0tormod
this is 53 weeks old..

But the openchrome xserver packaqe is missing from the latest xorg-edgers ppa..

---

