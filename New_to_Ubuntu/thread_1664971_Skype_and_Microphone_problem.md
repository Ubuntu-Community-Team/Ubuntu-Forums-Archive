---
title: "Skype and Microphone problem"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by taber59602 on 2011-01-11
I've given up for now. I spent all day yesterday tryng to get Skype working, and I failed.

Day before yesterday I downloaded Skype 2.1 beta2 for Linux Ubuntu 8.10+64-bit from the Skype website and installed it on my 64bit HP Pavilion's Kubuntu 10.04 Lucid operating system. Then I tested it out, and everything worked! Right out of the box, so to speak. I could talk, my wife could hear me on her computer using Windows Skype, and I could hear her too. Even the video worked both ways. Life was good. I went to bed.

When I got on my computer yesterday morning there was a notice that an update to Skype awaited me. I dutifully downloaded and installed the update. Since my wife wasn't available just then, however, I didn't test it out right away. I fooled around with my new computer some more - familiarized myself with Amarok which seemed to work fine, and installed Audacity which didn't work fine - but that's another story you probably know anyway.

When my wife came home we tested Skype again. This time the video still worked both ways, and I could hear her, but she could not hear me. I also failed the Echo sound test on Skype repeatedly. I am suspecting there's something wrong with my microphone setup. I rule hardware out because Skype and the microphone work fine under Windows7.

So the changes made between the time it worked and the time it (the microphone) didn't work are 1)the installation of the update and 2)the installation and subsequent complete removal of Audacity. I believe the update made was to the version on Synaptic, and that version has 32-bit dependencies.

Wait, I forgot that along the way I also 3)installed Cheese to do comparison behavior of the microphone. When cheese was brought up my webcam worked fine and I took pictures ok, but when I tried to make a video (which I assume called for the use of the microphone) the web picture darkened and froze. Since it didn't work, I also completely uninstalled that. And wait, I also forgot that the last thing I tried was 4)completely removing Skype and reinstalling the 64bit package from Skype's website. Nothing changed as a result of that.

It looks like I'm not the first user to have problems with Skype and a microphone. Following is my hardware info:

neighbor@hp-pav-kubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  libsdl1.2debian-alsa                 1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
neighbor@hp-pav-kubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
neighbor@hp-pav-kubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
neighbor@hp-pav-kubuntu:~$ 


My hope here is that you can help me get my microphone working again so I can use Skype, and maybe even Cheese, and who knows what else. I guess you should also know that in my frustration I completely removed Skype again. It just pissed me off.

---

### Post by mikewhatever on 2011-01-13
That's very odd. Skype for Linux has not been updated for about a year, and checking the website still shows the same 2.1 beta2 or 2.1.0.81. What version of Skype do you have now, after the update?

---

### Post by taber59602 on 2011-01-13
Odd indeed. As I said, I "completely" removed Skype as my parting act of defiance before finally giving up on the problem the other night, so I can't tell you what the version was at that point. I do know, however, that the update did not come from the Skype website. It came from Synaptic, so I suspect it was upgraded to 2.1.0.81-lubuntu5.

---

### Post by mikewhatever on 2011-01-13
Was removing Skype a satisfactory solution? I suspect that you might have the Canonical's partner repository enabled, and Skype must have been updated from there. If Skype from skype.com worked perfectly, you might want to lock the version in Synaptc. Just select a package, then from the menu up top, Package->Lock Version.

---

### Post by taber59602 on 2011-01-15
Thanks for the tip on locking Skype in the repository. I did that right away so that's just one variable I won't have to contend with.

Progress of a sort today. I wanted to see if I could make my microphone just simply work, and the only application other than Skype I knew of that used a mic was Audacity, so I went to reinstall it. While in Synaptic I noticed I had upgrades available so I checked them out and they were libc-bin, libc-dev-bin,
libc6, libc6-dev, libc6-i386, and liblcms1. (Those are strikingly similar names to the files that were installed with the Skype update from the repository, only those names had "32" in them.) I installed the updates.

I subsequently reinstalled Audacity and with it my microphone worked. Just like it ought to. Yee-ha.

On to reinstalling Skype. After installation, I made a call. The video works both ways, I can hear my wife, she can hear me, yes, EXCEPT...

I sound like Darth Vader to her.

Check this out. It's from the Skype for Linux forum:

[http://forum.skype.com/index.php?showtopic=157841&view=&hl=darth&fromsearch=1](http://forum.skype.com/index.php?showtopic=157841&view=&hl=darth&fromsearch=1)

Does that give you any clue as to how to fix my problem? Obviously, kubuntu and fedora are a little different, and I'm pretty uncomfortable in the "try this-try that" mode, so I'm hoping you can employ a depth of knowledge I don't have to work this out. I appreciate your help.

---

### Post by sdowney717 on 2011-01-15
have you looked at sound preferences for the microphone?
click the speaker icon way up top.
you can unmute and set the levels. Here it shows my webcam.
I can record a video with sound using cheese.

---

### Post by taber59602 on 2011-01-15
My mixer settings are fine I believe. The mic works fine in Auacity now, remember, and playback in Audacity is normal. And at least it picks up sound in Skype now, which it didn't seem to before. But when it is played back my voice sounds like Darth Vader.

Did you check out the link I referenced in my previous post? Here it is again:


[http://forum.skype.com/index.php?sho...h&fromsearch=1](http://forum.skype.com/index.php?sho...h&fromsearch=1)



They appear to be discussing my problem, only in Fedora. Their solution involves PulseAudio (which I don't know anything about). There are also a couple other threads on that Skype for Linux forum that discuss Skype and microphones. I was hoping that discussion would lead you to the solution to my problem in Kubuntu

---

