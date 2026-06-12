---
title: "MythTV most basic question ever!  Play local videos!?!"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by casperlingus on 2011-04-21
I am almost embarrassed to be posting on the beginner's forum, because I've been a Linux/Ubuntu guru for 5 years.  But I am completely baffled how to use MythTV for playing files on my local HDD.

I am furious that such a simple task is so ridiculously difficult on such a mature program!  I have googled everything, and come up with lists of menu options that I don't have.  Everything is geared towards the TV tuner, but I don't even have cable.  I just want to play files on my computer!

I was able to run mythtv-setup, and add some storage directories.  There's now a massive list of them in the MythTV setup, but it's all irrelevant since the frontend is oblivious.  Yes, I have both frontend and backend on the same computer.

From inside the frontend, I go to "Media Library", then there's one option for "Watch Recordings" which takes me to a TIVO-esque menu that's completely empty.  I tried going to Utilities/Setup-->Setup-->General and find no indication of how to specify where my files are. 

My frustration with such a simple task is beyond words.  I hope someone can help me out of this hole...

-Casper

---

### Post by bance on 2011-04-22
Mythtv is a digital video recorder/media centre application, it has a rich feature list that is geared towards that. If you simply want to play downloaded/ripped video files you might try another media player mplayer/VLC.

Mythtv does take a bit of fiddling to set up, but it's features make the effort worthwhile.

To get to your problem, you should be using myth-video, a plug-in for mythtv.

You haven't mentioned what version of myth you're using, the current version (0.24) does have storage group support for myth-video, I believe, but this functionality is really for remote front-ends (you don't have to mess about with NFS etc.)

You need to set-up your storage directories in utilities/settings>settings>mediasettings>video settings>general.

Once this is done, you can play-back from media library>watch videos, You have to press 'M' and scan for videos to have your files loaded, so you can see them.

By the way, I seem to remember reading somewhere that you must have at least one capture card defined in order for myth to work. I'm not sure if this is correct.... (I haven't tried it!)

HTH good luck Steve.

PS. the mythtv forums are [_[COLOR=Red]here[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=301").

---

