---
title: "wide screen - widens everything like 15%(( NEED DRIVERS?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Ubunser on 2009-12-02
My notebook has wider than usual screen, so when I look at some photo of a girl they're all fat( Doesn't it suck, guys?

---

### Post by coffeecat on 2009-12-02
OK - now you've told us about the photo, tell us about the notebook: make/model, graphics card, screen size/resolution, and which version of Ubuntu you're using.

Come on now! Eyes off the picture! Pay attention! :wink:

---

### Post by Ubunser on 2009-12-03
Samsung R518, Jaunty Jackalope 9.04, screen resolution 1024x768

lshw said about graphic card I guess:

*-display UNCLAIMED
                description: VGA compatible controller
                product: M96 [Mobility Radeon HD 4650]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
:P

---

### Post by coffeecat on 2009-12-03
Well - here's your problem:

> **Ubunser said:**
> My notebook has wider than usual screen

A quick google shows that you screen is a 15.6" 1366x768 one, which is by no means wider than usual. That's a typical 16x9 screen. You'd have difficulty getting anything else new these day.

Anyway...

> **Ubunser said:**
>  screen resolution 1024x768

I presume you mean that the display driver is stuck at 1024x768 rather than the screen being 1024x768. That's an old 4x3 display resolution. No wonder everything (and everyone) looks fat.

You've got a Mobility Radeon card using the (presumably) open-source radeon driver. That driver is perfectly capable of displaying in 16x9 - or at least it is in Karmic. I don't know about Jaunty/9.04.

Three suggestions:

1 - Go to System > Preferences > Display. Can you change the resolution?

2 - Make sure you're connected to the internet and recently updated. Go to System > Administration > Hardware Drivers. Is that prompting you with the fglrx proprietary driver? If so, try installing it.

3 - Download the Karmic desktop CD and run it live. Do you get slim-looking people in your pictures? If so, consider replacing Jaunty with Karmic. The reason I suggest this is that I'm running Karmic on my 17" widescreen laptop with a Mobility Radeon HD4200 chipset, and it autodetects the correct resolution without problem.

---

### Post by Ubunser on 2009-12-03
I finally got normal looking, with your help, thank you! The driver FGLRX installation worked fine, making it possible to change the resolution, which I couldn't do before. Great! Thank you!

---

