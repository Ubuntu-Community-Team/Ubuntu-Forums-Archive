---
title: "need video card advice for ubuntu 10.04 64bit"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by morgan365 on 2010-10-09
Hello i am very close to being off of microsoft i have figured out most of what i need but i want to run dual monitors and need advice on a good video card that supports dual monitors but also works flawlessly with my new ubuntu os.Also general help on how to set up ubuntu to run the dual monitor not as mirrors but i want one for basically 24/7 video and one for web browsing i am useing a custom cumputer with an asus m3a78pro motherboard with a amd 2+ dual core 5400+ 2.8ghz unlocked processor with 4 gigs ram and a seagate 640gig drive the onboard video on this motherboard works great but i only have one monitor output thanks

---

### Post by roccivic on 2010-10-09
Personally, in the past I have always had all sorts of trouble with proprietary drivers for video cards. I now manage several linux workstations and all of these computers have been upgraded with some of the latest AMD processors and ATI video cards that work with the _opensource drivers_. This means that after installing ubuntu there is no need to do anything to the video cards - they work straight away. I had the best luck with the HD4*** series. This series is over two years old now, but the performance is still quite good. I would recommend checking compatibility for the radeon HD chipsets before buying (models that start with "X" probably won't work as I think support for these was dropped by ATI): [http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)

Hope this helps.

Rouslan

---

### Post by Irony on 2010-10-09
I notice that the link at [http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README) says that HD4350 is supported however I have that card and it doesn't work with Blender or Googleearth. It also scrolls slow and cuts out to a blank screen after about an hour.

Works well with latest the proprietary driver, though tends to leak memory with xorg, in fact with gtk2 installed it leaks massively.

---

### Post by cascade9 on 2010-10-10
> **morgan365 said:**
> Also general help on how to set up ubuntu to run the dual monitor not as mirrors but i want one for basically 24/7 video and one for web browsing

By 'video' do you mean watching video media (avis, etc)? 

If yes, go for nvidia, everytime. VDPAU (nVidia hardware video decoding) is great, its a lot better than the ATI version. 

A GT220 nVidia card is what I would get. ;)

---

### Post by EnGorDiaz on 2010-10-10
gigabyte gts 250

---

### Post by cascade9 on 2010-10-10
> **EnGorDiaz said:**
> gigabyte gts 250

If morgan365 isnt a gamer, then a GTS250 is pointless. If morgan365 is a gamer, there are better cards for gaming in the same price range.

---

