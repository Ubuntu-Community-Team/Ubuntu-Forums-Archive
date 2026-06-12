---
title: "gizmo project uses 100% CPU during in a call, and call quality is bad"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-18
When a call is in progress using Gizmo5 / Gizmo Project, 100% of the CPU is in use and the voice quality of from my end (my voice) is horrible. 

My current settings:
> 
In Gizmo Project / Preferences /Audio, the Sound System is Alsa. The Input Device and the Output Device are both set to "Default". Echo Cancellation and Automatic Gain Control are both checked on.

In Sound Preferences (System/Preferences/Sound; or Sound Applet on Panel), the Hardware Tab/Profile is set to "Analog Stereo Duplex".When I use Sound Recorder with the above Sound Preferences, there is no problem with my voice quality.

This didn't happen in Ubunu 9.10 on the same computer, so I know that the problem is not a weak/slow computer. On Ubuntu 9.10, the quality of the phone call was very good.




PARTIAL SOLUTION: Changes Gizmo Sound Settings from ALSA to OSS.

---

### Post by hanzj on 2010-05-18
Clarification: When I run the echo test, the man's voice saying "Congratulations, you've successfully made a Gizmo5 call..." clearly. 

But what I say is choppy, when I hear it back.

It's not a problem with my mic/headset. Even the sound effects in the DialPad tab is choppy during the echo test.


When I am speaking to a live person, the other person's voice is clear. But the other person can't hear me well.

---

### Post by hanzj on 2010-05-18
It seems that when I change from Alsa to OSS, then the voice quality is great. But what's the disadvantages to using OSS?

I noticed that when I use OSS, Sound Preferences / Input tab doesn't sense the Input Level.

---

### Post by hanzj on 2010-05-19
My facile solution is to go from ALSA to OSS in the Gizmo Settings. I'll make do with this until Google comes out with a OSS-compatible Google Voice / Gizmo app for Ubuntu.

---

