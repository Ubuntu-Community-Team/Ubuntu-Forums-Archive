---
title: "Various Set Up Issues"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-05
For starters I have a Dell Inspiron 1150 and am running Ubuntu 10.10 Mavrick, I've read up a little on the graphics issues with the Intel 855GM integrated graphics cards. I wanted to try and load the proper drivers for my graphics chipset and was tring to follow the instructions here: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

But my system will not allow me to create the file to load the proper 855 drivers and try the fixes. As thing stand on my system now my monitor blinks out and quickly back on every so often, has issues playing videos and color control programs don't work.

Secondly what ever drivers control the battery and AC adapter the problem with this system is the icons don't reflect the system state, for instance if the charger is unplugged the icon for still charging is still displayed there is really no rhyme or reason to how it reacts and I don't even know what to search, to be able to get myself stuck on this one. 

This next one may be related to the last one the hibernate and suspend functions don't work. doesn't mater if I set it up to hibernate when the lid closes or if I click on the hibernate tab under the power icon, it's a no go.

Lastly sound and I'm not sure if this is driver or program related I've only noticed this with VLC player but the sound from a played DVD would intermittently cut in and out at random. That would lead me to belive software set up issues but I also get other quirky things like the sound on startup is sometimes there sometimes not.

My main thing is I want to be sure I have all the right proprietary drivers running (or at least the Linux versions) so I can use as much of my computers hardware systems and features as I can in Ubuntu.

---

### Post by mikewhatever on 2011-03-05
There are no proprietary drivers for your GPU.
To create xorg.conf, run the following command:
```
gksudo gedit /etc/X11/xorg.conf
```

copy/paste the suggested text, save and exit.

---

### Post by DGINSD on 2011-03-05
> **mikewhatever said:**
> There are no proprietary drivers for your GPU.
To create xorg.conf, run the following command:
```
gksudo gedit /etc/X11/xorg.conf
```

copy/paste the suggested text, save and exit.

Works great so far thank you any ideas on the other issues hibernation / power sensors, or the sound issues?

---

### Post by mikewhatever on 2011-03-05
Not sure about the rest, as I am not familiar with the hardware. Try searching for your model and Ubuntu.

---

### Post by DGINSD on 2011-03-05
A general question  about the graphics fix I applied when I boot up now I have a Ubuntu kernel entry menuentry 'Ubuntu, with Linux 2.6.37-graphics3+12-generic'--class ubuntu--class gnu-linux--class gnu--class os will the Intel 8XX GM driver and patches be applied to all future kernel entrys and if not how do I make it so.

An update on my hibernation issue I tested it out last night and it does go into hibernation and works properly if I click the power icon and then hibernate, but it won't hibernate when the lid closes, what gives? Seems like its not sensing what ever hardware tells my system the lid is closed, I know the hardware is working because it still works in Windows XP.

On a side not I has a strange glitch this morning, After downloading a pdf document to look at on a MSN page (not sure if that has anything to do with it or not) when I would click  on places/downloads or places/home or any places extention instead of opening that folder, "Dragon Player" would open. I uninstalled dragon player, as it didn't work anyway, and now things are working as they should, really weird.

---

### Post by DGINSD on 2011-03-06
Something I've noticed on the battery and power issues if I left click on the batter icon on my top bar and left click on "laptop battery is charged" it pulls up my "Power Statistics-Device Information" and I've noticed the refresh fields for both the battery and charger are 19913 seconds for the battery and 22164 for the charger. That seems awful high to me, how do I go about changing them to something more reasonable?

In system tools theres something called configuration editor I'd assume thats where but it's a bit intimidating reminds me a lot of Reg-edit in windows without all th e binary and stuff. What can be done with this and how does one use it?

---

### Post by DGINSD on 2011-03-08
Does Ubuntu/Linux have a program similar to Microsofts "Process Explorer" and also some ability to see all devices and device properties like in "device manager" these 2 programs have been very valuable to me when problems and questions regaurding performance and set up arise.

---

### Post by DGINSD on 2011-03-10
With regaurds to the graphics drivers I activated and fixes I applied I have a kernel in grub that loads the drivers and fixes and the text in grub identifies it as such "Ubuntu (a bunch of numbers to ID it)(other blah blah) graphics"                                                                                                                    The driver and fix I applied is listed in the first paragraph of the first post of this thread. My question is do I need to do anything else in grub to make these changes permanate and in turn part of all future kernels and upgrades?                                                                                                                I'm still having issues with my lid not being detected could changes to the acpi setting in the kernel help solve this issue?

---

