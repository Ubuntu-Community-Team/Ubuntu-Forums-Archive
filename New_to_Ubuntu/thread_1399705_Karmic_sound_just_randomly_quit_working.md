---
title: "Karmic sound just randomly quit working"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Apache0c on 2010-02-06
I posted this in Absolute Beginner Talk because I am an eternal Linux NOOB. I've been working on it for 10 years and I'm just now figuring out how to use Sudo... I kno, I kno...

I'm pretty hopeless.



Anyway, I thought I was some sort of cool hacker because I was able to install Karmic on my machine and get everything working without a hitch. I had sound working both on my external 5.1 and on my USB headset, I installed Firestarter and even dressed things up with compiz and emerald. I installed Windows 7 Ultimate in Virtualbox and got it working in seamless and yeah, I basically bragged to everyone I know...

Now a week later, and all in the same day, I come home and somehow my firewall is stopped, my USB keyboard completely quit on me and my sound just randomly stopped working. fml

I dont care about the keyboard and while the firewall is a mystery, I've reactivated it and will deal with that later. But as far as the sound, I'm lost, I've read endless pages about scripts and root terminal commands and I'm hoping there is some sort of fix I can download and install with the GUI, it makes me feel pathetic.

I've ran all of my updates and restarted several times, I've checked and rechecked my settings... Can anyone help me?

---

### Post by Apache0c on 2010-02-06
Ahh... I guess it is really busy around here, a lot of us noobs looking for someone to make their problems easy. lol :D

Anyway, thanks to anyone who reads this and hopefully you maybe at least get a laugh out of my story because I did indeed get the sound working again.

Solution: In the sound preferences, hardware tab, with my primary audio output device selected,  I just scrolled through the "Settings selected for this device:" at the bottom. While I had an audio application playing, I started at the top with "Off" and just used my scroll wheel to click through each one until the sound came on.

Note: I'm not a total noob because I was aware of this and I had initially set it up with the correct setting. Which is why it was working before. But for some reason, going back to off and then back around to the correct setting corrected the problem.

Thanks again to anyone that does read this with the intention to help, I know that you're busying solving as many problems as you can.

---

### Post by 23dornot23d on 2010-02-06
I had to install the Alsa drivers again today to get my sound back ..... 

depends if pulseaudio works for you or not ..... it does not for me .....

alsaconf ........ in a terminal window does the trick for me ......

---

### Post by Apache0c on 2010-03-06
I have to do the scroll trough method that I posted above every once in a while. For some reason it just glitches out and disconnects sometimes. Then it works fine again for a while.

---

### Post by Apache0c on 2010-03-22
Wanted to update this. I've had another random occurrence of the sound not working. This time it was strange because it worked through my usb headset but not through my digital output to my speakers. And my previous solution didnt fix the problem this time.

Oddly enough, I installed Gnome ALSA Mixer and the master volume mute checkbox was checked. Yet it was not checked in the default Gnome Sound Preferences. Unchecking it in the ALSA Mixer fixed the issue.

---

