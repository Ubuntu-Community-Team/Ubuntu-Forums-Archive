---
title: "PCSX - the cd does not appear to be a valid playstation cd"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by ahiung on 2011-04-07
Help, I already created the ISO from the PSX game that I want to play. Can anyone help me?
I spent my day travelling into the unknown world wide web searching something that can make any psx game running on my small laptop.

*I tried pSX, but after choosing the BIOS i got a present "[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams, SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault"

*after various reasons, I went to epsxe, downloaded 2 different versions. Result: Pitch Black screen and present me "Gdk-ERROR **: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0." after I close the program. also, It did mention that I wont have any sound. crap---

*After decade, I found someone said about PCSX. wow, I found it great and seems very Ubuntu-nism, and looks like everything run well...at first, I don't have any ISO game file. After I got a program called K3b, I transmute the .ECM file to .ISO. I had a great feeling, At last this will run! hahaha I don't want to care about the sound, joystick, or any plugin yet. I just want to see something pop up with some pictures. but, here I am...suffering 
from this unlucky events.

I'm newbie, this is my first time on Ubuntu Linux, using 10.10 MM. It's sad though that I can't play some/many PC games on it. I don't like wine. But, I found out that PSX doesn't use wine. I don't know how mess up is the Ubuntu language, but I just can't find the fine solutions for the errors in google...

Sorry bout my bad English:(

---

### Post by mips on 2011-04-07
Install AcetoneISO.
Open AcetoneISO, click Image Conversion --> Generate ISO from CD/DVD and it is: --> a Playstation 1 Game

The above will create a **.bin** file which you can open with PCSX.


You might want to have a look at [http://ubuntuforums.org/showthread.php?t=1686297](http://ubuntuforums.org/showthread.php?t=1686297), I find the N64 platform much more fun than the PS1.

---

### Post by ahiung on 2011-04-07
omg, i am so stupid. some1 said that i can convert the .ECM file to .ISO by safe it as .ISO, using burning software. That was so lame.
I solved this problem by UNECM the ECM file to IMG.
For some1 has the problem, you need to write it appropriately in Terminal. remember to add slash opposite with `/` before the space.
Actually by converting this to 1 IMG file(instead of 3 files .ECM,.CCD,etc), I can play on ePSXe too! except for pSX, I crashed right after choosing BIOS.

I:m closing this thread right now.:P

---

### Post by ahiung on 2011-04-07
> **mips said:**
> Install AcetoneISO.
Open AcetoneISO, click Image Conversion --> Generate ISO from CD/DVD and it is: --> a Playstation 1 Game

The above will create a **.bin** file which you can open with PCSX.


You might want to have a look at [http://ubuntuforums.org/showthread.php?t=1686297](http://ubuntuforums.org/showthread.php?t=1686297), I find the N64 platform much more fun than the PS1.

btw, It seems you attracted me to your N64, I never played it yet. hopefully they have a game with a decent story like suikoden.

---

### Post by mips on 2011-04-07
> **ahiung said:**
> btw, It seems you attracted me to your N64, I never played it yet. hopefully they have a game with a decent story like suikoden.

Try Legend of Zelda: Ocarina of Time as well as Majora's Mask although not strictly RPGs.

Quest 64, Hybrid Heaven, Ogre Battle 64: Person of Lordly Caliber, Super Robot Wars 64, Zool: Maj&#363; Tsukai Densetsu, Paper Mario, Aidyn Chronicles: The First Mage, Paper Mario: The Thousand-Year Door are some listed N64 RPGs with Ogre Battle 64 being popular I think.

---

