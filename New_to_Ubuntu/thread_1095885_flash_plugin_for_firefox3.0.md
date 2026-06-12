---
title: "flash plugin for firefox3.0"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by idom on 2009-03-14
Hi
I have just started with ubuntu. And it looks great. However,
I am not able to play any video on youtube.
It says"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. " 

I chcked on Edit->preferences-->content tab that Javascript is enabled in firefox.
I installed flash-plugin-nonfree through synaptic package manager and restarted firefox. 
I also downloaded "Adobe Flash Player version 10.0.22.87 - .deb for Ubuntu 8.04+ | 3.8MB  " from <http://get.adobe.com/flashplayer/> However, synaptic package manager is not able to open that. And when I double click it opens package installer and says "Error:Dependency is not satisfiable libpango:1.0-0"

Help is appreciated in advance.

Cheers
Idom

---

### Post by hostilejosh on 2009-03-14
I recommend installing ubuntu restricted extras package which makes mp3, flash, dvd's etc work.

---

### Post by idom on 2009-03-14
> **hostilejosh said:**
> I recommend installing ubuntu restricted extras package which makes mp3, flash, dvd's etc work.


Thanks, However, as I am new let me ask another silly question. How do I do that ? 

And one more thing. mp3 is working in audacious. 
Cheers
Idom

---

### Post by blueridgedog on 2009-03-14
Open a terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gandaran on 2009-03-14
which version of ubuntu are you running?
the flash package from adobe.com only installs on ubuntu 8.04 and above, for older versions download the tar.gz package

---

### Post by ivanvajar on 2009-03-14
This is solved long time ago. You need to post what version of Ubuntu you are running and are you using 32 or 64bit computer. You can find how to make all multimedia running [here]("http://ubuntuforums.org/forumdisplay.php?f=334").

---

### Post by waspinator on 2009-03-14
> **idom said:**
> Thanks, However, as I am new let me ask another silly question. How do I do that ? 

And one more thing. mp3 is working in audacious. 
Cheers
Idom

If you don't want to go though terminal, you could just click Applications-> Add/Remove... and search for "Ubuntu Restricted Extras". Install that and everything should work.

---

### Post by idom on 2009-03-14
> **blueridgedog said:**
> Open a terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

Thanks for the help.

I did run the command and it did not give any errors. However, when I restarted firefox and youtube still gives the same problem. 
I am using ubuntu  -Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
				
and I think I am using 32 bit Toshiba Satellite version. ( 32 bit I am not sure however, as it is pretty old machine, I guess it is 32 bit )

---

### Post by SunnyRabbiera on 2009-03-14
Try removing gnash, it is installed by default in ubuntu as a flash alternative.
Once gnash is removed, it might work.
You try to remove it in synaptic.

---

### Post by idom on 2009-03-14
> **SunnyRabbiera said:**
> Try removing gnash, it is installed by default in ubuntu as a flash alternative.
Once gnash is removed, it might work.
You try to remove it in synaptic.

gnash is not installed on my system. I checked on synaptic and also 
sudo apt-get remove gnash said that it is not installed. 

Regards
Idom

---

### Post by blueridgedog on 2009-03-14
> **idom said:**
> Thanks for the help.

I did run the command and it did not give any errors. However, when I restarted firefox and youtube still gives the same problem. 
I am using ubuntu  -Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
				
and I think I am using 32 bit Toshiba Satellite version. ( 32 bit I am not sure however, as it is pretty old machine, I guess it is 32 bit )

I would reboot just in case there is a firefox process still running.

---

### Post by gandaran on 2009-03-14
two things you have to do to get that flashplguin-nonfree working in ubuntu 8.04
first, apply all system updates
second, that flashplugin-nonfree is outdated or broken, you must first get a new package list before installing it, to fix it remove the flashplugin-nonfree, open synaptic scroll down to flashplugin-nonfree, mark for complete removal and hit the apply button, next click the reload button to get the new package list, now you can reinstall the flashplugin-nonfree, restart firefox, should work, if it wont I will tell you later how to install flash manually.

---

### Post by ivanvajar on 2009-03-15
For Ubuntu 8.04 - 32-Bit:

> sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

---

### Post by jimmyhacker on 2009-03-15
you must click Install Plugin when firefox opens a yellow tab.Select Adobe Flash Player.Wait while it installs.Restart Firefox.

---

### Post by idom on 2009-03-21
> **gandaran said:**
> two things you have to do to get that flashplguin-nonfree working in ubuntu 8.04
first, apply all system updates
second, that flashplugin-nonfree is outdated or broken, you must first get a new package list before installing it, to fix it remove the flashplugin-nonfree, open synaptic scroll down to flashplugin-nonfree, mark for complete removal and hit the apply button, next click the reload button to get the new package list, now you can reinstall the flashplugin-nonfree, restart firefox, should work, if it wont I will tell you later how to install flash manually.


Thanks a lot.Sorry that I could not try this out earlier. I just needed to update the system. Removing and reinstalling flashplugin-nonfree was not required.

---

