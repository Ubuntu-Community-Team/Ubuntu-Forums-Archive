---
title: "DVD Space issue"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by mrphud on 2010-08-15
Hello There,

So here is the dilemma. I have 24 mp4 videos ~ 110 Mb in size each. The combined size totals ~2.5 Gb. Each file is ~ 50 min in length. I want to burn them all to a DVD, but not in data format. If I try to burn it with Devede or Brasero they space the files by time and not by size. This means I can only put 2 files on one DVD.

Does anyone have suggestions or do I just have to make a data CD and bite the ....?

---

### Post by jtarin on 2010-08-15
> The conversion syntax is MP4Box -add inputFile destinationFile. This option is used to import media from several sources. You can specify up to 20 -add in common MP4Box builds. This process will create the destination file if not existing, and add the track(s) to it. If you wish to erase the destination file, just add the -new option.[Docs HERE]("http://gpac.sourceforge.net/doc_mp4box.php")
[Download]("http://sourceforge.net/projects/gpac/")
You might be able to do it with Imagemajik or the Gimp, but I dont have time to fully research it.

---

### Post by mrphud on 2010-08-15
I'm not really sure what all that means. Are these options for a burner program? Or is this mp4 in general?

Please be a bit more explicit.

---

### Post by jtarin on 2010-08-15
They are suggestions for splicing your files together as one.

---

### Post by jtarin on 2010-08-15
[GnomeBaker]("http://www.ubuntugeek.com/how-to-burn-a-cdsdvds-in-ubuntu-linux.html") is a Gnome CD/DVD burning application.Supports writing a multisession disk.




Edit to add:[Burning CDs and DVDs in Ubuntu]("http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/opensource/0672329093/ch10lev1sec1.html")

Look for X-CdRoast in repositories...another good tool for multi-session .

---

### Post by mrphud on 2010-08-15
OK I will do some tinkering.

Thanks

---

### Post by mrphud on 2010-08-15
Well I suspect I have figured something out.

First, I have tried gpac and successfully joint ~12 mp4 files together. I then tried to burn the concatenated file. I still get the error that the file is too large. But, I think I figured out why.

If a DVD player was able to read at various speeds, there would be no problem. However, DVD players read at a fixed speed. This means that the file, when written to disc, must be recorded such that the files play normally when read at the "standard" speed. I believe this is why the number of files I can burn at a time is limited even though the size is must less than capacity.

Now, armed with this possible explanation I suppose another approach is to convert .mp4 to DVD format and just burn as a data DVD. 

So...What is DVD format for most players and what can I use to convert .mp4 to that format?

thanks

---

### Post by mrphud on 2010-08-15
jtarin,

your location is in asia? You have good english for such a location.

---

### Post by jtarin on 2010-08-16
You know you might be able to convert with [VLC media player]("http://www.videolan.org/vlc/"). I have converted many a movie file with it.

---

### Post by jtarin on 2010-08-16
I better have good English or I will lose my job as an English teacher here in Vladivostok. I'm from Texas. LOL :P

---

### Post by Jimbob0i0 on 2010-08-16
You say you want to burn them to disc but not as data format...

Not quite clear on what you mean here....

If you want to turn them into DVD player standard compatible video for playback in a standard player then you have to bear in mind the length of video that can be put on a DVD as per the specs...

A 4.7GB DVD (assuming we are working with single layer here and not dual layer) will fit 2 hours of video on it - which fits in with what you are seeing.

In that case you will have to burn 12 DVDs with 2 files apiece... but it will allow you to play in any DVD player.

If you want to fit the 24 110 MB files (so approximately 2.5GB) on a single disc you will need to burn them as data... with the proviso that only a PC or a DVD player that is capable of playing mpeg4 files (many are these days) will play your videos.

This has nothing to do with disc speed and is just dependant on the codec used in DVD versus what you have now... mpeg2 is the standard DVD codec but requires much more space than mpeg4 for the same length/quality.

---

