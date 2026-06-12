---
title: "No audio with QuteCom softphone - HELP!!!"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by zi8 on 2010-07-02
Hi!
This is my first post here, and I'm the beginniest of all people - I  really don't have any computer skills at all...he he

Didn't know whether to use the 64bit- or the ubuntu- prefix on this thread, so this post appears under both prefixes (sorry about that).


I'm using Ubuntu 10.04 (lucid), Kernel Linux 2.6.32-22-generic and I  have an AMD Athlon 64x2 dual core 3600+ processor.

I have just installed VOIP through internetcalls.com.
For Linux users, internetcalls.com recommend Linphone, which I dowloaded  through the Synaptic Package Manager, and configured successfully.

 I managed to make a call in the sense that the landline phone I was  calling too actually ringed, but when lifting the receiver on that phone  there was no audio - neither was there any audio in my headset - I  couldn't even hear the signals going through to the landline phone in my  headset - utter silence.

Thinking there's something wrong with the Linphone/installation, I  uninstalled and reinstalled to no avail.
I gave up, uninstalled Linphone and somebody mentioned to try QuteCom  instead - they've had success with that program in Ubuntu 10.04 - so I  downloaded QuteCom through the SPM, installed and configured it etc,  only to find the exact same symptoms - landline phone ringing, but no  audio whatsoever (in the landline phone receiver or my headset).
I have checked the mic and earphone settings (i.e. my headset) in the  QuteCom program, and they are at almost maximum levels as is the  separate volume control on my headset.
I have also checked the settings in the System-Preferences-Sound: Under  the Output tab, there is a "device" listing ("Output Dummy Stereo"), and  the level is at 100%, and under the Input tab, there's no device listed  at all, so can't set any levels there.
I'm at a total loss here, and beginning to have some serious  self-doubts...:wink:

Any tips?

---

### Post by stoogiebuncho on 2010-07-02
What kind of headset / microphone are you using?  Is it a usb device, or does it plug directly into your sound card?

---

### Post by zi8 on 2010-07-02
Hi,

It plugs straight into the soundcard - not USB-

---

### Post by stoogiebuncho on 2010-07-02
I apologize because I haven't used either of these programs before.  

You said you went to the sound settings in these programs and made sure the volume was turned up.  When you were in the sound settings, was there also a place to choose the input and output devices, or a place where you can set the path to your sound device?

If it's easier, you could just take a screenshot of the settings page and post it here.

It's a bit troubling that you don't have anything listed under "input" in the System-Preferences-Sound area.  Does your sound work for other applications?

---

### Post by zi8 on 2010-07-03
There's no  place to choose the input and output devices, or a place where I can  set the path to any sound device.
I do get sound coming form my speakers OK, like when I play YouTube, radio stations etc - all that works as it should.
Here are some screenshots:
[IMG]http://www.vintafon.com/u1.JPG[/IMG]
[IMG]http://www.vintafon.com/u2..JPG[/IMG]
[IMG]http://www.vintafon.com/u3.JPG[/IMG]
[IMG]http://www.vintafon.com/u4.JPG[/IMG]

Dunno if this is of any help at all.

---

### Post by zi8 on 2010-07-03
Well...that's bizarre, but after I had taken these screenshots, I now don't have any sound coming from the speakers (YouTube etc.).
When I click the Speaker icon at the right hand top of the screen (where there used to be a volume control slider), now there's nothing.
Here's a new screen shot of the Syetem-Preferences-Sound "Hardware" Tab - there used to be a device there (VT1708A Azalia HDAC etc.) - please have a look at pic no. 1 above, but there isn't one there now:
[IMG]http://www.vintafon.com/u5.JPG[/IMG]

I cannot understand what is happening - any help is greatly appreciated!

---

### Post by stoogiebuncho on 2010-07-03
The first thing I would try is to open a terminal window and enter
```
alsamixer
```
That will give you another place to adjust volume, etc.  Sometimes it works better than the volume manager on the panel.  Double check to make sure that your output or input are not muted.

Just in case that doesn't fix it, I did a quick google search for "ubuntu VT1708A Azalia HDAC", and the results indicate that this sound card might have some issues with linux.

I don't know how you feel about getting your hands dirty with something like this, but here are a few threads to start you off.  If you have questions, feel free to post back here and I'll help if I can.

[http://ubuntuforums.org/showthread.php?t=1309046]("http://ubuntuforums.org/showthread.php?t=1309046")

[http://forums.debian.net/viewtopic.php?f=10&t=31058]("http://forums.debian.net/viewtopic.php?f=10&t=31058")

---

