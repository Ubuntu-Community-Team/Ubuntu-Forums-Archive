---
title: "VOB problems"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by kleth on 2009-09-08
I am moving away from Windows, thus two things are holding me back
1. Nero Vision.
2. DRM'ed music.

The issue I am adressing right here is Nero Vision - There seems to plenty Ubuntu alternatives to this product Smile, Manslide, DeVeDe, KMediafactory, Open Movie Editor and QDVDAuthor which all seems to be very good. 

I dump my DV to a DVD using my DVDRecorder. Then I copy the VOB files to th PC. VLC, Movie Player and Handbrake are able to play/load the VOB files and hence the nature of the VOB files there is no encryption problem.

Now to my problem, all the programs listed are unable to process the VOB files that I have copied to the PC. I have even tried to apply the old windows trick of renaming the extention. What am I doing wrong ? :confused:
I do not want to degrade video quality nor waste time on transcoding the files to any other format.

Oh - I am running the amd64 version of Jaunty

Further more the overlays in the preview zone of the video software, seems not to work that well, but I expect that is due to the Intel performance bug in Jaunty ([http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)).  I tried the Safe/Optimal solution but this did not seem to yield anything.

---

### Post by Hospadar on 2009-09-08
What do you mean by "unable to process"? Do the programs give you error messages (if not, try running them in a terminal)?  To my knowlege VOBs are just mpegs layed out in a specific way.

Please post here any kind of error messages you might be getting.  Are these Vobs ready to be burned to a DVD?

---

### Post by kleth on 2009-09-10
Hello, thank you for your reply.
The only common thing I can identify is that most of the video programs states "get fences failed -1". Is that a query on "electric-fences" ? Elsewise I am unable to identify what package fences is in. On application homes there is no mentioning of fences as a dependency .

Manslide shows an application error "ERR: SCR moves backwards, remultiplex output". So I figure it is not that happy about my VOBs.

SMILE does absolutely nothing and it is like the format within the VOB container is not recognised., but elsewise the application is silent.

Open Movie editor states "ac-tex damaged at 7 5" "Missing Picture start code" "invalid dts/pts combinanion". Which is kind of funny since Nero Vision were fed with the exactly same instance of these VOBs without any fuzz.

I have DeVeDe working with the VOBs but it is horribly slow.

Yes VOBs ought to be just a container for mpeg-2

Seems like I have to content myself with the XP dualboot :( for now

---

### Post by mc4man on 2009-09-10
Really shouldn't take too much to make the .VOB(s) 'acceptable' to your reauthoring app.

Don't know the particulars of what you have but re-multiplexing with transcode should work and not take to long

If you have more than 1 .VOB either do separately or join together first

Ex. with 1 .VOB, that won't be accepted  ( assuming mpeg2 with ac3 audio stream

```
tcextract -i VTS_01_1.VOB -x mpeg2 > VTS_01.M2V
```
```
tcextract -i VTS_01_1.VOB -x ac3 > VTS_01.AC3
```
```
mplex -f 8 -o VTS_01.VOB VTS_01.M2V VTS_01.AC3

```

Another possibility is to just use ffmpeg and don't let it re-encode 

Ex same .VOB

```
ffmpeg -i VTS_01_1.VOB -acodec copy -vcodec copy -target ntsc-dvd 1.mpeg 
```

Edit 
for simple authoring ala DvdShrink I use Varsha, currently checking out dvdwizard

---

### Post by bdalzell on 2009-09-27
Have you tried Avidemuxer?

It is available from the Ubuntu repositories

Also I was able to pull my vob files off of a dvd using the command line program vobcopy.

vobcopy is also available from the Ubuntu repositories,

vobcopy -m 

will list all the titles of the separate vob files on the DVD in your dvd drive and 

vobcopy -n vobtitle

will copy that file to your Desktop

---

