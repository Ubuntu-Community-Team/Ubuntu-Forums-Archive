---
title: "Trying to install drives for nvidia"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by servicetech on 2009-03-21
As a newbie trying to run mythbuntu for the first time I'm trying to get the graphics drivers installed in 8.10. The only driver options are 1.73 and 1.77, neither works really will with my M3N78-EM motherboard. I tried installing 9.04 aphla 6 and it had the correct driver just by clicking the install button. However 9.04 is still in alpha and still has more bugs to work out so that's a no go.

I've read a little about terminal commands but it seems like there is a long list of commands needed that will have to be written down before I can try to install using this method. It seems like Ubuntu is still relying heavily on terminal commands for advanced functions, reminds me 10 years ago when we were doing this with Microsoft DOS. The heavy reliance on terminal commands is IMHO why Ubuntu hasn't unseated Windows, the average user has no interest in learning manual command entry.

Is there an easier way to install a graphics driver than a 10 line command prompt? I *really* don't want to shell out $100 for the system builders version of Vista Home Premium with MCE built in. 

FWIW I do have another machine that is running plain Ubuntu successfully for the most part, so far I'm happy with it. Even if I end up buying Windows for my HTPC I'll be leaving Ubuntu on my main PC.

---

### Post by ivanvajar on 2009-03-21
Did you try in System/Administration/Hardware Drivers?

---

### Post by servicetech on 2009-03-21
Yes, the hardware drivers program only allows driver versions 1.73 and 1.77, neither works well. On Mythbuntu 9.04 alpha it had the option for a newer driver and it worked perfectly.

---

### Post by ivanvajar on 2009-03-21
Open Applications/AddRemove Applications and search for nvidia drivers.

---

### Post by servicetech on 2009-03-21
I'll give the KDE version a shot, maybe they will have different options than the gnome version (both types showed up in the add/remove).

Edited to add that I can't find where to open the program, only the gnome version shows up in the menu.

---

### Post by ivanvajar on 2009-03-21
Wait a moment. Don't quit on your problem like that. Use Synaptic to find nvidia drivers. You just need to install them. This is Ubuntu, not Sabayon.

---

### Post by servicetech on 2009-03-21
I found the "nvidia-180-modaliases" and installed it with Synaptic, it still doesn't show up as an option in the hardware drivers.

---

### Post by ivanvajar on 2009-03-21
Do you have nvidia-glx package installed?

---

### Post by servicetech on 2009-03-21
The 180 driver option showed up in the hardware manager after a restart. I installed and restarted again, now it's working perfectly. Whew, that was a close one I REALLY didn't want to give M$$$ another dime of my money.

Next project is getting the air2pc tuner card working, is this still a beginner question or does it go to another forum?

On a side note I will say it's the support you can get from people such as yourself that makes Ubuntu a feasible OS. Thanks for the help :)

---

### Post by ivanvajar on 2009-03-21
Any time :-) And YES, it's Absolute beginner question :-D

---

### Post by servicetech on 2009-03-21
OK, how do I get the air2pc DTV tuner card to work?
MythTV doesn't recognize it as a tuner. It's almost as I need the driver for it but I don't know where the Ubuntu equivalent of the 'device manager' is. Also I cannot get guide data to come through but the tuner may need to be functional before than happens.

While were at it let's go for 5.1 surround sound out of the SPDIF connector and get my Harmony 688 set up through LIRC. If I can get all of these to work my HTPC will be ready for primetime :)

I figure I'll have to use my one remaining windows machine to run the Harmony setup program (Logitech doesn't have a Linux version).

---

### Post by servicetech on 2009-03-22
I just gave Windows 7 beta a test run. Dolby digital works right out of the box and the monitor resolution auto set correctly. At least I know the sound issues aren't hardware/bios related. Air2pc card still doesn't work but it's not Windows compatible. Windows doesn't support LIRC, so I'll have to come up with another solution for the remote, probably will buy a windows compatible tuner W/WMC remote. For right now it looks like Windows 7 beta wins out for HTPC use. 

Now the question is how much is M$ going to want for it when the beta expires next year and where will Mythbunutu be? I hope by next year Mythbuntu is developed to the point where the average person can use it and it won't require lots of terminal commands/manula config to get it working.

I'm keeping ubuntu 8.10 on my main PC, I like the interface and how "light on its feet" it is compared to Windows. Ubuntu works MUCH better than XP, less crashes and a better interface. Vista is too much of a resource hog on older systems.

---

