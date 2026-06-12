---
title: "problems with fx5200 screen resolution"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by huggies15 on 2009-04-25
Hi. I'm having a very strange problem, and don't know what to do.
I just installed jaunty on an old pc for use in my room. Set it all up how I wanted it with all the programs I'd need. I then unplugged it from downstairs, moved it to a different room (no internet there) and turned it on. The resolution dropped to 640x4?? And it now looks aweful. I'm using exactly the same hardware (monitor and all) so I thought nothing should have changed. The only difference is I have no internet connection now.

The hardware is an acer 1916w monitor (1440x900), nvidia fx5200, and old sempron processor. I have the nvidia drivers installed and like I said, they were working, but not now.

Does anyone know what I should try to do to fix this. The machine is currently inoperable!

Sorry if this message is garbled, have had to write it on my phone :(

Cheers in advance,
Steve

Ps if it makes any difference nvidia is now saying I have 2 monitors, one being a tv... Didn't know what was going on with the either

---

### Post by blackened on 2009-04-25
Have you tried booting into recovery mode and running xfix?

---

### Post by huggies15 on 2009-04-25
I did xfix in recovery mode, it starts in non nvidia mode, and I get a max resolution of 800x600. Then if I open the nvidia settings it says something about running nvidiasettings as root, and that just leads me back to the 640x4?? Resolution. Also if I try changing the resolution before activating the nidia driver, the 'display' tab says monitor:unknown, where as when connected to the net it came up as acer1916w.
Cheers

---

### Post by blackened on 2009-04-25
You may also try deleting ~/.config/monitors.xml.

If I were a betting man, which luckily I am, I would say that this is just incorrect monitor detection. Delete the monitors.xml file, then run xfix again. Make sure you run nvidia-settings as root (*sudo nvidia-settings* from the terminal).

---

### Post by inobe on 2009-04-25
tell us what driver is installed.

also go into synaptic and search **nvidia**

tell us everything that's installed related to the activated nvidia driver.

---

### Post by Happy_Man on 2009-04-25
Hey, I've got the same graphics card as you do (Nvidia Geforce FX 5200, right?). 

I had no problems getting Jaunty to work OOTB on my comp, so it most likely isn't a driver issue. More likely something got corrupted when you unplugged it somehow (Maybe a neutrino hit it?) and now your computer's dropping you to a safe resolution because it doesn't know what to do. 

Do what blackened said up there about deleting stuff, and then report back if it works. If it doesn't, well...

---

### Post by inobe on 2009-04-25
happy-man

could you post what's installed in synaptic "for your card" so that we can use it as reference just to assure huggies15 has all the needed components :)

---

### Post by huggies15 on 2009-04-25
> **inobe said:**
> tell us what driver is installed.

also go into synaptic and search **nvidia**

tell us everything that's installed related to the activated nvidia driver.

Ok, I deleted monitor.xml, redid xfix, loaded nvidia settings, and no change, still not detecting monitor properly, and can't get res above 640x4??  
In synaptic it says I have:
Nvidia-173-kernal-source
Nvidia-173-modaliases
Nvidia-180-modaliases
Nvidia-71-modaliases
Nvidia-96-modaliases
Nvidia-common
Nvidia-glx-173
Nvidia-settings
Xserver-xorg-video-nv

All installed. I installed the driver thru the restricted thing in system->admin, it said it was driver 173(recommended)

Hope this helps

Steve

---

### Post by inobe on 2009-04-25
i need happy-mans list of components as requested :)


certainly looks like your missing at least three components.

but uncertain

---

### Post by inobe on 2009-04-25
at this point i looked in synaptic, it seems you have all the requirements.


all that i can think if is try the basics.


first disabling the driver in "hardware drivers" and restarting, once your back to the desktop try activating the driver once more.


not: we will take this one step at a time, have patience :)

---

### Post by huggies15 on 2009-04-26
I seem to have fixed it.
I took it downstairs again, to see if the internet was making a difference, and noticed that the cable I was using to hook the pc to the monitor had 1 pin missing in each end. I swapped this out for a new one, and it works fine. Everything detected and perfect. I tried the original cable on a windows pc and it works fine on it, so it must just be sonme qwerk of linux that u need this pin that u don't in 'dows. Anyway, thank u for ur patience and help, it was a weird fault :)

Steve

Ps moral of the story is check the easiest things first!

---

### Post by blackened on 2009-04-26
> **huggies15 said:**
> Ps moral of the story is check the easiest things first!

The BOFH would be proud... right before he made you electrocute yourself.

---

### Post by Happy_Man on 2009-04-26
> **huggies15 said:**
> I seem to have fixed it.
I took it downstairs again, to see if the internet was making a difference, and noticed that the cable I was using to hook the pc to the monitor had 1 pin missing in each end. I swapped this out for a new one, and it works fine. Everything detected and perfect. I tried the original cable on a windows pc and it works fine on it, so it must just be sonme qwerk of linux that u need this pin that u don't in 'dows. Anyway, thank u for ur patience and help, it was a weird fault :)

Steve

Ps moral of the story is check the easiest things first!
Hahahaha, glad to see that you've fixed it and it's good now.

---

### Post by inobe on 2009-04-26
wow

that will be noted

---

