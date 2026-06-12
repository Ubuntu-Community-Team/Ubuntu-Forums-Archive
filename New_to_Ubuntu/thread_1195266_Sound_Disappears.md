---
title: "Sound Disappears"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2009-06-23
Hi

When I start my laptop which has Jaunty installed, the sound works fine.  However, during the course of working on the laptop, the sound disappears. When I visit System > Preference > Sound, and try to test, then I get the following messages:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

I am using ALSA.  The only way to get sound working is to restart the laptop.

Any ideas what I should do to troubleshoot.

---

### Post by LewRockwell on 2009-06-23
I have the same thing happen sometimes in Windows and Mac OS X

How many minutes does it take for your sound to disappear?

---

### Post by irv on 2009-06-23
> Could not open audio device for playback. Device is being used by another application.

It sound like you ran an App that is not releasing the Device so it can be used by another App. Make a note of everything you are doing before the sound doesn't work. Maybe you can trouble shoot the problem and see what App is doing this.

---

### Post by arnold.pietersen on 2009-06-23
> **LewRockwell said:**
> I have the same thing happen sometimes in Windows and Mac OS X

How many minutes does it take for your sound to disappear?

Hi LewRockwell

I have not kept track of the time.  Maybe I should start doing it and get some sense if the disappearance of the sound is linked to timeframe.

Thanks

> **irv said:**
> It sound like you ran an App that is not releasing the Device so it can be used by another App. Make a note of everything you are doing before the sound doesn't work. Maybe you can trouble shoot the problem and see what App is doing this.

Hi Irv

I will track what I am doing and check if the sound is still around.

Thanks

---

