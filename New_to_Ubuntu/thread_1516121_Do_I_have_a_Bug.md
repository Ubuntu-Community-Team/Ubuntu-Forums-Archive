---
title: "Do I have a Bug?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by myrnamynkoff on 2010-06-23
Hi friends,

 I'm having some 'strange' problems on my computer, I just started using ubuntu a few months ago so I'm still a little bit new around here.. I have an Acer Aspire 1 netbook, and I just ran all the system tests and everything seems to be working fine.
I think the problem started after I updated to the 10.04 version (it took me a few months to do that because at first I thought that I had to back everything up as it would delete all my files :S ) Anyways, after the update I have certain problems... the most annoying one is that everyday now at least twice a day, if I have some tags opened in firefox, I would click on one and it will close it. I would open the tag again, and all the sudden I click on it and it closes it again. Finally it started happening with firefox itself that it would close. So that's one.

Second, pulseaudio is really giving me a bad time. Before updating this problem already existed somehow. It was that if for example I wanted to use Skype, I had to first go to the terminal and kill pulseaudio, then open skype, make my call, and then once i was done i needed to go again and activate it. But now it's like the opposite. Skype works fine, but if I use for too long, I loose audio on any webpage I'm at. And on the other hand now I don't have a volume icon, so if i want to mute the pc I have to go to the terminal and activate pulseaudio to do it so, but most likely I'll loose sound 'somewhere' by doing that.....

Finally, and I think this is the most dangerous one: every time i plug or unplug the battery charger to the wall, it's like the computer's screen goes blank, the hard disk goes to sleep, and I have wake the pc up and log in again. this happens many many times a day, it's really annoying and I don't know how to change it :(

So, I guess my question is... regarding what's happening with Firefox, is it a bug or something? And with pulseaudio and the problem with the power adapter and the pc going to to sleep.... can we fix that? :confused:

I hope so!

Thank you  :)

---

### Post by sb5551 on 2010-06-23
Unfortunatly, I can't help you with your problems, but Firefox just started doing what you described for me yesterday too. This was on my netbook remix.

---

### Post by Bucky Ball on 2010-06-23
Applications->Sound & Vid->Pulse Audio Device Choooser. Click the icon which is now in the toolbar. Select Pulse Volume Control, start a playback stream (Skype, Firefox, VLC, etc) with the playback stream window open. You should see the playback stream. Right click on the stream and 'Move Stream', and move it to the device you want to use.

Don't know if that will fix your problem. Pulse is the go but it can be nightmareishly tricky. Took me an age to get it together on the laptop (haven't bothered with the other machines - if it's not broke don't fix it!).

---

### Post by myrnamynkoff on 2010-06-23
> **Bucky Ball said:**
> Applications->Sound & Vid->**Pulse Audio Device Choooser**. Click the icon which is now in the toolbar. Select Pulse Volume Control, start a playback stream (Skype, Firefox, VLC, etc) with the playback stream window open. You should see the playback stream. Right click on the stream and 'Move Stream', and move it to the device you want to use.

Don't know if that will fix your problem. Pulse is the go but it can be nightmareishly tricky. Took me an age to get it together on the laptop (haven't bothered with the other machines - if it's not broke don't fix it!).


I don't have Pulse Audio Device Choooser there, not even after I tried activating pulseaudio from the terminal... any idea on why is not there? :/

---

### Post by Bucky Ball on 2010-06-23
You might want to look at post #8 here:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

I was fixing hardy. You want to search for installing Pulse Audio for 10.04. Doubt if you have any bugs, 10.04 is buggy for many (most posts concern this release) but will improve over time. Just get updates regularly and you might find some of your issues resolve.

---

### Post by Locke_99GS on 2010-06-23
Because it's not included in Ubuntu by default, and it's depreciated. The package is "padevchooser", if you want it though. I believe PulseAudio Volume Control ("pavucontrol", also not installed by default) has picked up the functionality of the Device Chooser.

---

### Post by myrnamynkoff on 2010-06-23
> **Locke_99GS said:**
> Because it's not included in Ubuntu by default, and it's depreciated. The package is "padevchooser", if you want it though. I believe PulseAudio Volume Control ("pavucontrol", also not installed by default) has picked up the functionality of the Device Chooser.



Ok thank you! I don't know what 'depreciated' means (sorry, i'm not a native english speaker, cool word though :P ) But i will install that package now and then I will follow Bucky Ball's advice on the first post he/she made. I'll let you know what happens :)


ps: anyone knows how to fix my other problem of the computer logging off and going to sleep every time i switch from power from the wall to battery, or vice-versa? I think it has to do with some power management options but I can't figure it out.

---

### Post by myrnamynkoff on 2010-06-23
> **myrnamynkoff said:**
> Ok thank you! I don't know what 'depreciated' means (sorry, i'm not a native english speaker, cool word though :P ) But i will install that package now and then I will follow Bucky Ball's advice on the first post he/she made. I'll let you know what happens :)


ps: anyone knows how to fix my other problem of the computer logging off and going to sleep every time i switch from power from the wall to battery, or vice-versa? I think it has to do with some power management options but I can't figure it out.


 
Ok, no, it't didn't work..... this is what I got trying to install the package

W: Falló al obtener [http://cr.archive.ubuntu.com/ubuntu/pool/main/libg/libglademm2.4/libglademm-2.4-1c2a_2.6.7-2build1_i386.deb](http://cr.archive.ubuntu.com/ubuntu/pool/main/libg/libglademm2.4/libglademm-2.4-1c2a_2.6.7-2build1_i386.deb)
  Algo malo sucedió resolviendo «'cr.archive.ubuntu.com:http» (-5 - No hay dirección asociada con el nombre de host)

It's saying that it failed to get the package because something bad happened solving  «'cr.archive.ubuntu.com:http», that there's not address related to the host name.

I'm really confused now :(

---

### Post by mörgæs on 2010-06-23
It sounds like you have a backup. If this is the case, you could just reinstall 10.04 (not upgrade). 

You learn a lot about Ubuntu while fixing errors, but if the purpose is to get the machine running I would rather put one hour in a reinstall (with cable) and see if it fixes some if not all of your problems.

---

### Post by myrnamynkoff on 2010-06-23
well... yes.... that sounds like a good idea... i guess i'll do that as soon as i have time,

thank you all :)

---

