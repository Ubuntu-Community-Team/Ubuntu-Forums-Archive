---
title: "Media Converter"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-15
Im looking for an app to convert media to various formats (i.e mkv to mp4). Any suggestions? I tried winff and it couldnt get the job done.

---

### Post by Revolutionary101 on 2010-07-15
I would suggest using Avidemux. It supports multiple formats and it allows you to configure many options. I have tried many other converters and I have been able to configure the H.264 codec to perform 50% better than the Divx and Xvid codecs. I think this is by far the best GUI converter for any OS.

To get it type this into terminal:
```
sudo apt-get install avidemux
```

---

### Post by TimEnid on 2010-07-15
> **Revolutionary101 said:**
> I would suggest using Avidemux. It supports multiple formats and it allows you to configure many options. I have tried many other converters and I have been able to configure the H.264 codec to perform 50% better than the Divx and Xvid codecs. I think this is by far the best GUI converter for any OS.

To get it type this into terminal:
```
sudo apt-get install avidemux
```

 thanks alot, trying it out now.

---

### Post by TimEnid on 2010-07-15
not sure whats going on. i click on Open and select my video, and a screen pops up re: matroska, then it counts down and i get h.264 detected and asks me if i want to use safe mode. after i select safe mode, it starts acting buggy, the screen enlarges and when i click anywhere, it just jumps around. im unable to convert the media.

---

### Post by TimEnid on 2010-07-15
got this message: codec error the number of channels is greater than what the selected audio can do. either change codec or use the mixer filter to have less channels

---

### Post by bark50 on 2010-07-15
I can't help with the Avidemux problems, but if you're comfortable installing an application from a PPA, I can recommend Handbrake for video conversions:  [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots")

---

### Post by TimEnid on 2010-07-15
> **bark50 said:**
> I can't help with the Avidemux problems, but if you're comfortable installing an application from a PPA, I can recommend Handbrake for video conversions:  [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

not familiar with ppa, but always willing to learn. how do i go about using this? thanks again for the help.

---

### Post by bark50 on 2010-07-15
> **TimEnid said:**
> not familiar with ppa, but always willing to learn. how do i go about using this? thanks again for the help.

Try this:  Open a terminal (which is at Applications -> Accessories -> Terminal).  Copy and paste this into the terminal:  sudo add-apt-repository ppa:stebbins/handbrake-snapshots  Enter your password at the prompt, hit your enter key and let the terminal do its thing.  If there are no errors, open up synaptic (System -> Administration -> Synaptic Package Manager).  (If there are errors, you'll need someone more knowledgeable than me to help!)  Do a search in synaptic for Handbrake and install the one that says Handbrake-gtk.

I assume you're running Ubuntu 10.04.  If you're running an earlier Ubuntu, these instructions won't work.

To clarify:  Copy and paste "sudo add-apt-repository ppa:stebbins/handbrake-snapshots" (without the quotes) into the terminal.

---

### Post by TimEnid on 2010-07-17
this is what i got after doing that  > Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 43D3A9F60C58A7169778E6FB8771ADB0816950D8 gpg: requesting key 816950D8 from hkp server keyserver.ubuntu.com gpg: key 816950D8: &quot;Launchpad HandBrake Snapshots&quot; not changed gpg: Total number processed: 1 gpg:              unchanged: 1  i checked synpatic, and handbrake is not there

---

### Post by bark50 on 2010-07-17
Tim, when you have Synaptic open, click on the Reload button in the upper, left corner.  Then look for Handbrake-gtk.  Your output from the terminal is exactly what I got also when I installed Handbrake.

---

### Post by TimEnid on 2010-07-17
> **bark50 said:**
> Tim, when you have Synaptic open, click on the Reload button in the upper, left corner.  Then look for Handbrake-gtk.  Your output from the terminal is exactly what I got also when I installed Handbrake.

that worked my friend. thanks a lot.

---

### Post by bark50 on 2010-07-17
Phew, that's a relief!  :lol:  This probably isn't pertinent to your situation, but I'll pass it on anyway.  One aggravation I have with Handbrake is that it does not rip video directly from a DVD.  I have to rip the DVD to an iso file, save the iso to my desktop, and then use Handbrake to rip from the iso.  Anyway, glad you get the chance to try Handbrake out.  It has always worked better for me than Avidemux.

---

### Post by TimEnid on 2010-07-18
wheres all the presets for handbrake? i dont see any option for a zune.

---

### Post by bark50 on 2010-07-18
No, no options for Zune in Handbrake AFAIK.  It just does video conversion to MP4 or mkv.  You might want to open Synaptic and do a search for "zune."  The search will take you to ogmrip-profiles.  When you read the description, does that sound more of what you're looking for?  If so, give it a whirl.  I've used ogmrip but found it to be really slow on my machine.  You might have better luck.

---

### Post by Mr.Brownow on 2010-07-19
3.	Hi! I have compared different converters and I recommend Easy-Remove-DRM. It convers music and movies. The converters is easy to install and use. 
[http://easy-remove-drm.com](http://easy-remove-drm.com)

---

### Post by Legendary_Bibo on 2010-07-19
> **Mr.Brownow said:**
> 3.    Hi! I have compared different converters and I recommend Easy-Remove-DRM. It convers music and movies. The converters is easy to install and use. 
[http://easy-remove-drm.com](http://easy-remove-drm.com)

That's not pertinent to his question, and that's for windows.

---

### Post by MrWES on 2010-07-19
> **TimEnid said:**
> Im looking for an app to convert media to various formats (i.e mkv to mp4). Any suggestions? I tried winff and it couldnt get the job done.

Read this thread, jump to my post, #4. There is no need to transcode mkv to mp4. Follow my instructions and you'll have a working mp4 in a matter of minutes:

[http://ubuntuforums.org/showthread.php?p=9370090#post9370090]("http://ubuntuforums.org/showthread.php?p=9370090#post9370090")

One thing I would add, if the mkv audio is dts and you don't have a dts cabable audio system, you can convert it to ac3 with ffmpeg:

```
ffmpeg -i audio.dts -ab 448k audio.ac3
```

Bill

---

