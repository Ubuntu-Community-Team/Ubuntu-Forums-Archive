---
title: "Drivers"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by sncking on 2009-11-04
I have just dual booted my computer to the latest version, and I am looking to find drivers, and instructions on how to install them.  What are the best places to look?

---

### Post by Phil D. on 2009-11-04
Drivers for what'

---

### Post by sncking on 2009-11-04
Opps, sorry.  Toshiba A205-S4587 laptop.

---

### Post by sncking on 2009-11-04
I started looking for the individual pieces of equipment on the computer itself in windows, and found a couple, but I'm not sure how to install the drivers in ubuntu

---

### Post by leorolla on 2009-11-04
Tell us what works, what does not work, and what works so-so.

Most important: internet

---

### Post by aktiwers on 2009-11-04
Ubuntu often finds and installs all drivers for you, when you install it.

Else you can check out System => Administration => Hardware drivers

If something shows up in there, you can click to install it.

Are you having some problems, making you think that your drivers are not installed?

---

### Post by sncking on 2009-11-04
video resolution is way down.  I have a 24in wide screen monitor, and the best i can get is 1024x768 for one.  Not sure about my wireless yet...

---

### Post by sncking on 2009-11-04
Nothing shows up in the drivers window

---

### Post by Dougie187 on 2009-11-04
Well, Ubuntu doesn't have drivers in the same since that windows does. You will most likely be able to find windows drivers for your computer through google, but cannot use those on ubuntu. If you are missing some specific feature, or some hardware is not working your best bet is to make a separate thread with a descriptive title and post about your problem and see if someone can help you.

---

### Post by JPorter on 2009-11-04
Linux doesn't require that you install a raft of drivers for all the different devices in your system, most of them are supported by default.

The graphics settings sounds like a configuration issue, hopefully I can help.  What type of graphics chip is in that laptop?

---

### Post by JPorter on 2009-11-04
I just looked it up, spec sheet was here:  [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A205-S4587.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A205-S4587.pdf)

It's an Intel GMA 950 (945GM Chipset), with a 1280x800 laptop display.  Use that first, and get everything working the way it should prior to attaching any external devices.  The Intel graphics with the laptop display should be supported out of the box (zero configuration) in Ubuntu 9.10.  In an odd case you may need to manually set the resolution in the System -> Preferences -> Display dialog.

If nothing seems to be working, we can try setting it manually in the config file (xorg.conf), but that shouldn't be necessary if things are running otherwise normally.

---

### Post by sncking on 2009-11-04
intel 945 express chipset

---

### Post by sncking on 2009-11-04
I went into the display dialog.  the only setting available is the 1024x768.  there is no other options

---

### Post by JPorter on 2009-11-04
> **sncking said:**
> I went into the display dialog.  the only setting available is the 1024x768.  there is no other options

I understand. 

First, disconnect the external monitor entirely, and use the screen built into the laptop.  What resolution does it give you?

---

### Post by mal1958 on 2009-11-04
Not sure about 9.10 but with my version of 9.04 I had to download video drivers because the Chipset was an Nvidia chipset and that takes propriatary drivers that don't ship in the CD or Image...


(edit):  Oh, and sncking, Welcome to the world of Ubuntu.

---

### Post by sncking on 2009-11-04
OK, found part of the problem.  my monitors were mirrored.  did not catch that at first (probably thinking like the windows puke that i have been my whole life).  Now that i can separate them, when I choose the resolution i want on my external (1920x1080), the computer locks up with both screens black and unresponsive...

---

### Post by JPorter on 2009-11-04
> **sncking said:**
> OK, found part of the problem.  my monitors were mirrored.  did not catch that at first (probably thinking like the windows puke that i have been my whole life).  Now that i can separate them, when I choose the resolution i want on my external (1920x1080), the computer locks up with both screens black and unresponsive...

Get the single primary monitor working properly first.  Then attach the external monitor and configure it, then save the configuration (it will prompt you) and reboot.  Only then will it set up and use the second monitor properly.

---

### Post by sncking on 2009-11-04
OK, I did remove the external, got the laptop monitor working, and rebooted.  as soon as i plug the externa monitor in and click on detect, both screens black out and the computer becomes unresponsive.  had to reboot again with the single monitor...

---

### Post by sncking on 2009-11-04
I appreciate the help you were giving me, and was just wondering if you had seen my last post:

OK, I did remove the external, got the laptop monitor working, and rebooted. as soon as i plug the externa monitor in and click on detect, both screens black out and the computer becomes unresponsive. had to reboot again with the single monitor...

---

### Post by JPorter on 2009-11-04
Turn off Compiz first.  

System -> Preferences -> Appearance -> Visual Effects -> None.

---

