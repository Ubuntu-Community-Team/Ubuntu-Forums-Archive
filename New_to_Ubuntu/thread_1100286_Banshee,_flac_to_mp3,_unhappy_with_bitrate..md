---
title: "Banshee, flac to mp3, unhappy with bitrate."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by barbedsaber on 2009-03-19
SOLVED, But I can't find the mark as solved button.

Hey there, I have a bit of a problem with banshee.
A considerable portion of my music collection is in the .flac format, and I love the extra bitrate this gives me. Unfortunately, my Creative Zen Vision:M does not support this great format. This is ok, because banshee automaticly detects this, and converts my flac files as I copy them over (keeping the ones on laptop as flac, and putting mp3's on my player)
unfortunately, it converts them to 128kbps mp3 files, which I find inadequate. Is there some way to tell banshee that the device supports 320kbps mp3, and I want my flac files to use the extra bitrate. (normal mp3's copy fine, with the original bitrate.

thanks
barbedsaber/mynameistux

---

### Post by mc4man on 2009-03-19
You could edit the gstreamer mp3 'profile' or whatever it's called for different lame parameters. ( don't use gtreamer apps so can't advise exactly, there's a recent thread in multimedia & video forum somewhere.

You could also try using soundconverter or soundkonverter. (also install lame

Here are several ways, some scripts if you want to.
You should make sure the mp3's are tagged with whatever way you use.

[http://ubuntuforums.org/showthread.php?t=1096665](http://ubuntuforums.org/showthread.php?t=1096665)

---

### Post by barbedsaber on 2009-03-19
I am familiar with programs such as sound convertor, I was hoping that I could keep just the flac files on my hard drive, (have them convert at the last minute as I transfer them) This is because I am running out of HDD space. (probably becasue of all those flac flies :P )
I will have a look into changing the gstreamer ness.

---

### Post by barbedsaber on 2009-03-19
I could not find anything, anyone have any other ideas?

---

### Post by mc4man on 2009-03-19
Here's some threads about entering new/additional parameters in the gstreamer profile.
I'd read a few and do the edit carefully, remember something about editing in incorrectly can be hard to recover from

[http://ubuntuforums.org/search.php?searchid=56914807](http://ubuntuforums.org/search.php?searchid=56914807)

---

### Post by barbedsaber on 2009-03-20
> **mc4man said:**
> 
[http://ubuntuforums.org/search.php?searchid=56914807](http://ubuntuforums.org/search.php?searchid=56914807)

vBulletin Message
Sorry - no matches. Please try some different terms.

---

### Post by nothingspecial on 2009-03-20
Have a look at this - 

[http://mp3fs.sourceforge.net/](http://mp3fs.sourceforge.net/)

It mounts your flac collection as mp3s but they don`t actually exist until you open them or copy them at which point it converts them on the fly. 

I think it might be exactly what you`re looking for.

You can specify the bit rate in the command used to run it.

---

### Post by mc4man on 2009-03-20
Sorry, seems a link to an ubuntu seach is only good for a short period of time.

Here are some threads

[http://ubuntuforums.org/showthread.php?t=839198&highlight=gstreamer+parameters+lame](http://ubuntuforums.org/showthread.php?t=839198&highlight=gstreamer+parameters+lame)

[http://ubuntuforums.org/showthread.php?t=1069647&highlight=gstreamer+parameters+lame](http://ubuntuforums.org/showthread.php?t=1069647&highlight=gstreamer+parameters+lame)

[http://ubuntuforums.org/showthread.php?t=295698&highlight=gstreamer+parameters+lame](http://ubuntuforums.org/showthread.php?t=295698&highlight=gstreamer+parameters+lame)


command to show current profile, ect
[http://ubuntuforums.org/showthread.php?t=261855&highlight=gstreamer+parameters+lame](http://ubuntuforums.org/showthread.php?t=261855&highlight=gstreamer+parameters+lame)

note that the script i posted in the link (flac to mp3 with tags) pipes directly to lame so no .wav"s are created, takes up very little space (only the size of the .mp3's which can  be deleted after transferring an 'album'

---

### Post by zekopeko on 2009-03-20
what banshee version are you using?

i'm using 1.4.3. there is an option in banshee for giving a different bitrate. right click on your music player icon in banshee and there should be the device properties option. under the properties option there should be the edit button. the rest is self-explanatory.

---

### Post by barbedsaber on 2009-03-20
> **zekopeko said:**
> what banshee version are you using?

i'm using 1.4.3. there is an option in banshee for giving a different bitrate. right click on your music player icon in banshee and there should be the device properties option. under the properties option there should be the edit button. the rest is self-explanatory.

Thank you Thank you Thank you.
This is exactly the sort of thing that I was looking for, and easy soloution from within banshee.
Nothing against all you other folks, it's just that this was so easy to implement.

I really appreciate your help, and thanks again.

Where did the mark as solved button go?

---

### Post by pbhill on 2010-09-03
When I try to change my device encoding by right clicking on the device in the menu, all I have in the drop down list is "Waveform PCM" which is a lossless uncompressed format. Doesn't take too long to fill up the device at this rate. How do I get more options?

---

### Post by pbhill on 2010-09-05
OK, figured it out... I didn't have the proper gstreamer installed.

---

