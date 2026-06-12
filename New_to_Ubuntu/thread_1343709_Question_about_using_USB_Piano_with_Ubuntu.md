---
title: "Question about using USB Piano with Ubuntu"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by civillianslave on 2009-12-02
Hey all,

After recently getting my Ubuntu 9.10 OS up and running properly(thanks to the kind help of folk here) I have been look to start recording my music again. 

I was wondering if anyone could tell me if any usb piano will work with Ubuntu or will i need a specific model, like my Ubuntu webcam? I am about to buy a USB Mic and Piano and thought i would ask before i spent my money.

Many thanks

---

### Post by Yanno on 2009-12-02
> **civillianslave said:**
> Hey all,

After recently getting my Ubuntu 9.10 OS up and running properly(thanks to the kind help of folk here) I have been look to start recording my music again. 

I was wondering if anyone could tell me if any usb piano will work with Ubuntu or will i need a specific model, like my Ubuntu webcam? I am about to buy a USB Mic and Piano and thought i would ask before i spent my money.

Many thanks
I haven't used a USB piano before.I guess it would need a specific driver.Absolutely the manufacturer of the piano will provide you a driver for Windows but seldom for Linux.

---

### Post by civillianslave on 2009-12-02
so thats a no go on the USB piano then?:( what about  USB microphones?

---

### Post by Mark Phelps on 2009-12-02
In my experience, USB stuff nearly always works.  The problem is most probably going to be that the piano will come with some sort of music composing/playing application -- and THAT won't run in Linux.

So, even if you get the OS to see the device, you won't be able to use the SW that comes with it.

---

### Post by coffeecat on 2009-12-02
Do you mean a USB MIDI keyboard controller, or a digital piano with a USB MIDI output?

Have a look at the [Rosegarden]("http://www.rosegardenmusic.com/") site. If you mean a dumb keyboard, then this page:

[http://www.rosegardenmusic.com/tutorials/en/chapter-2.html](http://www.rosegardenmusic.com/tutorials/en/chapter-2.html)

> 
**2.1.2.2.1 USB Keyboards**

 [Evolution]("http://www.evolution.co.uk/") manufactures  several models that are known to conform to the standard USB MIDI  specification, which are therefore compatible with Linux. Chris Cannam,  one of the core Rosegarden developers, uses an Evolution-2 keyboard,  and reports that it works using the [FONT=courier 10 pitch] snd-usb-audio[/FONT] module, which should probably be loaded  automatically by hotplug. He imagines that most other manufacturers'  wares are similar.

 **2.1.2.2.2 USB MIDI Interfaces **

 The Edriol UM-2 and mAudio MidiSport 2x2 are known to work under  Linux. I have no experience with such things myself, I'm afraid, so I  can only provide second-hand information.
 Pedro Lopez-Cabanillas, a contributing Rosegarden developer, reports  that getting the Edriol UM-2 working is as simple as plugging in the  USB cable and loading the [FONT=courier 10 pitch]snd-usb-audio[/FONT]  module, which should probably be loaded automatically by hotplug.

---

