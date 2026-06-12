---
title: "ktimer's command line feature"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Athelas08 on 2010-02-11
Hi!  So, I have this situation where I want KTimer to count down 120 seconds, and then play an audio file.  It seems pretty straight forward, but I can't get the audio file to play!  So, I thought I'd post on the forums and see if anyone had any ideas as to what I was missing.  I have the gnome desktop manager installed as my default and I just installed Ubuntu 9.10 the other day.  The command I entered into KTimer's command line text box is as follows:  mplayer &quot;/path to music file with intentional spaces/sound1.wav&quot;  Mplayer is installed.  Now, when I open a terminal and enter that command, it plays the sound file fine... but when I try to do it in KTimer, it doesn't work.  Just for the fun of it, I tried to enter &quot;firefox&quot; into KTimer's command prompt text field to see if that would work instead, and it did not...  (I also verified that the command does work in a regular terminal)  Anyone have any suggestions?  Thanks!

---

### Post by Nodnarb2012 on 2012-04-14
I know you're original post is over a year old, but I was wondering if you worked out the problem?

I had the exact same desire, to play an audio file on an adjustable delay, and I wanted to be able to loop it.

Up until today, I have never used a command line.  I've spent way too much time reading, trying to learn what was needed to make a successful command.  I finally found your post, and after a few adjustments and tries, it worked great.  

I typed: "mplayer home/brando/etc/etc_etc/file.wav"  Works like a charm!

I originally had problems with spaces in my folder names, but once I fixed those, everything worked like I hoped it would!

Maybe this will help somebody else someday...

---

### Post by Nodnarb2012 on 2012-04-14
* over two years old

---

