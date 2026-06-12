---
title: "Splash screens and Sound card drivers...help?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by nuzzy2811 on 2011-04-26
Hi Ubuntu people. 
I'm completely new to Ubuntu; I installed it two days ago and have spent that time running Windows XP in VirtualBox in order to retrieve an .inf file to make my Netgear adapter work.

After fixing my wifi problem I installed my graphics card driver through the Additional Drivers application because without it I cannot see the full screen due to 'overscan'.  
Anyway, to cut a long story short the splash screens no longer come up since I installed the graphics card driver. I have looked through other threads on this forum but all of the solutions have something to to with putting codes into the terminal which I don't understand due to the fact that I'm new.

Any help is greatly appreciated.

Also if anyone knows how to install the driver for the SB Audigy II sound card please let me know. I'm lost without sound!

---

### Post by calavier62 on 2011-04-26
Graphics card: Please give us the make and model. Otherwise, we can't help you. Sorry.

Sound card: well, the majority of things that relate to drivers involve something with the terminal. First let's make sure you have 'alsamixer' installed, and all you have to do is copy (Ctrl+C) and paste it into a terminal (Paste for terminal is Ctrl+Shift+V):
```
sudo apt-get install gnome-alsamixer
```

Now open GNOME ALSA Mixer from Applications -> Sound & Video -> GNOME ALSA Mixer.

If you have Unity, just type in 'GNOME ALSA Mixer' into the applications search bar


Choose the tab: “SigmaTel…”
 and Turn on “Audigy Analog/Digital Output Jack”


Now try your sound. If it still doesn't work, try the correct drive from this site: 

[HTML]http://opensource.creative.com/soundcard.html[/HTML] and follow the readme to install the driver. If you need help, please attach the readme in a post (little paperclip next to the smiley face in the formatting toolbar located below 'Message:').


Best of luck to you!

---

### Post by nuzzy2811 on 2011-04-26
Done! My sound now works, Thank you very much. 

My graphics card is the Sapphire RADEON HD 4350. hope this helps...

---

### Post by calavier62 on 2011-04-27
Well, that's good to hear that you can now use your sound card. I decided to post two methods to fixing the bootscreen, and hopefully you'll get a good result.
first try pasting this into your terminal: 

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```And then this (after you've run the first command): 
```
sudo update-initramfs -u
```And reboot after your done. If the bootscreen still didn't appear, try my other method:

Download the zip file I attached, open it, and just drag the folder onto your Desktop.
[ATTACH]190135[/ATTACH]

next, type this into a terminal ```
gksu nautilus
```Navigate to your '/lib' directory (left panel (filesystem) then open the 'lib' folder in the main window)

drag the folder (plymouth) from your desktop to '/lib'. close the nautilus window (but not the terminal)

type these into the terminal (one at a time)
```
sudo update-alternatives --config default.plymouth
``````
choose ubuntu-logo.plymouth
``````
sudo update-initramfs -u
```And of course reboot. You should now have a splash screen (if the other method didn't work)

If this didn't work, don't hesitate to say so.
Good Luck!

---

