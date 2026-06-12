---
title: "sudo lshw-&gt; 82801H (ICH8 Family) HD Audio Controller: is this my &quot;sound card&quot;?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by swarup on 2009-05-22
I just installed Jaunty in a Dell desktop E520, and there is no sound. The sound was working perfectly in Ubuntu 8.10. I am trying to trouble shoot it, and need to know what I should set as the "sound card" where the HowTo's tell to put it in the various sound utilities of Jaunty.   

Here is what I think to be the relevant part of ~$ sudo lshw:

  ```
  *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

So according to the above, what is my sound card's name? The default options in the "Sound" utility (System->preferences->sound), in Default Mixer Tracks, are HDA Intel (ALSA Mixer), SigmaTel STAC9227 (OSS Mixer), HDA intel - STAC92xx Analog (PulseAudio). Does one of these sound like it matches the data I present above?

EDIT: On the basis of further reading and the above terminal output, I am currently under the impression that the currect setting for this computer would be "HDA Intel (ALSA Mixer)". Please let me know if this seems correct. The sound still does not seem to be working yet, which is all very odd given that the sound was fine in 8.10.

---

### Post by Didius Falco on 2009-05-22
Hi,

I've done a bit of googling, and come up with these links:

[ttp://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](ttp://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

That link has a link to Markbuntu's huge thread on solving sound issues, which is huge -kudos to him for maintaining it (Did I mention it was huge? <G>):

[ttp://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](ttp://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Here is a quick explanation from markbuntu on how the sound system actually works:

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

I hope these links lead you to a "sound" solution!!

Regards,

Didius

On Edit: I just ran across this LaunchPad bug report - it has a fix that has worked for several others with that same audio chip, but differing PCs - have a read-through and see what you think...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354398)

---

### Post by swarup on 2009-05-22
Didius,
Thank you very much for your kind and helpful suggestions. 
I had been reading Markbuntu's HowTo's and worked on this matter for about five hours today. I could not get the sound to work on that computer. I've dealt with Ubuntu sound issues multiple times on various computers, but this one when I could not get it working in five hours and needed the sound, I ultimately tried wiping Jaunty and reinstalling it fresh-- still no sound. So I removed Jaunty and installed Hardy, which I know works well on that computer. The sound worked immediately. 

Don't know why Jaunty play well with this Dell E520, but Hardy works just fine. If anyone ever gets a solution to this matter I'd gladly update to Jaunty. Until then, I guess we'll just stick with Hardy on this computer.  

Thanks again!
Swarup

---

