---
title: "No Microphone: Acer Aspire 5735-6694"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by bpowell2005 on 2009-02-14
Hello all,

Well, I'm declaring defeat and asking for help! I'm running Ubuntu Jaunty, fully updated, it's the only Ubuntu that's been on my new Acer Aspire. The Acer has a built-in microphone, however, I can't get it to work in Ubuntu. I can't find a way to select it when using the sound recorder, and all of my Skype test-calls come back silent!

This laptop also has windows, and the microphone works just fine in Windows (which was a good sanity check for me to verify there IS a microphone present!)

Any help would be welcome. I'm open to posting the output of various commands if needed...I'm not a Linux newbie, but I'm not an expert either; I know enough to know when I'm licked!

Thanks for your help team!

---

### Post by treesurf on 2009-02-15
Have you checked to the mic input level?  Double click on the volume applet in your taskbar.  Click Edit>Preferences to make sure that all available option boxes are checked and then look at you mic level.  Also make sure that the correct mic is selected.  For example under the options tab in my Volume Control mixer it lists mic, front mic, line, CD, etc...

---

### Post by bpowell2005 on 2009-02-15
> **treesurf said:**
> Have you checked to the mic input level?  Double click on the volume applet in your taskbar.  Click Edit>Preferences to make sure that all available option boxes are checked and then look at you mic level.  Also make sure that the correct mic is selected.  For example under the options tab in my Volume Control mixer it lists mic, front mic, line, CD, etc...

Tried that; everything is checked and both MIC Boost and INternal MIC Boost are turned up...when selecting either MIC or Internal MIC in options, no improvement.

choosing "MIC" does give a lot of "noise" in the Skype test call...sounds like digital data, not voice or feedback or anything like that.

---

### Post by treesurf on 2009-02-15
What is your audio card and chipset?  Typing "alsamixer" in the terminal will bring up the terminal version of the sound mixer.  In the upper right hand corner it will tell you the card and chipset.

---

### Post by bpowell2005 on 2009-02-15
> **treesurf said:**
> What is your audio card and chipset?  Typing "alsamixer" in the terminal will bring up the terminal version of the sound mixer.  In the upper right hand corner it will tell you the card and chipset.

Alsamixer says I have an HDA Intel with a Realtek ALC268 chipset.

Thanks!

---

### Post by treesurf on 2009-02-16
Some of the info on this page might prove to be useful.  I had a bear of a time getting the mic to work on my HDA Intel card as well, although mine is a different chipset:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Flag on 2009-02-16
Acer build in mic is front mic.

---

### Post by barretr on 2009-02-19
See: [http://ubuntuforums.org/showpost.php?p=6721529&postcount=23](http://ubuntuforums.org/showpost.php?p=6721529&postcount=23)

---

### Post by ujodarko on 2009-09-23
for me only alsamixer reconfigurating as root solved the problem. After that, graphical interface responded for the firs time, and as well after reboot.

Good luck!

---

### Post by apuglisi on 2009-09-26
Already posted this in other thread but I think this applies here as well.

After a big headache with the microphone thing, I've got it to work.
My notebook is an Acer Aspire 5720 Z and this is what got it working today:

Add the following lines to the configutaion file: /etc/modprobe.d/sound


# Code to get mic working:
options snd slots=snd-hda-intel
# u1Nb.Z0J4Co96n9E (ICH8 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

after rebooting, the soundcard was completely recognized with internal microphones and all.
I really hope this helps you.

---

