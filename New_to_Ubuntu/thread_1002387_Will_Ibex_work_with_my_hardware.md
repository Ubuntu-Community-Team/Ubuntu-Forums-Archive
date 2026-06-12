---
title: "Will Ibex work with my hardware?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Adamantus on 2008-12-04
I posted a similar question a little while back because I was having trouble finding a linux distro that worked with my computer. I tried a lot and the only one I could get to work was Ubuntu 8.04, which I then upgraded to 8.10. It didn't work too well though (couldn't get the wireless to work, bad video, etc.), so I decided to go back to Vista and try out Ubuntu again later. Now that I'm going to have some time in the coming weeks to work with my comp, I wanted to make sure it'll work.

I have a HP Pavillion dv5 with an ATI Radeon HD 3200, and Atheros 242 wireless card, and an AMD 64 Turion processor.

I've discovered that it is nearly impossible to get Fedora 10 to work with the Radeon 3200. I know I can get Ubuntu working with my graphics card, but will playback be shoddy? Also, I really liked this program I saw on youtube called linux beryl. Would it work or would I have problems with it? Would I have other graphical problems I couldn't get rid of?

Also, last time I installed Ubuntu, my computer got a lot louder and the battery life was severely reduces. Was that most likely to a bad install? I used unetbootin, since it was the only way I could get Ubuntu to install. Is there a better alternative to the normal install disk?

Thanks for any help.

---

### Post by earthpigg on 2008-12-04
ram?

(usually the limiting factor)

---

### Post by Adamantus on 2008-12-04
Sorry, I have 4 gigs and a 2.1 Ghz processor.

I know my computer is fast enough. It's mostly the hardware compatibility. And if it makes a difference, I would be installing the x86_64 version.

---

### Post by Tatty on 2008-12-04
Beryl no longer exists, it merged with compiz to form Compiz Fusion about a year and a half ago.

Compiz Fusion is installed by default (although switched off) in ubuntu.  To enable the basics go to System->Preferences->Appearance->Visual Effects, then select what you want.  To do more advanced things you will need to install a couple more apps, but all the information for that is located around these forums.

I used to run Beryl (back in the day) on a radeon 7xxx card (cant remember the exact model now), so I imagine your card will be able to run Compiz Fusion to some extent.  It mainly depends on wether you can get the propriety ATI drivers running on your machine, but thats something you wont know till you have a go.  It should work though.

---

### Post by aktiwers on 2008-12-04
I think it will work just great.
The only thing I think you need to apply this to get your wireless to work.
[http://ubuntuforums.org/showthread.php?p=6086976](http://ubuntuforums.org/showthread.php?p=6086976)

But why not try out the liveCD and see how everything goes?

---

### Post by Adamantus on 2008-12-05
Okay, I just tested out 8.10 using Wubi and it worked somewhat fine. Some problems:

-The battery wasn't charging. It stayed at 47.7% for at least 10 minutes, even though I had it plugged in. 

-I couldn't install the flgrx driver for my graphics card because I couldn't connect to the internet. For some weird reason, it wasn't even recognizing that I had an ethernet cable plugged in, yet Windows seems to recognize it perfectly. 

I'm sure that the internet problem is easily fixable, but the battery problem is a little more distressing since this same thing happened the last time I installed Ubuntu.

Edit: I just restarted with the ethernet cable plugged in and I can connect. But I found couple of problems:

-When I shut down or restart, the top of the screen flashes a lot of colors for a split second and then there's a semi-loud pop that comes form inside my computer. Is this something that's going to hurt my computer?

---

### Post by Adamantus on 2008-12-05
Okay, after having my computer plugged in for the night with it turned off, the battery is fully charged. When I had the computer plugged in with Vista running, it also seemed to be sort of stuck at the same charge, so maybe it's just that the computer charges kind of slowly.

The last time I turned it off, the pop didn't happen, but there still seems to be some colors flashing at the top of my screen when I shut down. What's the cause of this, and do I even need to fix it? Edit: Scratch that, I just restarted and it popped again. I'm sort of scared to start Ubuntu again. I feel like it's going to screw up my hardware.

Other than that, Ubuntu seems to be working fine, although a little slowly (but I think that is because it's just the demo and I'm not even sure if it is the 64 bit version - it says I only have 3.6 gigs of ram, so I'm guessing it is only the 32 bit).

---

### Post by Martje_001 on 2008-12-05
> **Adamantus said:**
> Other than that, Ubuntu seems to be working fine, although a little slowly (but I think that is because it's just the demo and I'm not even sure if it is the 64 bit version - it says I only have 3.6 gigs of ram, so I'm guessing it is only the 32 bit).
No, that's okay. The onboard audio/videocard may use some (same situation here, and I have 64-bit and 4GB RAM).

---

### Post by philinux on 2008-12-05
Flashing colours usualy indicate it's running with the default driver and not the one that you need for your specific card.

What give in system>admin>hardware drivers. Anything offered.

---

### Post by aktiwers on 2008-12-06
And it will always run slower off the livecd. A real install will be faster.

---

### Post by Adamantus on 2008-12-06
Is the popping when it shuts down a problem?

---

### Post by Adamantus on 2008-12-06
bump

---

### Post by aktiwers on 2008-12-07
Popping? Is the screen blinking or?
I wouldn't say that was a problem ;)

---

