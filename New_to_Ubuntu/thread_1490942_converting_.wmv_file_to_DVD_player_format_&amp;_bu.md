---
title: "converting .wmv file to DVD player format &amp; burning"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by phubert28 on 2010-05-23
64 bit Ubuntu 10.4
I have a .wmv file I need to burn to DVD in a DVD player-compatible format.

Brasero is asking for a Gstreamer plugin, "mplex" which, though I've located it, I seem not to be able to download.

Is RealPlayer an alternative? And, if so, how? (I've been searching info on RealPlayer 64 bit and so far have information without solutions I can put to use!)

**

My actual requirements:

* convert video formats to DVD-playable formats & burn
* rip & burn mp3 CD's and audio CD's

---

### Post by TeoBigusGeekus on 2010-05-23
> **phubert28 said:**
> 64 bit Ubuntu 10.4
1) convert video formats to DVD-playable formats & burn
2) rip & burn mp3 CD's and audio CD's
1)DeVeDe
2)Brasero or K3b

---

### Post by phubert28 on 2010-05-24
I tried using Brasero, but it required the GStreamer plugin "mplex" and I haven't been able to figure out how to get and install it.

I found a listing of two .tgz files here:

[http://www.openbsd.org/4.5_packages/amd64/gstreamer-mplex-0.10.7.tgz-contents.html](http://www.openbsd.org/4.5_packages/amd64/gstreamer-mplex-0.10.7.tgz-contents.html)

But have no idea what to do with them! (I've downloaded the file)

After I found & downloaded a package for DeVeDe and went to install it, I saw that it was available via Synaptic and used that, instead. Still hanging when it comes to the plugin for Brasero, however.

The DeDeVe package install completed, but I don't see it in the menus! Wonder just where it WENT!

Now if I search in Synaptic, I find nothing... what's up?
WHen I tried to download into the GDebi Package installer, it tells me I HAVE a later version installed... great, but it doesn't appear under the Applications menu!

**

O.K. a reboot showed DeDeVe.

---

### Post by phubert28 on 2010-05-24
Just tried DeVeDe and the conversion said it ran successfully.

I then used Brasero to write the output .iso file to the DVD... none of my players would recognize it as a valid disc. Apparently I selected the wrong option. When, however, I selected "Video project" I again ran into the plugin (mplex) issue again... where do I get it and how do I install it??

Trying Transmageddon but it seems to be doing nothing at all but consuming cpu (Python?)

**

Now installing K3B ... hoping SOMETHING under Linux knows how to transform various video files to DVD player-playable format AND burn the bloody disk (RealPlayer Pro on Windows does the thing end to end - and I have yet to figure out how to get a fully functional RealPlayer running on Linux!)

---

### Post by SlidingHorn on 2010-05-24
> **phubert28 said:**
> I then used Brasero to write the output .iso file to the DVD... none of my players would recognize it as a valid disc. Apparently I selected the wrong option. When, however, I selected "Video project" I again ran into the plugin (mplex) issue again... where do I get it and how do I install it??

Did you burn it as a file or an image?  

[quote=phubert28]Brasero is asking for a Gstreamer plugin, "mplex" which, though I've located it, I seem not to be able to download[/quote]

mplex is a part of mjpegtools, which is in the repos:

```
sudo apt-get install mjpegtools
```

---

### Post by phubert28 on 2010-05-24
Thanks, SlidingHorn, for that info about mplex ... hadn't found THAT anywhere!

I see SO MANY different formats ... in order to simply PLAY on a standard DVD player, what format should my input file have???

I just ran that install, and brasero still doesn't see mplex.

It first says:

Brasero wants to install a file

The following file is required:

. /usr/lib64/gstreamer-0.10/libgstmplex.so

Do you want to search for this now? (Install)

THen:

The file could not be found in any packages.

---

### Post by SlidingHorn on 2010-05-24
hmm...not sure about the mplex thing though.  Standard DVD format is MPEG-2 if I remember correctly

---

### Post by phubert28 on 2010-05-24
Since I know little of the formats, I was probably choosing the wrong one.

---

### Post by mitsumits on 2010-06-13
I have the same problem. Installing the mjpegtool doesn't seem to help. libgstmplex.so is still required.

---

### Post by spin498 on 2010-06-30
It's a bit of a pain, but I went to Ubuntu Software Centre and installed everything relating to GStreamer that wasn't already, it was only 2 extra packages. After that Brasero worked
without asking for the extra libraries.

---

### Post by bumanie on 2010-06-30
I use devede and play them in vlc player > sudo apt-get install vlcAlso, have always found that they work flawlessly in a dvd player, if made with devede - ensure you choose PAL or NTSC depending on where you live. I think PAL is the default.

---

### Post by phubert28 on 2010-06-30
From what I'm seeing, I must have gotten involved in another thread on the same topic because MY problem was that I wanted to WRITE MP3's to CD for the COMPRESSION.

The answer I got from a regular at varlinux.org -AND- in the Ubuntu forums was pretty simple:

Write as  a DATA disc and just burn the MP3 files! End of story.

I suspect when I posted my issue, my intent wasn't clear so I was getting answers unrelated to my need!

---

### Post by Tomei Ningen on 2011-03-06
> **phubert28 said:**
> Thanks, SlidingHorn, for that info about mplex ... hadn't found THAT anywhere!

I see SO MANY different formats ... in order to simply PLAY on a standard DVD player, what format should my input file have???

I just ran that install, and brasero still doesn't see mplex.

It first says:

Brasero wants to install a file

The following file is required:

. /usr/lib64/gstreamer-0.10/libgstmplex.so

Do you want to search for this now? (Install)

THen:

The file could not be found in any packages.


To find out which package contains this file:

$ sudo apt-get install apt-file
$ apt-file libgstmplex.so
gstreamer0.10-plugins-bad-multiverse: /usr/lib/gstreamer-0.10/libgstmplex.so

I had the same problem as the original poster. After installing gstreamer0.10-plugins-bad-multiverse brasero works now.

---

### Post by Tomei Ningen on 2011-03-06
BTW, Brasero had problems dealing with m4v files that were created by HandBrake (says too many dropped frames). So I installed DeVeDe instead and it could handle those m4v files just fine.

Plus DeVeDe has much better GUI than Brasero anyway.

---

### Post by frank cox on 2011-04-27
Brasereo asked for dvdimager and dvdauthor , they were both in Software Manager and then it burned the disk to Mpeg-2 without problems.

---

### Post by jmore9 on 2011-04-27
When i was using windows xp pro i used to record or convert the video/s into mpeg2 then just burn them over to a dvd as files .  The person who watched then put them in i think a progressive scan dvd player and they worked just fine. 

I figured this out by accident by giving this person a dvd with some videos on it and forgot to tell them to watch it on their computer, so they just popped it into the dvd player and watched it.   I was really suprised that it worked like that.

Hope this little info helps in some way

---

### Post by frank cox on 2011-04-27
> **jmore9 said:**
> When i was using windows xp pro i used to record or convert the video/s into mpeg2 then just burn them over to a dvd as files .  The person who watched then put them in i think a progressive scan dvd player and they worked just fine. 

I figured this out by accident by giving this person a dvd with some videos on it and forgot to tell them to watch it on their computer, so they just popped it into the dvd player and watched it.   I was really suprised that it worked like that.

Hope this little info helps in some way

Again, all one has to do is add the programs Brasero asks for from the software manager.
It is due to the law that Linux cannot offer the program to convert to mpeg-2 out of the box, not any shortcoming. If we wanted a windows solution why would we be here?
I tried this for the first time tonight and in less than 10 minutes I was set-up and converting, worked like a champ,

---

### Post by bi3nary on 2012-08-03
I know it's way late, but I was having this problem, and started individually adding gstreamer packages from Synaptic.

First:  gstreamer0.10-ffmpeg-dbg (0.10.10-1)
Problem did not go away.

Second:  ubuntu-restricted-extras
Problem solved.  I'm burning a DVD now.

For information, that package installs the following
cabextract (1.2-3+lenny1build0.10.04.1)
gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu2)
gstreamer0.10-plugins-bad-multiverse (0.10.18-0ubuntu1)
gstreamer0.10-plugins-ugly-multiverse (0.10.14-0ubuntu2)
icedtea-6-plugin (1.2-2ubuntu0.10.04.2)
icedtea6-plugin (6b21.2-2ubuntu0.10.04.2)
libfaac0 (1.26-0.1ubuntu2)
libmp4v2-0 (1:1.6dfsg-0.2ubuntu8)
ttf-mscorefonts-installer (3.2ubuntu0.1)
ubuntu-restricted-extras (39)
unrar (1:3.9.3-1)

---

### Post by wildmanne39 on 2012-08-03
Thanks for sharing. Thread Closed.

---

