---
title: "No audio with QuteCom softphone - HELP!!!"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by zi8 on 2010-07-02
Hi!
This is my first post here, and I'm the beginniest of all people - I really don't have any computer skills at all...he he


I'm using Ubuntu 10.04 (lucid), Kernel Linux 2.6.32-22-generic and I have an AMD Athlon 64x2 dual core 3600+ processor.

I have just installed VOIP through internetcalls.com.
For Linux users, internetcalls.com recommend Linphone, which I dowloaded through the Synaptic Package Manager, and configured successfully.

 I managed to make a call in the sense that the landline phone I was calling too actually ringed, but when lifting the receiver on that phone there was no audio - neither was there any audio in my headset - I couldn't even hear the signals going through to the landline phone in my headset - utter silence.

Thinking there's something wrong with the Linphone/installation, I uninstalled and reinstalled to no avail.
I gave up, uninstalled Linphone and somebody mentioned to try QuteCom instead - they've had success with that program in Ubuntu 10.04 - so I downloaded QuteCom through the SPM, installed and configured it etc, only to find the exact same symptoms - landline phone ringing, but no audio whatsoever (in the landline phone receiver or my headset).
I have checked the mic and earphone settings (i.e. my headset) in the QuteCom program, and they are at almost maximum levels as is the separate volume control on my headset.
I have also checked the settings in the System-Preferences-Sound: Under the Output tab, there is a "device" listing ("Output Dummy Stereo"), and the level is at 100%, and under the Input tab, there's no device listed at all, so can't set any levels there.
I'm at a total loss here, and beginning to have some serious self-doubts...;)

Any tips?

THANKS!!!

---

### Post by okplayer02 on 2010-07-03
Well seems like there is alot of problems with this package i think it is a bit out of date. According to this thread

[http://ubuntuforums.org/showthread.php?t=1069933](http://ubuntuforums.org/showthread.php?t=1069933)

well you could try ekiga also 
but look at this thread also .

---

### Post by YannBuntu on 2010-07-05
I confirm, Ekiga is best for VoIP.

If you want to do computer-to-computer audio+video calls, I recommend :
- Ekiga (which exists also on Windows)
- Empathy with Telepathy PPA, ubuntu-restricted-extras package and a Jabber account (a Gmail address is ok), this can do audio+video calls with Windows Gtalk users
- Skype which exists also on Windows, but is not open-source

---

