---
title: "no sound on dell latitude d600"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by michael_k on 2009-11-03
I'm very new to this and have found some solutions to lack of sound on laptops, but none of them have worked for me. I'm running 9.04 on a Dell Latitude D600. I'd appreciate any advice or solutions. I had sound the first few times I booted, but no longer.

---

### Post by RedSingularity on 2009-11-03
In System>Prefs>Sound click the test buttons.  Do you hear anything at all?

---

### Post by michael_k on 2009-11-03
Nope, none at all. Not with headphones, not on the speakers.

---

### Post by RedSingularity on 2009-11-03
Do you have Alsa installed?  Do this in a terminal.

sudo apt-get install alsa

see what it says when you run that command.

---

### Post by michael_k on 2009-11-03
It says the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

M

---

### Post by RedSingularity on 2009-11-03
Do this then

sudo apt-get autoremove --purge pulseaudio

and Restart the computer.

---

### Post by nadian on 2009-11-03
try this thread it sorted me out [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by michael_k on 2009-11-03
Red -

Nope, nothing.

---

### Post by michael_k on 2009-11-03
Nadian -

I've tried that, but I can't find my model in the list. I've tried a couple, but it's not working.

---

### Post by RedSingularity on 2009-11-03
Post the output of 

lspci | grep Audio

---

### Post by NJ0E on 2009-11-03
I have a question along these lines.  I have no audio -- my sound card in mylaptop was fried.  I have no need for sound in this computer.  Can I remove pulseaudio completely?  Is it 'integral' to any other programs?  

Thanks,

Joe

---

### Post by michael_k on 2009-11-03
Here it is.

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

---

### Post by RedSingularity on 2009-11-03
> **NJ0E said:**
> I have a question along these lines.  I have no audio -- my sound card in mylaptop was fried.  I have no need for sound in this computer.  Can I remove pulseaudio completely?  Is it 'integral' to any other programs?  

Thanks,

Joe


You can remove pulse completely if you dont need sound.

sudo apt-get autoremove --purge pulseaudio

---

### Post by RedSingularity on 2009-11-03
> **michael_k said:**
> Here it is.

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)


Ok in a terminal type this.............

alsamixer

Make sure volume is all the way up.

---

### Post by RedSingularity on 2009-11-03
Also you can install...........

sudo apt-get install gnome-alsamixer

This gives you many sound level options.

---

### Post by michael_k on 2009-11-04
Problem solved! I ran the ALSA upgrade script found here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Thanks for your time.

M

---

