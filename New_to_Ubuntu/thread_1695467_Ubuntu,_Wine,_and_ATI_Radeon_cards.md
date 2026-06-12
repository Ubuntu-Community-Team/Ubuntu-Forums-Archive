---
title: "Ubuntu, Wine, and ATI Radeon cards"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Metapanda on 2011-02-25
First of all, here's my pc's specs

Dell OptiplexGX260
1.5 GB DDR1 RAM
ATI Radeon 2600 HD Pro AGP
300 GB hard drive (with Ubuntu installed there's about 60 GB left total on my hard drive, the Ubuntu partition has about 20 out of 30 left I think)



I tried setting up Ubuntu the other day using Wubi, and so far, it works good. I installed Wine, and everything went smoothly, and I also installed fglrx (think that's the name of the driver). I then downloaded Get Amped 2 in order to test it out. Get Amped 1 (Splash Fighters) recieved a decent score from the Wine page, so I figured that Get Amped 2 would work as well. 

I managed to install the game and open the patcher, and it patched successfully. However, when I started up the game, I got audio, but the screen was black. I tried pressing ctrl+alt+delete and I saw the menu bar, but the blackness was still covering the rest of the screen, with some glitchy mess in it. I had to reboot my pc because there was no way to close it.

My burning question is, is this a Wine problem, video card problem, or something else? I'm thinking maybe the game isn't compatible, or I didn't fully set up my video card. I couldn't seem to get Catalyst Control Center working after all.

---

### Post by LowSky on 2011-02-25
do you run Wine's setup before attempting to play the game?

Also try Playonlinux. PlayOnLinux is a front-end for wine. It permits you to easily install Windows Games  and softwares on Linux. It also install Windows Fonts too to help with text. Please give it a try

---

### Post by Metapanda on 2011-02-26
As far as I know, POL only works if someone makes a script for a specific game. And their forum was almost totally dead last time I was there, and they mostly just do retail games anyway =/

And I'll give that other suggestion a try, although I did make a mistake and try installing xorg when I already had fglrx installed. I need to find a way to uninstall xorg.

---

### Post by Metapanda on 2011-03-02
Update: I booted up Ubuntu and I saw something about xorg before getting into Ubuntu. I guess it was an update or something. Once I got on, I uninstalled anything that had to do with fglrx, while keeping xorg. I got an update for xorg, along with some other Ubuntu updates (starting to think that Ubuntu is easier to work with than Winblows xD). I installed all of the updates, then tried installing Wonderland Online. Then I tried loading it, and there was a slight delay and an error, but on the 2nd try I managed to load up the game. It seems to run a bit slower (although that's probably because I'm used to TinyXP with Gamebooster), but it does at least work.
 
I still haven't tested any 3d games yet, but I'm assuming that my video card is now playing nicely with Ubuntu and that Wine is working. However, I cannot figure out how to get Catalyst Control Center. The only version I saw was for fglrx, and I figured that it should work with xorg as well, since it's for ATI Radeon cards, but no dice. I did find out how to change the gamma through terminal, although I would prefer an easy to use GUI.
 
Also, does anyone know how to get Get Amped 2 to work? Every time I load it up, the launcher has glitchy graphics, and when I load the game, I still have the audio with no sound problem, and the glitchy graphics everywhere when I try to close it.
 
If I can get Aika, Get Amped 2, and S4 League to work with Ubuntu, I could finally drop my XP partition, and I would probably even pay for Cedega if I knew everything would work with it, and there were no viable free alternatives.

---

### Post by Mark Phelps on 2011-03-02
IF it's Amped 2 v2.2, it simply won't work.  See the link below to the WineHQ site for that app:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7626]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=7626")

Wine is not a miracle cure, and while it CAN run some apps and games, the results vary enormously with the game/app and the specific version.

The WineHQ site is an invaluable source of info on any app/game that you want to run in Wine.

As to your assumption  of Ubuntu being easier to use -- that depends very much on what you're trying to do.  Installing CCC, for example, in Windows is simply running a setup file, granting it permission and then sitting back while it works.  Can't get much easier than that.  Doing the same in Ubuntu CAN be equally easy -- if it works.

Installing apps can be equally easy in both -- running a setup file in Windows, selecting from options in Software Center in Ubuntu.

What Ubuntu, specifically, and Linux in general, bring to the table is a much greater variety of customizations, and often, to a much greater depth of detail -- than is typically available in Windows.

So, there tends to be more that you CAN do in Ubuntu -- and not all of that is easy to do.

And finally, CCC will only work with the fglrx drivers; not with the open-source drivers.

---

