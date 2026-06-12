---
title: "No Hardware Drivers!"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Aen2lt on 2009-06-04
anyone know why when i go into my hardware drivers it says "No proprietary drivers are in use on this system"

---

### Post by furialis on 2009-06-04
Ubuntu does not come with proprietary software installed. Go to System>Administration>Hardware Drivers to install the restricted drivers.

---

### Post by Aen2lt on 2009-06-04
when i do that... its blank

---

### Post by UbuntuNerd on 2009-06-04
right click on an empty space of your desktop scroll to the bottom and click on (Change Desktop Background)
when the menu opens click on visual effects and try selecting normal or extra to see if you can activate the effects.

---

### Post by Sef on 2009-06-04
Unless you want to run 3D, there is not much of a need for proprietary drivers.

---

### Post by Aen2lt on 2009-06-04
yes i am able to switch  between normal and extra and i would like to run 3D to do some minor gameplay

---

### Post by oedha on 2009-06-05
> **Aen2lt said:**
> anyone know why when i go into my hardware drivers it says "No proprietary drivers are in use on this system"

CMIIW....
that's because all of your HW is generically support in your installation

for example....if you use ATI...then this ATI will be in that proprietary list

regards;
~E~

---

### Post by Aen2lt on 2009-06-05
right, so how do i enable 3D drivers if there is nothing on the list

---

### Post by hovzio on 2009-06-05
Seems like your not using an nvidia card or so, these will use proprietary drivers. An integrated intel chip needs no proprietary drivers. End of story, if all works fine be happy not to have a "tainted kernel". ;)

---

### Post by UbuntuNerd on 2009-06-05
> **Aen2lt said:**
> yes i am able to switch  between normal and extra and i would like to run 3D to do some minor gameplay

thats where I was getting at I have a machine that doesn't need proprietary drivers and Im able to run Compiz, desktop effects and so on. you should be good to go

---

### Post by 3rdalbum on 2009-06-05
> **Aen2lt said:**
> yes i am able to switch  between normal and extra and i would like to run 3D to do some minor gameplay

If you can run Compiz, then congratulations: You have 3D acceleration.

I'm guessing that you have Intel graphics. They use open-source drivers that work out-of-the-box.

---

### Post by Peter6218 on 2009-06-09
> **Aen2lt said:**
> when i do that... its blank

Yeah I get the same thing running an Nvidia card. Jaunty does not do anything where earlier distro's did. Would like to enable the proper driver but so far no luck.

---

### Post by LowSky on 2009-06-09
> **Peter6218 said:**
> Yeah I get the same thing running an Nvidia card. Jaunty does not do anything where earlier distro's did. Would like to enable the proper driver but so far no luck.

that should be the case, could you open a temrnial and run

```
lspci
```

the l is a lower case L, for some reaosn that trips up many people

---

### Post by Peter6218 on 2009-06-09
> **LowSky said:**
> that should be the case, could you open a temrnial and run

```
lspci
```

the l is a lower case L, for some reaosn that trips up many people

Yep sees the card. Can't do anything with the desktop though. Won't go to Normal or Extra!!

---

### Post by kunks112 on 2009-06-10
Im running an NVIDIA card, and when I look inside my Hardware Drivers, it blank.

I cannot manually install the driver because I have tried 5 times and have had to re-install Ubuntu 4 times due to blank screens and missing or unwritable xconfig.conf files.

can someone tell me how to get my drivers listed on the hardware drivers menu so I can install my drivers from there.

thanks

edit: Using Ubuntu 8.04
card NVIDIA 9600 GT

---

### Post by Mortus Pryde on 2009-06-10
> **kunks112 said:**
> Im running an NVIDIA card, and when I look inside my Hardware Drivers, it blank.

I cannot manually install the driver because I have tried 5 times and have had to re-install Ubuntu 4 times due to blank screens and missing or unwritable xconfig.conf files.

can someone tell me how to get my drivers listed on the hardware drivers menu so I can install my drivers from there.

thanks

edit: Using Ubuntu 8.04
card NVIDIA 9600 GT

What I have found is that generally the Restricted Drivers installer will show there are no proprietary drivers for your hardware if there is infact no proprietary drivers compatable for your hardware in the repository. This means that either your hardware device in question is old and no longer has a compatable prorietary driver for it, and or the proprietary driver for your hardware is not compatable with that version of Ubuntu.

In this case trying to manually install such drivers either from Synaptic or downloading and compiling them from the vender website could cause MAJOR graphical issues.

---

### Post by kunks112 on 2009-06-10
As per reference to this thread
[http://ubuntuforums.org/showthread.php?t=1139143]("http://ubuntuforums.org/showthread.php?t=1139143")


Which has the same video card I have and running the same Ubuntu, there are such drivers.

My vid card is not old, however its not new either, and its a fairly good card.

I just want to be able to use both my monitors, and I need the driver to do that.

Thanks for a reply though

---

### Post by Bixler Zavala on 2009-07-29
I am having simillar problems. I can't get my TV Out to work!

---

