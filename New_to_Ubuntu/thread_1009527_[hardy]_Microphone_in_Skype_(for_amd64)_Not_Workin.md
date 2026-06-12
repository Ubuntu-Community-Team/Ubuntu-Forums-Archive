---
title: "[hardy] Microphone in Skype (for amd64) Not Working"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-12-12
Hi All,
I installed skype for amd-64 from a deb file from Skype.

I works well:
- I am able to see video and hear sounds from the other end.
- The guy on the other side is able to see my video

MY Problem:
- My microphone doesnt work - I have tried playing around with options in Skype but to no avail - Any help?

Thx
B.

---

### Post by donkyhotay on 2008-12-12
Are other programs able to recognize your microphone? If your uncertain install audacity (it's in the ubuntu repositories) and try recording a brief message. If this doesn't install either check your microphone volume level and confirm it isn't muted. The easiest way (that I know of) to do that is to install alsamixergui (also in the repositories) and use that.

---

### Post by NullHead on 2008-12-12
I agree, check your microphone volume both in skype and in the volume applet in the top left corner of your screen.

---

### Post by markbuntu on 2008-12-12
If your mic is not working, go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If your microphone is acutally working, you can get skype working on Hardy amd64 with this:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

---

### Post by suncoolsu on 2008-12-14
Hi Markbuntu,
I read you exhaustive tutorial on PA.

I tried following all the stuffs only related to PA and did everything on my laptop. Alhtough I had fixed sound without PA.. but with PA things are better.

I am sure my mike is working becuase I am able to record my sound on sound recored in Applications menu.

Now about SKYPE:
After changing all the options in sound Devices of SKYPE after changing Sound In Sound Out and Ringing to Pulse. I am able to hear nothing from the other side neither is my voice going there. Without PA I was able to hear sound from calee side. Now apart from Video Nothing works :( I dont know what happened? I read the SKYPE thread as well - but of no use :(

Pls help

---

### Post by steveneddy on 2008-12-14
On my laptop I must unmute the mics in the volume manager, turn the mic boost all the way up and go to the recording tab and make sure that those mics are turned up.

Hope that this helps.

---

### Post by suncoolsu on 2008-12-14
> **steveneddy said:**
> On my laptop I must unmute the mics in the volume manager, turn the mic boost all the way up 
Hope that this helps.
I think you mean - go to the Speaker icon on the panel right click -> open volume control. In this In the playback tab I dont see any mike.
In the recording tab I see Mike and its all the way up and unmuted. Switches tab has a mention of headphones line out

> and go to the recording tab and make sure that those mics are turned up.

The mike is turned all the way up in the recording tab.

The problem is:
Without pulse audio - My only problem was callee coulnot hear my voice. I could hear the callees voice and video.

After PA and selecting pulse options in SKYPE
I am not able to hear sound from sound from callees side (new problem after PA) and callee cant hear me (old problem exists)

Videos still work fine

Thanks for any help

---

### Post by Swerve1000 on 2008-12-14
Theres issues with Skype and 8.10 right now. 

I would save your time on wait until Skype put some effort in to fix it.

---

### Post by suncoolsu on 2008-12-15
But mine is Hardy :(

I have seen a lot of people running Skype on Hardy without any problems :(

---

### Post by markbuntu on 2008-12-15
Did you go here for help with skype. That is the link from my guide.

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

---

### Post by suncoolsu on 2008-12-16
Should I download Skype-static package from Mediabuntu? I didnt do that. Everything else I did.

OK i will download Skype from Mediabuntu.

Will inform if I run into any problems

---

### Post by suncoolsu on 2008-12-16
Markbuntu,
I have done everything said in your post. Now I have lost video as well in skype in addition to voice of callee and me.

I installed skype-static from medibuntu repository. 

Please help :confused:

---

