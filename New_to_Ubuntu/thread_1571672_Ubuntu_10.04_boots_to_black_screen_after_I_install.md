---
title: "Ubuntu 10.04 boots to black screen after I install graphics driver"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by cardinal4 on 2010-09-09
Hi guys, I'm kind of a newcomer to Linux, though I've tried to use LinuxMint before.

I installed Ubuntu 10.04 as dual boot via Wubi. Everything worked fine on first use. Then I realised I couldn't change my screen resolution (monitor options only displayed 640x480), so I decided to run the Hardware Driver thingy and download drivers for my graphics card.

I downloaded the FGLRX driver indicated, and proceeded to restart my computer as indicated.

On restart, after the Grub menu, my monitor turned black. Nothing loaded! Normally I'll see the Ubuntu loading indicator in seconds.

But if I press the power button, amazingly, the Ubuntu loading indicator appears, and my computer powers off. :confused:

Is the graphics driver damaged or not suitable? How do I get the right one?

My computer specs:
ATI Mobility Radeon HD 5650 (switchable graphics)
Intel graphics media accelerator
AMD64 Ubuntu 10.04

Thanks in advance.

PS: I rmbed in LinuxMint the default recommended fglrx driver didn't work too, but someone recommended some cryptic Terminal commands that fixed it. gah shd have copied it down somewhere. :(

---

### Post by MacinViLLe on 2010-09-09
Are you having the same problem with the other OS? Try to remove the graphics card and use the onboard one, just to check if the problem is really with the card or has something to do with your Ubuntu installation.

Also, try to reinstall the Ubuntu without Wubi. ;)

---

### Post by cardinal4 on 2010-09-10
> Try to remove the  graphics card and use the onboard one, just to check if the problem is  really with the card or has something to do with your Ubuntu  installation.Ubuntu ran okay on the graphics card, there were no issues. It's just that upon installing the driver for the card via Hardware Driver, that Ubuntu failed to boot. Plus, it already is the onboard one.:)

> Also, try to reinstall the Ubuntu without Wubi.I need to get more used to Ubuntu first, cannot rush things. ;)

[COLOR=Plum]Without a graphics driver, my desktop is stuck at 800x600... really small. 

I tried downloading the graphics driver from ATI itself, the Catalyst 10.8 for Linux x86_64. But on installation Ubuntu says I don't have vcdk installed...

How?[/COLOR]

Erm.. haha. I just realised I could change the resolution on the Monitors application. Because I was using dual display (laptop and external monitor), the resolution they gave me was 800x600 - the only common compatible resolution for both display.
By disabling *"same image in all monitors"* I could change the resolution to 1280x1024. woops. My mistake haha.. :p

Erm, so why did Ubuntu prompt me to install the "proprietary hardware drivers" then? It seems I didn't need any graphic drivers to begin with... :confused:

---

