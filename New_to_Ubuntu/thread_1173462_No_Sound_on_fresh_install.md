---
title: "No Sound on fresh install"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-05-29
Hi All,
I am using the new LinuxMint 7, which is based on 9.04, so I am hoping that someone here knows what to do. 

I am getting no sound. I tried running something that I found in another forum, and some of the suggestions, but nothing worked, so...... figured I would start fresh and hope that someone can walk me through what to do?

Thanks

---

### Post by richg on 2009-05-29
I am running Mint 7 and I have volume but I have to put my ear up to the speaker. I have a couple speaker sets that have no volume at all. I did a bunch of things recommended here and in Mint forums but no joy. Still very low volume. Some others in the Mint forums have the same issue. There does not seem to be an easy solution. 
A couple threads are talking about it but the threads seems to die. No one seems to want to write up a complete solution, just try this or try that. 
I have been hacking around for over three hours. All gain controls are at max and nothing is muted. I have been into the command line for the mixer and everything is maxed out.
Right now I am opening the external speaker with the amplifier and increasing the gain of the preamp chip by modifying the feedback gain resistor for each channel.
All three speaker sets work very well with my stepsons Windows PC.

Rich

---

### Post by AndyP79 on 2009-05-30
Yea, I know what you mean about the threads dying. It seems like lately everything leads back to "did you google it?", yes, I did, that is why I asking here. Right? 

Well, I am going to just keep my eyes out and see if anyone come up with something..........

---

### Post by superprash2003 on 2009-05-30
try various combinations under system->preferences->sound ,

---

### Post by Seline on 2009-06-08
I got my audio working by:

Downloading this [http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.1/alsa-driver-linuxant_1.0.20.1_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.1/alsa-driver-linuxant_1.0.20.1_all.deb.zip), compressed and installed it.

Then in Terminal I typed:  sudo gedit /etc/modprobe.d/alsa-base.conf
and added a line:
options snd-hda-intel model=laptop
at the end of the file

Then I restarted,  and made sure from audio that nothing was muted.

Hope this helps.

---

### Post by taavikko on 2009-06-08
Please post the output from "aplay -l" to get info for the chipset
Then edit /etc/modprobe.d/alsa-base.conf 
to use correct options for that particular chipset.

---

