---
title: "Convert .flac to .mp3 (highest VBR possible)"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-10-06
Hi all,

I know this type of question has been posed numerous times before but I have not found an ideal solution. 

I want to use sound converter, however, the bit rate I get with sound converter is atrociously low. I have set the preferences to:

Format: .mp3
Bitrate Mode: Variable (VBR) - Best quality
Quality: Insanely High

Target bitrate: ~320kbps.

Even with these settings when I am converting the .flac file to a .mp3 file my .mp3 file has a bitrate of 159kbps. 

I have tried with numerous different type of songs from numerous albums that I have ripped before and no matter what it never seems to go beyond 19kbps. Is there anywhere I can adjust the settings so that I am getting a VBR of around 256lbps+.

Thanks!

---

### Post by abhiroopb on 2009-10-06
According to the update at the [SoundKonverter website]("http://soundconverter.berlios.de/"), gstreamer (for some reason) defaults to a max bit-rate of 60kbps. That is why my converted .mp3 files were about 159kbps (just below 160kbps). I installed the latest version of SoundConverter (1.4.4) from the website and now the bitrate of my files are about 240kbps+.

---

### Post by ajgreeny on 2009-10-06
If you are not afraid of the terminal you can do this much quicker, and I find more accurately with ffmpeg.  I have occasionally had strange things happen when I use soundconverter to make an mp3 from large .wav files of 600MB. For some reason it turned a 1hr track into a 2hr track, according to file properties, though the track did appear to play reasonably well.  However, I didn't trust it completely, and therefore boned up on ffmpeg, and that is quick, and I have to say that inmy opinion, much better in all ways.

---

### Post by abhiroopb on 2009-10-06
what is the command?

---

### Post by mikechant on 2009-10-06
Try sound**K**onverter instead of sound**c**onverter. I'm sure I've used it for flac-->mp3 with high bit rates at least once...

---

### Post by ajgreeny on 2009-10-06
> **abhiroopb said:**
> what is the command?
```
ffmpeg -i file.flac -acodec libmp3lame -ab 128k file.mp3
```
where -i file.flac is the input file, -acodec libmp3lame is the audio codec to use, -ab 128k is the audio bitrate, but use your own figure, and file.mp3 is the output file.  What I'm not sure about is getting a VBR, though I'm sure someone else will answer that.

---

### Post by Eisenwinter on 2009-10-06
According to [_this_]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/011573.html"), applying the **-aq 2** option in ffmpeg, generates a VBR file.

I have not tested, I rarely convert files, you'll have to test it yourself.

---

### Post by abhiroopb on 2009-10-06
Thanks I'll have a look at the ffmpeg command.

---

### Post by ajgreeny on 2009-10-06
> **Eisenwinter said:**
> According to [_this_]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/011573.html"), applying the **-aq 2** option in ffmpeg, generates a VBR file.

I have not tested, I rarely convert files, you'll have to test it yourself.
I've just tried this and right clicking on the output file still shows it as a CBR mp3.  I used both ```
ffmpeg -i file.wav -acodec libmp3lame -aq 2 -ab 128k file.mp3
``` and ```
ffmpeg -i file.wav -acodec libmp3lame -aq 2 file.mp3
``` both ended in exactly the same length file and CBR bitrate shown in file properties, but with a bitrate of 160.  I assume that an mp3 encoded as VBR will show that in file properties, but all music files show CBR, which I think they probably are, so now to check, I'm re-encoding one CBR to VBR with soundconverter to see what the output file shows.

OK, I'm back.  The new file from soundconverter is of a different length, 61m 35s, and the original was 52m 27s, according to file preferences, and still CBR.

That does not help me a great deal, and I wonder how else one can find out the encoding bitrate (CBR, VBR, ABR) of any mp3 file.

---

### Post by abhiroopb on 2009-10-06
Does this have anything to do with the fact that gstreamer is using 160kbps as its default. Hence, your conversion tops of at 160kbps.

KDE's SoundKonverter works reasonable well. I am getting similar bit-rates with both Konverter and Converter (after upgrading the later to 1.4.4).

---

### Post by abhiroopb on 2009-10-06
FFmpeg is a video encoder!

---

### Post by nothingspecial on 2009-10-06
> **abhiroopb said:**
> FFmpeg is a video encoder!

aswell.

> FFmpeg is a complete, cross-platform solution to record, convert and stream audio and video.

The first sentence on the ffmpeg home page. Infact ffmpeg is the backend to alot of open and closed source/free and non free audio and video converters.

For starters have a look at [[COLOR="Magenta"]this[/COLOR]]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs")

If you want to go more advanced look at [[COLOR="Magenta"]this[/COLOR]]("http://howto-pages.org/ffmpeg/")

There are loads of ffmpeg tutorials on the web.

---

### Post by CaptainMark on 2009-10-06
I used ffmpeg for the first time the other day and loved it, it can get confusing knowing what command to use especially when doing a task you havent done before so i googled and found out that winFF (its in the standard repos) is a gui setup that you tell it what you want to do and it generates the appropriate command and runs it through ffmpeg for you, brilliant for noobs like me not used to terminal apps

---

### Post by MrWES on 2009-10-06
> **abhiroopb said:**
> Hi all,

I know this type of question has been posed numerous times before but I have not found an ideal solution. 

I want to use sound converter, however, the bit rate I get with sound converter is atrociously low. I have set the preferences to:

Format: .mp3
Bitrate Mode: Variable (VBR) - Best quality
Quality: Insanely High

Target bitrate: ~320kbps.



Even with these settings when I am converting the .flac file to a .mp3 file my .mp3 file has a bitrate of 159kbps. 

I have tried with numerous different type of songs from numerous albums that I have ripped before and no matter what it never seems to go beyond 19kbps. Is there anywhere I can adjust the settings so that I am getting a VBR of around 256lbps+.

Thanks!

Here's a little script I use to convert flac to mp3. Just rename the file flac2mp3.sh and then make it executable with chmod u+x flac2mp3.sh .

Put the file somewhere in your path, ie /usr/bin

Now cd into a directory that contain the flac files and type:
```
flac2mp3.sh *.flac
```

Bill

---

