---
title: "Video editor better than Cinelerra?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-08-29
I am trying to edit a simple video, just overlay music and add a title. I have been using Cinelerra for most things, but it does not like my new HD camera (Sanyo Xacti HD1010). Kino is impossible to line up audio, Cinelerra crashes all the time, and I haven't see anything else. Any recommendations? I just needs to be simple, nice GUI (unlike cinelerra), and most important work.

Thanks a lot,
Justin

---

### Post by powel212 on 2009-08-29
For linear video editing nothing beats **Avidemux**. It is in the repos.
I love Avidemux. If you shoot a video and just want to cut some parts out, when you are done you can create a new file based on the orriginal without having to re-encode the whole thing so I can take a one hour video, cut out the parts I don't want and just save using "copy" instead of "xvid" and the new file is done in a few seconds instead of a very long time.

And for Non-Linear I use **Kdenlive**. This one works much the same as Premier did a few years ago. Easy to use and very powerful. It is also in the repositories. Just remember when you are rendering the file to choose "lossless" instead of "File Rendering" for your output.

Once the video is done I Use **DeVeDe** to burn an iso and drop it on DVD. DeVeDe is also in the repositories.

I hope that helps.

Powel

---

### Post by Commander_Bob on 2009-08-29
Thanks Kdenlive looks great. Too bad it uses KDE as I'm using Gnome. It actually works though and seems easy to use. Thanks a lot.

---

### Post by celticbhoy on 2009-08-29
Try OpenShot :-

[http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.openshotvideo.com%2F&ei=2_KYStuKOp-5jAecjey6BQ&rct=j&q=openshot&usg=AFQjCNHo_w8YgXv18y9psd_LDOUS-LQAlA](http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.openshotvideo.com%2F&ei=2_KYStuKOp-5jAecjey6BQ&rct=j&q=openshot&usg=AFQjCNHo_w8YgXv18y9psd_LDOUS-LQAlA)

---

### Post by Commander_Bob on 2009-08-29
I am using Kdenlive and it works pretty well. However I am trying to render my project and I am only getting audio, no video. The render only takes about a minute which is odd. Any ideas?

---

### Post by woedend on 2009-08-29
For gnome, try pitivi: [http://www.pitivi.org/wiki/Main_Page](http://www.pitivi.org/wiki/Main_Page)
It's based on gstreamer so make sure to install all of your gstreamer plugins.
It's in the ubuntu repos.
I also did like avidemux a lot...I just had issues getting certain formats to work(for example...I could create AVI files, but they had no sound when using devede or uploading to youtube)

---

### Post by s.fox on 2009-08-29
Hi,

Might I suggest you also try Kino. :)

-Silver Fox

---

### Post by Commander_Bob on 2009-08-29
I used to use Kino, but it's near impossible to line up an audio track perfectly, and it takes forever as you have to render it each time.

I'll try out PiTiVi. It looks like there a lot more editors since I last looked.

Thanks for the suggestions.

---

### Post by SunnyRabbiera on 2009-08-29
> **Commander_Bob said:**
> I used to use Kino, but it's near impossible to line up an audio track perfectly, and it takes forever as you have to render it each time.

I'll try out PiTiVi. It looks like there a lot more editors since I last looked.

Thanks for the suggestions.

Yeh video editing in linux is still primitive.
But both Kdenlive and Pitivi are looking real promising.

---

### Post by jukingeo on 2009-08-31
> **Commander_Bob said:**
> Thanks Kdenlive looks great. Too bad it uses KDE as I'm using Gnome. It actually works though and seems easy to use. Thanks a lot.

That is the big issue with Kdenlive, it works, but ONLY if you have KDE.  It doesn't work for Gnome.

Right now I am looking into the new kid on the block, OpenShot.  Supposedly the creator has had his troubles with video editors in Linux too and is stepping up to the plate.

Up to now I had trouble with just about every video editor except Cinelerra.  This one runs fine, but it is pretty darn difficult to use.  I am basically looking for something like Windows Movie Maker, but with more options.   While WMM does the job, the problem is that you don't have much freedom in editing the audio. 

So I am crossing my fingers for OpenShot.

Geo

---

### Post by telocity on 2009-12-08
I have just tried Cinelerra for the first time.  I only spent a couple of hours reading and then trying to do a simple edit.  Extremely frustrating, I was not able to figure out how to line up the video and audio as they are from separate sources .   I could spend more time with it, but as comparison I have tried a windoze program from Corel and was able in the same time to actually complete a project.  I will try Kdenlive, but may have to return to windoze for working with video.   As a side note I have used audacity in Ubuntu for years now for recording audio for podcast and video.  Does a awesome job, until you try to do a complex edit on audio of more them a hours length, then it hangs often.  Thought it was the computer I was using, but found out recently it does it on variety of PCs.   Just a heads up.

---

### Post by jukingeo on 2010-03-08
> **telocity said:**
> I have just tried Cinelerra for the first time.  I only spent a couple of hours reading and then trying to do a simple edit.  Extremely frustrating, I was not able to figure out how to line up the video and audio as they are from separate sources .

LOL!  Yes, I ran into similar issues.  Supposedly Cinelerra is great once you figure it all out.  There are tutorials out there but I really wanted a program that is quick and easy to use so I can set up simple edits for slideshows and family videos.  Cinelerra is really more production video oriented and has far more features than the average home user would ever use.  But it WOULD be nice to figure it out one day.  I just don't really have too much time right now.

> 
I could spend more time with it, but as comparison I have tried a windoze program from Corel and was able in the same time to actually complete a project.  I will try Kdenlive, but may have to return to windoze for working with video.

Here is the issue with Windows.  You have the free Windows Movie Maker, which sucks at best.  You can't really mix audio (embedded), it has really no real world video file support (vob, flv, etc).  The renaming trick for video camera files does NOT work, so you have to use a lengthy AVI or MPEG converter.

The other option for Windows is to pay $100 or more for a decent editing program.

Enter Linux.  Very powerful programs that are FREE...but don't always work.

Kdenlive is the best bet right now if you have a KDE desktop, but what I am hoping for right now is a program called "Open Shot".  It is right now in it's infancy and there are problems with it, but it is getting better.  Best part is that it works for Gnome.  So I am hoping for this to be the one.

> As a side note I have used audacity in Ubuntu for years now for recording audio for podcast and video.  Does a awesome job, until you try to do a complex edit on audio of more them a hours length, then it hangs often.  Thought it was the computer I was using, but found out recently it does it on variety of PCs.   Just a heads up.

Hmmm, I never really had to edit a BIG file, but I have used the program before.  It reminds me of the program "Soundforge" for Windows.  You remember that one?   I do admit I like Soundforge better than Audacity, but Audacity is getting better and better and MUCH of what you can do.

Geo

---

### Post by anewguy on 2010-03-08
Don't be scared off by KDE stuff - you can have KDE apps running in Gnome with no problem.  When you install a KDE app in Gnome it will normally gather up the dependencies the first time so that all of the needed KDE libs, etc., are installed.  KDE and Gnome co-exist quite peacefully in my experience.  You don't need to switch to the KDE desktop - you can just run the KDE apps in Gnome.

As for the type of editing you want to do - +1 to the "seeking" column.  I have yet to find a video editing program that works simply for me without the video/audio getting off track or some other problems, and I have tried most mentioned here.  Cinelerra is difficult at best to learn - powerful, but a BIG learning curve, and I also had problems with it aborting quite often.

I would assume it's just a matter of time before someone comes up with a Linux-based tool for this that works great every time and works simply.  I would consider tackling such a task from a programming standpoint, but I know *NOTHING* about video files and their "internals".

Good luck!  I'll be watching this thread to see how things work out for you.

Dave ;)

---

### Post by kitschl on 2010-03-08
OpenShot ([http://www.openshotvideo.com]("http://www.openshotvideo.com/")) is the OSS video editor I've had the best experience with.

---

### Post by jukingeo on 2010-03-14
> **kitschl said:**
> OpenShot ([http://www.openshotvideo.com]("http://www.openshotvideo.com/")) is the OSS video editor I've had the best experience with.

Yes, I am aware of Open Shot and had been using it before the holidays.   But I had my share of syncing problems with it.   However, just a few days ago I received a message from the development team that the problem has been fixed.  So I would like to try OpenShot again. 

I only recently been getting back in the loop after a several month hiatus without using Ubuntu as I had a major crash with it that rendered it inoperative.  I didn't want to do a potentially risky install since I have Ubuntu on a triple boot system and I needed my Windows partition for holiday projects.  But now that the holidays are over, I was able to fix Ubuntu...so I will be back to video editing with it shortly.  So I am really HOPING that OpenShot is working properly now.

Geo

---

### Post by Commander_Bob on 2010-03-14
I just tried openshot after upgrading to 9.10 and kdenlive failed to work well. OpenShot worked great for me!

---

### Post by jukingeo on 2010-03-15
> **Commander_Bob said:**
> I just tried openshot after upgrading to 9.10 and kdenlive failed to work well. OpenShot worked great for me!

I just reinstalled the new version of OpenShot right now.  I am hoping that many of the problems have been fixed as I really can't stand Windows Movie Maker (hate hate hate it!!).  While Cinelerra is great, it is just 'too much'. 

After seeing the features that OpenShot offers I know it came in the middle road, much better than WMM, but not as learning curve intensive as Cinelerra.

True there was Kdenlive before OpenShot, but that seems to only work right with the KDE interface.  So hopefully this new version of OpenShot answers the prayers of MANY Gnome users.

I am going to play with the new OpenShot version over the next few days and see how many improvements were made.

Geo

---

