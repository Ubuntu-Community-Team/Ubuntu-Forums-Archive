---
title: "Livestreaming and Skype"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by bonde on 2011-04-09
Two things:
**1) Livestreaming:**
Is there some way to install livestreaming software on Ubuntu, like sopcast and the likes?
I use these programmes for watching sports, but so far I've always used Windows Vista for this, and Vista runs really slow on my computer compared to Ubuntu, and I pretty much only use Ubuntu, so would be nice if it would be possible to use Ubuntu for livestreaming as well.

**2) Skype:**
I've tried installing Skype on Ubuntu, and didn't have any problems logging in or anything. And I could see other people who were online, and they could see me. But if trying to have a conversation with them, that doesn't work. The conversation starts, but neither of us can hear anything. So Skype is the second thing I've used Windows Vista for.

---

### Post by stoogiebuncho on 2011-04-11
I believe you can install a sopcast player on Ubuntu.  Check this out: [http://blog.mattrudge.net/2010/04/30/installing-sopcast-on-ubuntu-10-04-lucid-lynx/]("http://blog.mattrudge.net/2010/04/30/installing-sopcast-on-ubuntu-10-04-lucid-lynx/")


As for skype, try going to the options menu, then to the audio or sound area, and look for a checkbox that says something like "Allow Skype to change my volume settings".  It will probably be checked by default.  Uncheck it and see if that solves the problem.

---

### Post by Greydog on 2011-04-11
I've just started using Skype and have been through the whole gamut of problems. 
Just in the past few days, there has been an update to Skype.
I think it has already been added to the repositories....anyway, the first thing that helped me was replacing the command associated with the icon with: sh -c "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"
That fixed issues with video.
Audio was pretty much trial and error with the input/output settings in the "options" menu. Just make sure all of the sliders are not muted and be sure to select the proper input/output settings.
The audio settings are not at all intuitive. You need to set your preferences under the "Sound" settings in System>Preference>Sound
I have mine set as: Input: Internal Audio Analog Stereo
                            Output:  Internal Audio Analog Stereo
I hope this helps

---

