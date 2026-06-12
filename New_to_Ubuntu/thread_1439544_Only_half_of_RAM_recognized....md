---
title: "Only half of RAM recognized..."
date: 2010-03-26
forum: New to Ubuntu
---

### Post by arashiko28 on 2010-03-26
My family computer suffered some sort of mishap and doesn't boot anymore, just turn on the fans and the power led, for the rest somethings work, others I don't know. So I took a very old PC I still had and swapped parts from one and another to make it work again, I could take out the HD and DVD burner.

This old PC seems to only recognize half of RAM that actually has, even less. I placed a 512MB and a 256MB memories and only get 243MB of RAM on system monitor. I installed Xubuntu as once had it but even xubuntu seems a bit clumsy on this specs. Is there a way to fix this without buying a new PC? Even though I will eventually, now it's not the best time to do it.

> PC specs
Processor Celeron (coppermine)
243MB RAM


---

### Post by Slonda828 on 2010-03-26
What are the specs and manufacturers of the RAM you installed? When did you add the RAM, and if you added it recently, how much did it come with originally, and did the system display the correct RAM count before you added the new RAM?

Incorrect RAM count is typically, at least in my job, hardware based and not OS based. Maybe one is inserted wrong, maybe the two are designed for different bus speeds, etc.

---

### Post by undecim on 2010-03-26
My guess would be that 

1: The old motherboard doesn't support more than 256 MB ram, or doesn't support the 512 stick (although usually this results in a non-bootable system, so make of it what you will)

2: Part of the 256 MB is allocated to your video card.

Also, for old computers, Xubuntu isn't really a good option (it's actually heavier than Ubuntu) Try Lubuntu instead.

Although you don't have to reinstall. Just open a terminal and run:
```
sudo aptitude install lubuntu-desktop
```

And you will be able to select LXDE as your desktop environment from your login screen. LXDE is much lighter than than the XFCE desktop that comes with Xubuntu.

---

### Post by NightwishFan on 2010-03-26
That Xubuntu is heavier is subjective. Linux uses RAM in strange ways. I would think overall it would have a lighter disk footprint but fairly even otherwise.

As for the RAM issue I would check if the BIOS sees it if possible, as was said.

---

### Post by arashiko28 on 2010-03-26
The bios sees the RAM just as Xubuntu does, these are old RAM, I changed them when I first got that computer about 4-5 years ago. Once got to read the 512MB, I do remember that because before it was mine, was from a cousin and I upgraded it for her, changing 128MB to 512MB along with the upgrade from win 2000 to XP. It has about 2 years I didn't used it, since I got my laptop I don't remember anymore if it was like that, I do remember Xubuntu ran very well including I could run beryl with it's 8MB video ram... there's the post somewhere where I show the screenshot of the cube :p

---

### Post by arashiko28 on 2010-03-26
> **undecim said:**
> My guess would be that 

1: The old motherboard doesn't support more than 256 MB ram, or doesn't support the 512 stick (although usually this results in a non-bootable system, so make of it what you will)

2: Part of the 256 MB is allocated to your video card.

Also, for old computers, Xubuntu isn't really a good option (it's actually heavier than Ubuntu) Try Lubuntu instead.

Although you don't have to reinstall. Just open a terminal and run:
```
sudo aptitude install lubuntu-desktop
```

And you will be able to select LXDE as your desktop environment from your login screen. LXDE is much lighter than than the XFCE desktop that comes with Xubuntu.


Can you enlight me about Lubuntu? I have never heard about it before, I'm jumping into wiki search right now.

---

### Post by Slonda828 on 2010-03-26
> **arashiko28 said:**
> The bios sees the RAM just as Xubuntu does, these are old RAM, I changed them when I first got that computer about 4-5 years ago. Once got to read the 512MB, I do remember that because before it was mine, was from a cousin and I upgraded it for her, changing 128MB to 512MB along with the upgrade from win 2000 to XP. It has about 2 years I didn't used it, since I got my laptop I don't remember anymore if it was like that, I do remember Xubuntu ran very well including I could run beryl with it's 8MB video ram... there's the post somewhere where I show the screenshot of the cube :p

Well, I am just shooting from the hip here without seeing your motherboard, but I would pull each module one by one until I found the one that is affecting your RAM count. Then I would swap that suspected bad module with another slot (if you have another slot of similar size and such), and see if that changes anything. It could be a bad slot. If you change slots and the RAM count still reads bad (by this time you will have reseated the DIMMs several times by now), I would gather (from the hip, again) that you may have a bad RAM module. This is usually how troubleshooting plays out on servers anyway. I hope this was remotely helpful.

---

### Post by c00lwaterz on 2010-03-26
what is the difference between ubuntu and xubuntu? what audience is intended for xubuntu?

thanks

---

### Post by NightwishFan on 2010-03-26
Xubuntu is a more conservative desktop environment designed for slightly older machines or efficiency on newer ones. You can gain a much lighter desktop but installing using the alternate CD using only a command line, and manually installing a basic DE such as xfce4 packages or lxde.

---

### Post by jfmanamtr on 2010-03-26
The difference is in the desktop environment used. By default, Ubuntu installs Gnome 2.x & Xubuntu installs XFCE 4.x. Lubuntu is a newer flavor that seems to revolve around LXDE. I think that Xubuntu & Lubuntu are entended for older hardware that may not be able to run Gnome.
 
~John

---

### Post by arashiko28 on 2010-03-26
> **Slonda828 said:**
> Well, I am just shooting from the hip here without seeing your motherboard, but I would pull each module one by one until I found the one that is affecting your RAM count. Then I would swap that suspected bad module with another slot (if you have another slot of similar size and such), and see if that changes anything. It could be a bad slot. If you change slots and the RAM count still reads bad (by this time you will have reseated the DIMMs several times by now), I would gather (from the hip, again) that you may have a bad RAM module. This is usually how troubleshooting plays out on servers anyway. I hope this was remotely helpful.

Did that yesterday, had to toss 2 cards, when alone, just made one long beep and nothing further. Changed the cards from slots same results, these 2, were 256MB read 130MB and 512 another 256Mb, I thought at least would get some 380MB or so, but no...

---

### Post by NightwishFan on 2010-03-26
You can run memtest off the live CD or when installed. Hold "shift" to get a grub menu. It has no "end" so let it run a few passes until you are satisfied.

---

### Post by undecim on 2010-03-26
> **arashiko28 said:**
> Can you enlight me about Lubuntu? I have never heard about it before, I'm jumping into wiki search right now.
> **c00lwaterz said:**
> what is the difference between ubuntu and xubuntu? what audience is intended for xubuntu?

thanks

All the different flavors of Ubuntu are just the same operating system with different packages installed. Think of them as the same person, but in difference clothes.

The most main difference in installed packages is the desktop environment which is the visual interface of the computer. Any other changes are based on this one change. For example, Kubuntu, which comes with the KDE Desktop Environment, comes with k3b for burning discs instead of the brasero that Ubuntu comes with, because k3b works better with KDE.

Ubuntu comes with GNOME, which is an okay default. It's fairly simple and not too heavy.

Xubuntu comes with XFCE, which is similar to GNOME. Wether or not it's lighter or heavier is debatable.

Kubuntu comes with KDE, which is designed to be user-friendly and visually appealing. It is very heavy though. If you have a computer that is "designed for Windows Vista" it should run KDE fine.

Lubuntu comes with LXDE, which is designed to be as lightweight as possible while still being somewhat user-friendly. It's not as pretty as GNOME or XFCE, but it will run circles around them. If you have the graphics card, it's possible to run Compiz and Emerald to get some eye candy.

---

### Post by arashiko28 on 2010-03-26
Will I be able to choose which one to use freely or should I uninstall XFCE, if so, how do I do it?

---

### Post by natravis on 2010-03-26
> **arashiko28 said:**
> Will I be able to choose which one to use freely or should I uninstall XFCE, if so, how do I do it?

For your original issue: I imagine the RAM was bad, as others have pointed out and you determined from the "only have one plugged in and try" test. The remaining RAM can be tested by using Memtest (which is included on the LiveCD), which was also stated.

For different desktops:
You can choose which to boot into at the splash screen. From my standard Ubuntu install, I installed LXDE and KDE to test by using ```
sudo apt-get install lubuntu-desktop
```
and
```
sudo apt-get install kubuntu-desktop
``` (other less sizable methods are available [http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html](http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html))

Then at the splash screen, there is a drop-down-box at the bottom, which allows you to select which environment you would like to boot into.

---

### Post by arashiko28 on 2010-03-26
Lubuntu is my new favorite flavor!!! Right now made me super IT at the house, everybody is happy with it, runs waay much better than XFCE on that coppermine and mine, well just fly! i might have it as well just for those cases where you want to presume speed! :D:D Thanks to all for your help!

---

