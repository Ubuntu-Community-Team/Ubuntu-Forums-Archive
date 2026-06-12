---
title: "How Do I disable on board sound"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-03-20
Hi :) I have Realtek A97 on board sound which I have installed the linux drivers for. I bought a SoundBlaster 1.5vx sound card which is working nicely with my WinXP (I dual boot) but I have no sound at all in Ubuntu now. I need to uninstall the on board sound and drivers but have absolutely no clue how. I need to get the Creative sound card working but I can't seem to find linux drivers yet. I'm hoping I have better luck with that than I've had with my internet. Thanks for any replies :)

---

### Post by blackmail on 2010-03-20
I am not quite sure, but there should be settings for this in your BIOS, or just try locating and uninstalling the drivers for your onboadr sound chip.

---

### Post by ThePinkWitch on 2010-03-20
> **blackmail said:**
> I am not quite sure, but there should be settings for this in your BIOS, or just try locating and uninstalling the drivers for your onboadr sound chip.

Thanks for your reply but thats what I'm asking :) how do I locate and uninstall the drivers in Ubuntu? Its a breeze for me in Windows but Ubuntu is becoming a source of meltdowns for me. I've had to lock my axe away as a few times my computer has had call to look nervous since I installed Karmic :/ *Eyes twitching*

---

### Post by linuxman94 on 2010-03-20
The drivers do not need to be uninstalled.  They will just be disabled when Ubuntu notices that the sound card is no longer there.

---

### Post by ThePinkWitch on 2010-03-20
> **linuxman94 said:**
> The drivers do not need to be uninstalled.  They will just be disabled when Ubuntu notices that the sound card is no longer there.

Ok thanks. How do I disable the onboard sound so Ubuntu sees the new soundcard ?

---

### Post by linuxman94 on 2010-03-20
> Ok thanks. How do I disable the onboard sound so Ubuntu sees the new soundcard ? 

You need to go into the BIOS and find the option to disable onboard sound.

---

### Post by blackmail on 2010-03-20
> **linuxman94 said:**
> You need to go into the BIOS and find the option to disable onboard sound.

This was one of my two suggestions :popcorn:

---

### Post by blackmail on 2010-03-20
If you won't manage till later, when i get home from work and take a nap i will look at how to hard-core uninstall the drivers, and force your PC to do what you want

---

### Post by ThePinkWitch on 2010-03-21
Thankyou both very much. I will go into the BIOS and see if I can work it out. Can't find anything on this OS :( Where's the control panel? :D

---

### Post by anewguy on 2010-03-21
Control Panel????  "This OS" ain't Windows!

Dave ;)

BTW - even if it WERE Windows, you still wouldn't need the control panel.  Boot your system, press F1, DEL or whatever you system takes to get to the BIOS setup screen.  Look in there for the ability to disable onboard sound, save it, and let the PC boot.

---

### Post by ThePinkWitch on 2010-03-21
> **anewguy said:**
> Control Panel????  "This OS" ain't Windows!

Dave ;)

BTW - even if it WERE Windows, you still wouldn't need the control panel.  Boot your system, press F1, DEL or whatever you system takes to get to the BIOS setup screen.  Look in there for the ability to disable onboard sound, save it, and let the PC boot.

er...that was a joke about the control panel :) I couldn't find the onboard sound to disable in the BIOS because I realised it was disabled in Windows Device manager. I went into windows and enabled it and it showed up in the BIOS so I could disable it there. THANKS EVERYONE for your help :) The Sound Blaster card is working perfectly now. :D

---

### Post by kcohen1017 on 2010-03-21
I've been down this path many times - once you determine the BIOS of your system, there are numerous web sites that will tell you how to access the BIOS setup.  Usually it's something like press F10 or F12 or Delete when you see the boot splash screen.  It will then tell you that it's entering Setup, and in a few seconds you'll be in the main BIOS setup screen.

Now, you will need to navigate the BIOS settings to find the on-board sound system.  I cannot tell you exactly, but typically it is in the same screen as the on-board LAN and/or video system.  Disable the sound system and save the new setting - while you're in the BIOS anyway, you may as well tweak a few other settings such as how much memory is available to the video system or shutting off unused serial ports.

After you save the new settings and exit the BIOS setup the system will boot up and Ubuntu and Windows will not see the on-board sound system.

I hope this helps.

---

### Post by blackmail on 2010-03-21
In KDE there is actually something ControlPanel like, but that is KDE :D

---

### Post by ThePinkWitch on 2010-03-22
while you're in the BIOS anyway, you may as well tweak a few other settings such as how much memory is available to the video system or shutting off unused serial ports.

Thanks so much. BTW would love info on how to "tweak a few other things: :D. Where do you find that stuff?

---

### Post by ThePinkWitch on 2010-03-22
> **blackmail said:**
> In KDE there is actually something ControlPanel like, but that is KDE :D

Thanks but I'm struggling to work Ubuntu out I don't want to confuse myself any more :P If I can't get sorted with Ubuntu I'm gonna try Mint. If I can't get stuff working with that I'm done. Thanks so much for your help :)

---

