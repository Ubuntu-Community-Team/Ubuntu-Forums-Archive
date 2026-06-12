---
title: "Internal microphone and Ubuntu 10.10"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-10-27
I'm having a problem with the internal microphone not working on my  Acer Aspire 3100 laptop running Ubuntu 10.4 and on my Asus netbook 1005hab running Ubuntu  10.10. Both of them work when using the sound recorder programme but not  with Skype, leading me to think it might be the Skype software. 

It might also be  related to the PulseAudio server, since that is all Skype presents as a  sound device option, while I know both computers have HDA  Intel as a device. 

I don't have this problem when  running Windows on these machines and the audio output (i.e. the  internal speakers) seems to function fine in both Ubuntu and Windows on both machines.

I am an almost complete newbie to Ubuntu (and Linux) and would appreciate it if any help is provided in the very simplest of language assuming I don't know any technical terms.

Bob Thomson
Ottawa Canada

---

### Post by ericdn on 2010-10-27
Have you checked your Skype options to make sure the correct microphone and the correct driver are selected for use with Skype?  If your microphone works with other applications in Ubuntu, then it's most likely a problem with Skype.

---

### Post by bthomson100 on 2010-10-31
> **ericdn said:**
> Have you checked your Skype options to make sure the correct microphone and the correct driver are selected for use with Skype?  If your microphone works with other applications in Ubuntu, then it's most likely a problem with Skype.

I think that's the problem. Skype only offers me PulseAudio as a driver and I know that there should be an HDA option. I've tried several version of Skype too and they don't seem to work either.

I suppose it could also be a PulseAudio issue as well but I'm a complete Linux newbie and have no way of knowing how to get past this.

Bob

---

### Post by sagara on 2010-11-05
Googling around a bit i found the following thread: [http://forum.skype.com/index.php?showtopic=579521](http://forum.skype.com/index.php?showtopic=579521)

The fix worked for me.  Essentially you have to disable one of the microphone channels.

Let me know if it works for you.

---

### Post by bthomson100 on 2010-11-05
Thanks Sagara for the tip re muting the left microphone. However it  didn't work. I have the same problem on my EEE 1005HAB with Ubuntu 10.10  and on my Acer Aspire 3104 running Ubuntu 10.4. On the 1005HAB, I  removed PulseAudio and installed gnome-alsamixer and alsa-oss. I can get  a recording now, but there is a lot of static and while it seems to  work OK with the linux sound recorder, anyone I call using Skype can't  hear me properly. That seems like a sound quality issue but it has the  same effect - I CAN'T USE SKYPE WITH UBUNTU!

Bob

---

### Post by SenorHelmut on 2011-01-29
After trolling around the forums for about 10 hours, I finally figured out a way to fix the problem with the microphone not recording in Ubuntu 10.10. I am not sure that it is a permanent fix, but it seems to have solved the problem for me.

This fix is assuming that you are running alsa. I use a HP Pavilion tx2000. When I first installed 10.10 beta, there was no problems with the microphone. During one of the updates *(and I'm not sure which one because I don't use gTalk or empathy for video chat often)* the record volume was changed to 0%. 

**The Temporary Fix**
[LIST=1]
[*]Open Synaptic Package Manager
[*]Search for gnome-alsamixer and click to install
[*]When the download is complete, press Alt-F2 and type "gnome-alsamixer". Click the Open in Terminal and press enter
[*]This will open a window that will give you direct access to all of the sound card operations. Set your Internal volume to max, and adjust Mic Boost and Capture until it sounds right in Sound Recorder. Close the window, and everything should be adjusted properly.  
[*]WARNING: System > Preferences > Sound may show that your microphone volume is unamplified. Changing this setting may cause the recording volume to be maxed out and crackle loudly when recording.
[/LIST]

Hope that helps! This is NOT a permenant fix, and future updates may resolve the actual problems. If that is the case, just follow the above instructions to readjust your recording volume.

---

### Post by vanlindholm on 2011-03-07
Installing the linux alsa driver modules fixed this problem for me (vaio fpcf1 and ubuntu 10.10). Note that a restart is required.

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Hope this works for you..

---

