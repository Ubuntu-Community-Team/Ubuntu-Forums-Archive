---
title: "Best media player for Ubuntu 10.04"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by msinfo on 2011-06-06
Hello Reader,
Just migrated to Ubuntu from past few days.
One thing annoying me is, I can't get quality playback of videos and audio, which I used to enjoy in Windows7.
VLC, Totem (with Gstreamer) are their but their audio output was messy, fuzzy and on times video rendering was foggy.
I was going to try mplayer and splayer (with wine) but both failed because of corrupt installation error. (already initiated a thread for same).

Is there any other media player which I can use for all kind of video/audio codecs with quality performance.

Waiting for friendly help! :o

---

### Post by SeijiSensei on 2011-06-06
Try installing **smplayer** from the repositories and see if that works for you.

---

### Post by Kromgol on 2011-06-06
If you can't get quality output with VLC for example, there must be a problem with your audio/video configuration. Check it up.

---

### Post by msinfo on 2011-06-06
@SeijiSensei
@Kromgol
Thanks for attending problem.

I fired command for sm player installation, but stucked in terminal with EndlUserLicenceAgreement from where I see OK button but cant move over it, whatever I do. Also now terminal display is hanged and overlayed with other application image.

Also,
How can I check my audio/video configuration. 
Could not find any diagnostic tool apart from Hardware drivers, which is again blank. 
How can I update my audio video drivers as we do in Windows (from CD or internet)

---

### Post by lovinglinux on 2011-06-06
> **msinfo said:**
> @SeijiSensei
@Kromgol
Thanks for attending problem.

I fired command for sm player installation, but stucked in terminal with EndlUserLicenceAgreement from where I see OK button but cant move over it, whatever I do. Also now terminal display is hanged and overlayed with other application image.

Also,
How can I check my audio/video configuration. 
Could not find any diagnostic tool apart from Hardware drivers, which is again blank. 
How can I update my audio video drivers as we do in Windows (from CD or internet)

In the EndlUserLicenceAgreement hit Tab to move to the OK button.

I am a big fan of smplayer. It has better rendering than VLC in my opinion.

Today I started to use [UMPlayer]("http://www.umplayer.com/download/"), which is a fork of SMPlayer with additional features.

---

### Post by msinfo on 2011-06-06
@SeijiSensei
@Kromgol
@lovinglinux
Thanks for attending problem, as it has been solved.

At this moment happy with SMPlayer and exploring it.
But it seems discovering best media player will go on, as new apps are always arriving.

It was good time, interacting with you all.

---

### Post by Grenage on 2011-06-06
My vision couldn't be any better; am I the only one who doesn't see a difference of quality in mplayer/vlc/etc?

---

### Post by Perfect Storm on 2011-06-06
Gnome mplayer is also a good options. Though the version in the repositories is old. The project is continually evolving fast. (and best of all they are open for suggestions and improvement).

[http://code.google.com/p/gnome-mplayer/](http://code.google.com/p/gnome-mplayer/)

---

### Post by mkornig on 2011-06-06
Yes, msinfo, media players and plugins were a problem on my system, too. I believe this is a serious flaw with Ubuntu. Since Ubuntu seems to promote Firefox, I would have expected Ubuntu to install all necessary plugins you need to run video, audio, flash, etc. by default right from the start.

Now, video is fine on my system (at least for the webpages I visit regularly). I still have some problems with flash audios.

Unfortunately, I can't tell you HOW I solved my video problems (I tried several options). Maybe, somebody could tell me how to find out about the plugins installed/used with my browser (Firefox). Then I might be able to tell what worked for me...

---

### Post by Perfect Storm on 2011-06-06
> **mkornig said:**
> Yes, msinfo, media players and plugins were a problem on my system, too. I believe this is a serious flaw with Ubuntu. Since Ubuntu seems to promote Firefox, I would have expected Ubuntu to install all necessary plugins you need to run video, audio, flash, etc. by default right from the start.

Now, video is fine on my system (at least for the webpages I visit regularly). I still have some problems with flash audios.

Unfortunately, I can't tell you HOW I solved my video problems (I tried several options). Maybe, somebody could tell me how to find out about the plugins installed/used with my browser (Firefox). Then I might be able to tell what worked for me...

Perhaps by installing ubuntu-restricted-extra?
or by installing libdvdcss2, wincodecs etc via. [http://medibuntu.org/](http://medibuntu.org/)


The reason they can't include all is boiled down to license, patents etc.

---

### Post by msinfo on 2011-06-06
@Grenage: Ha ha ha ha. Vision! Were you kidding? Bro, I really had playback issues in terms of quality, specially sound. But now all seems fine with SM Player.

@Artificial Intelligence : So is mplayer only option available when it comes to playing multimedia content with various free/non-free formats.

@mkornig: Still no flash content with audio problem has not come. I also let firefox install plugins itself, it worked but after faced lots of failure intially and like you, I also don't know how it (flash) started working.

It was nice informative interaction with you all.

---

### Post by Perfect Storm on 2011-06-06
> **msinfo said:**
> 

@Artificial Intelligence : So is mplayer only option available when it comes to playing multimedia content with various free/non-free formats.


No, there are some alternative, like gstreamer bad/ugly which you can download via the repsitories. VLC have neither problems playing non-free formats either.

But Ubuntu can't put them on the CD/Installation without getting into troubles.
In a perfect world everything would be open and free :P

---

### Post by Grenage on 2011-06-06
> **msinfo said:**
> @Grenage: Ha ha ha ha. Vision! Were you kidding? Bro, I really had playback issues in terms of quality, specially sound. But now all seems fine with SM Player.

No, I'm quite serious. I can generally play 1080-quality files in totem, mplayer, and vlc - and they all play with identical quality.

It's a moot point; since you have what you need.

---

