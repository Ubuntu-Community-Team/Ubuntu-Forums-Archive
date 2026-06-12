---
title: "Myth TV/ TV tuners"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by impatientboi on 2009-10-21
I have heard lots of good things about Myth TV. I've installed the program, but i want to know about hardware
has anybody had an experience using tv tuners with ubuntu?

I am a little unsure about the technical aspects. i know under windows usb devices are detected automatically. When I set up ubuntu all devices on my netbook were detected and drivers installed automatically (I'm guessing, all i know is everything just worked;-))

Secondly I am running an asus 1000h which has 1.6g processor overclocked to 1.8
and 2g of ram. I have no problems running xvid videos but occcaisonally some of the files i've purchased from itunes (sorry, unsure of the format) start to splutter. I assume this has to do with the processing power required and the atom not being up to scratch.

Should i anticipate any problems running myth tv? because i will be recording (more so than timeshifting) should I expect the computer to stuggle. I would hope to be recording tv streams to xvid.?

Any thoughts or help appreciated.

---

### Post by lovinglinux on 2009-10-21
> **impatientboi said:**
> I have heard lots of good things about Myth TV.

Yes, MythTV is awesome and a very powerful application, but sometimes it can be overwhelming in regard to setup/configuration and resources requirements.

If you are not going to use a central server backend and stream videos or live TV to other machines, then perhaps MythTV is an overkill for you.

> **impatientboi said:**
> I've installed the program, but i want to know about hardware has anybody had an experience using tv tuners with ubuntu?

I am a little unsure about the technical aspects. i know under windows usb devices are detected automatically. When I set up ubuntu all devices on my netbook were detected and drivers installed automatically (I'm guessing, all i know is everything just worked;-))


I don't have any experience with USB TV turners, but I own an analog PCI card. Unfortunately, it doesn't work out-of-the-box. I had to [set it up](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2) to properly loaded when booting.

Try installing [TVTime](apt:tvtime) or [Kaffeine](apt:kaffeine) and check if you can tune your TV properly before digging into MythTV configuration.

> **impatientboi said:**
> Secondly I am running an asus 1000h which has 1.6g processor overclocked to 1.8 and 2g of ram. I have no problems running xvid videos but occcaisonally some of the files i've purchased from itunes (sorry, unsure of the format) start to splutter. I assume this has to do with the processing power required and the atom not being up to scratch.

Should i anticipate any problems running myth tv? because i will be recording (more so than timeshifting) should I expect the computer to stuggle. I would hope to be recording tv streams to xvid.?

I'm not sure, but I think your machine will struggle. Nevertheless, modern TV cards has their own hardware mpeg encoder, so they do much of the processing needed to record TV. 

If you just need to record TV shows, then perhaps you would have a better experience with a simpler application. You could use mencoder or trancode to record TV from command-line or create scripts to do it semi-automatically. Take a look at the [Tutorial in setting up tvtime to record shows or video camera input](http://ubuntuforums.org/showthread.php?t=921233). 

Also check [TVFox](http://tvfox.bplaced.net/) and [FoxMediaCenter](http://fmc.isgreat.org). I'm the developer of the last one, which is a lightweight media center extension for Firefox.

Please notice that I'm not trying to convince you to ditch MythTV and use my own software. I'm not even sure it will work with your TV card. Anyway, I'm just giving you some options, since you probably never heard of those alternatives. If you can run MythTV properly on your machine, then go for it. MythTV is the most powerful media center out there. Also take a look at [Moovida](http://www.moovida.com/), [XBMC](http://xbmc.org/) and [Freevo](http://freevo.sourceforge.net/).

---

