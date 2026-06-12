---
title: "two questions"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by VioletsPie on 2009-05-06
1) I'm a big noscript fan but I find it problematic on Ubuntu Firefox.. is it even necessary to worry about in general on Linux? 

2) I'm having problems getting flash to work and I did read the forum below and I know I have multiple flashes installed.  How do I find out all the ones I have installed and how do I uninstall them and which one is the best to install?

ahh! oh yeah im on jaunty 64

VP

---

### Post by glotz on 2009-05-06
1) I'm a big fan too. It is still neccessary. What kind of problems do you have?

---

### Post by VioletsPie on 2009-05-06
It just seems more obtrusive than on Windows.

---

### Post by albinootje on 2009-05-06
> **VioletsPie said:**
>  2) I'm having problems getting flash to work and I did read the forum below and I know I have multiple flashes installed.  How do I find out all the ones I have installed and how do I uninstall them and which one is the best to install?


Not sure about flash in 64 bit, perhaps ask in the 64 bit section.

This might show all installed flash packages :
```

dpkg -l|grep flash

```
It won't however show anything which installed without using .deb packages.

---

### Post by VioletsPie on 2009-05-06
As for my flash problems I used that command and went into synaptic and completely removed all flash, restarted, took a cue from the thread below and installed the (controversial? questionably ethical?) ubuntu-restricted-extras and all things are go. 

:guitar:

---

### Post by Junkieman on 2009-05-06
> **VioletsPie said:**
> 1) I'm a big noscript fan but I find it problematic on Ubuntu Firefox.. is it even necessary to worry about in general on Linux? 

I'm also a big fan, and the short answer is yes, it is more secure using noscript in linux.

As a developer, and the longer answer, is that there is no single instance when any OS is safe from exploits. Someone might discover a new exploit tomorrow, and implement this exploit using JavaScript or Flash for example, and do whatever their dirty little hearts desire. Because of the way Linux is designed it's much harder to cause critical damage to your system, but your personal files (those owned by you) *could* be at risk, depending on what this exploit can access.

Stick with noscript if you like the extra layer of security, I do! It's the best way to prevent scripts from untrusted sources running on your system :)

Re the flash, run System -> Administration -> Synaptic, and search for 'flash', and see what you have installed. It might be a good idea to remove those, and afterwards go to a flash enabled site in firefox, it should prompt you for a flash plugin, and take you to the install page automatically.

Hope this helps :D

---

### Post by glotz on 2009-05-06
[QUOTE=VioletsPie]controversial? questionably ethical?[/QUOTE]Yes and yes. Read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by presence1960 on 2009-05-06
> **VioletsPie said:**
> 1) I'm a big noscript fan but I find it problematic on Ubuntu Firefox.. is it even necessary to worry about in general on Linux? 

2) I'm having problems getting flash to work and I did read the forum below and I know I have multiple flashes installed.  How do I find out all the ones I have installed and how do I uninstall them and which one is the best to install?

ahh! oh yeah im on jaunty 64

VP

search synaptic for flash and mark all for complete removal. Then follow this from the x86-64 Users section of the forum : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by VioletsPie on 2009-05-06
My flash and noscript issues are now resolved, thanks!

I have another question and I'm going to ask it here rather than starting a new thread. 

I have a HP Pavilion dv6000 laptop (well, technically a DV6985SE which is the dv6000 refurbished and sold on compusa. For the record, saved hundreds of dollars and no problems.. but the 90 day [no] warranty thing might be an issue sooner rather than later :o)

Anyway the dv6000 has got these external touch buttons for media.. windows requires a driver for them to work but they function out of the box in jaunty.

HOWEVER.. I mostly listen to music or simplynoise.com through ear buds plugged into the primary headphone jack in the library. If I attempt to adjust the volume using the external touch buttons the sound will start to blast out of the laptop's internal speakers as well as my headphones. I don't notice this until someone angrily jabs me as Stravinsky's Rite of Spring comes blasting through the library corridor! :oops:

The easy solution is to adjust the volume in ubuntu but habits die hard and I sometimes absent-mindedly or accidently hit the touch buttons. Whether it's mute/unmute/volume whatever, the result will be audio through both earbuds and internal speakers until i plug my earbuds out and in again.

I also have to make sure when booting or rebooting that the earbuds are unplugged and plug them in right as soon as i hear sound initialize in the startup screen or else the same will occur. 

That's my long-winded.. third question.. here in the beginner's board.

---

### Post by glotz on 2009-05-07
There probably is a smarter way to do it but you could write a script that first looks at the speaker volume and if that's zero, the buttons then will instead change the headphone volume. To do this, you need to pop open a mixer and play a tune. Then insert the headphones and see which track volume drops to zero. Then we can write you the scripts and point the hotkeys to them.

---

### Post by freeman2000 on 2009-05-07
I also have a 2yr old HP dv6000 laptop that came with Vista.  It has been a great trouble-free laptop.   Your sound problem has a simple solution - both for Ubuntu and for Vista.  Those buttons are part of HP's QuickPlay system.  To get it to work (both CDs & DVDs - both music & movies) without firing up an OS, you need to go in and enable QuickPlay.  You can do this easily with a Windows program called CCleaner, or from Windows Defender.  Now, as far as the sound problem, the 2 QuickPlay keys on the right are for your sound.  The right-most key is for the volume adjustment.  The 2nd right-most key has a speaker icon on it.  It is usually blue, and if you tap on it, it will turn orange and MUTE the speaker.  No external sound.  This works for both Linux & Windows.  Good luck.

---

### Post by Junkieman on 2009-05-07
> **VioletsPie said:**
> Whether it's mute/unmute/volume whatever, the result will be audio through both earbuds and internal speakers until i plug my earbuds out and in again.

Hello Pie, try disabling those volume buttons, from the main Ubuntu menu, go System -> Preferences -> Keyboard Shortcuts

You will see a list of global shortcuts, select the volume up item and press *Backspace* to turn that shortcut off. Do the same for volume down and mute. Close the shortcuts window and try your buttons now.

It's a work-around but if it works, at least it you won't have sound blaring if you accidentally press the vol buttons :)

---

