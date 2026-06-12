---
title: "dvd to mp3?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by wiab4355 on 2009-05-17
Hello

I record a lot of radio programmes with my Sony Freeview HDD recorder, transfer 2 hours or so to a DVD, then encode them, using Tmpgenc, from dvd files to mp3 files (not at great quality, I only play them in the car). Is there a Linux program that will let me do this? I don't mind using a few programmes if neccessary (although Tmpgenc would rip and then encode in one go).

---

### Post by blueridgedog on 2009-05-17
What is on the DVD when you make it? In other words, what is the format of the source material that needs to be converted to mp3?

---

### Post by wiab4355 on 2009-05-17
the usual, I suppose - audio_ts & video_ts folders with vob, bup and ifo files in the latter

---

### Post by Terry of Astoria on 2009-05-17
You could try opening the video.ts file in avidemux.
or here are some other proggys I'd suggest. . .
avidemux
vlc - I think under file- convert/save
handbrake
dvd:rip (dvdrip)

---

### Post by blueridgedog on 2009-05-17
> **wiab4355 said:**
> the usual, I suppose - audio_ts & video_ts folders with vob, bup and ifo files in the latter

Take a look at handbrake then....great app.

---

### Post by mprince on 2009-05-18
I vote for Avidemux.

It will let you strip/save the audio off of a VOB file with a couple of menu clicks. Saves right to MP3

*Audio>Encoder* 
Select MP3 (Lame) instead of 'Copy' 
then choose your bitrate

Then:

*Audio>Save*

---

### Post by wiab4355 on 2009-05-18
Thanks everyone

I'll try these suggestions one by one and let you know how I get on!

Ian out

---

### Post by wiab4355 on 2009-05-18
Thanks again

Avidemux worked well, but Tmpgenc detected the number of titles (usually 4 half-hour programmes) and these could be selected as 4 mp3s; I don't know how to do this in Avidemux.

Ian in

---

### Post by andrew.46 on 2009-05-18
Hi,

There is a probably less than popular way which is to use the commandline program Transcode. To give an example with Transcode 1.1.1, the following rips track 1, chapter 3, angle 1 of the Blues Brother DVD to a single mp3 with a single command:

```

transcode -x null,dvd -i /dev/dvd -T 1,3,1 -a 0 -y null,tcaud \
--lame_preset standard -E 44100,16,2 -m $HOME/Desktop/james_brown.mp3

```

This is the cameo of James Brown as the manic preacher, I have converted most of the other cameos for my media player as well :-). Although Transcode permits incredibly detailed choices I am the first to admit it is not for the faint-hearted and possibly not the best tool for the purpose you have mentioned. But I throw it in here with all of the other suggestions in case someone is interested!

All the best,

Andrew

---

### Post by 3rdalbum on 2009-05-18
I've always tended to rip the DVD using Acidrip, and then open the resulting .vob file with Kdenlive, using the "Extract Audio from Clip" function to make a WAVE, and then opening the WAVE in Audacity.

Dvd:Rip used to be able to extract the audio directly but it doesn't work anymore.

---

### Post by andrew.46 on 2009-05-18
Hi 3rdalbum,

> **3rdalbum said:**
> Dvd:Rip used to be able to extract the audio directly but it doesn't work anymore.

Hey I don't feel so bad for waffling on about Transcode in the post above as DVD::Rip is a frontend for Transcode amongst others :-). I don't use DVD::Rip but I can assure you that the commandline Transcode retains the ability that you mention to extract dvd audio directly.

Andrew

---

### Post by wiab4355 on 2009-05-18
3rd album

Acidrip seems to convert the dvd to either an avi or mpeg file - how do I make it just rip the vob files?

---

### Post by NightwishFan on 2009-05-18
You could possibly use ffmpeg to convert a vob file, disable video encoding and output audio only stream as mp3 or wav.

Something like this, use the ffmpeg man page as a reference.

```

ffmpeg -i file.vob -format mp3 -vn -acodec lame

```

---

### Post by wiab4355 on 2009-05-20
nightwishfan

I assume this is in terminal (what a scary proggy - reminds me of a blank dos screen).

Looking at those commands what would go instead of "file" - vts_01_1?

How would I tell ffmpeg where the .vob file is?

What's the ffmpeg "man page"?

TIA

---

### Post by NightwishFan on 2009-05-22
My apologies for not explaining, I had assumed you would find a better solution than mine. My way is very simple if you know the commands though. I would think ffmpeg is the best option if you do not want the video as well, and just audio. Although it can keep the video if you wish.

Regrettably, I am not on Linux right now, so helping you, though not in real time would be very difficult. Though I can say that using the console is handy and should be considered a tool. You should not be afraid to dabble in it a bit, it can help a great deal. If you want basics on the console, I can give you resources, it should not be as hard as dos.

As for the current situation, ffmpeg is a command line encoder. To learn about a command, you can type:
```
man ffmpeg
```
(replace ffmpeg with the command name you want).

Not all programs have a manual page, in which case you can use the simpler built-in help for the command. ie:
```
ffmpeg --help
```

For ripping a DVD, I believe most DVDs should contain a .vob file in the Video_TS folder. You can convert the vob file to formats of your choosing. In ffmpeg, you simply make the input file the .vob, and the output file an mp3 file. It is not hard, though I cannot tell you how offhand (I am not on Linux).

As before the commands you should type will be like the following though **not exactly**:
```

ffmpeg -i /media/cdrom0/VIDEO_TS/file.vob -f mp3 -vn -acodec lame

```

The variables are -i, which is the input file. After -i put a space, and drag and drop the vob file you want to convert into the terminal window. Then -f which forces the format to be mpeg1 audio layer 3 stream. Next is -vn which means do not copy the video stream. Lastly is -acodec which may be lame or libmp3lame, something of the sort. To get the information on your own, about what formats you can use. Type:

```
ffmpeg -formats
```

I can look up this and have it for you tomorrow, though someone may be able to help earlier. This is less complicated then it sounds, it is just I am bad at explaining off the top of my head. You will find doing it yourself it not like programming and should be very intuitive. Good luck and please ask for any help.

---

### Post by Terry of Astoria on 2009-05-22
NightwishFan, thank you for the very good advice about ffmpeg. I have used it before to do converting of formats, and it's always very satisfying to compose and issue a command that just powers through a task. 

   I think I can add here a reminder about how to exit the man page viewer. As NightwishFan said, if you type
 ```
man ffmpeg
```
you will be presented with the man(ual) page for the program. To scroll through it, just use the arrow keys or spacebar, but most importantly (this is sometimes a real bear for folks who are unfamiliar with Linux) please remember to hit
```
q
```
to quit the man page. The man-viewer is a program called less, I think, or more, anyway it's for reading text files, and that's how you exit. You press "q". When I first started using Linux, I was always closing the darn window - you know - "how do I get out of this???!"

---

### Post by wiab4355 on 2009-05-28
Thanks to all, but I think I'm going to stick with Tmpgenc - it's that horrible, cowardly word EASIER!

Ian

---

### Post by NightwishFan on 2009-05-28
Indeed. Good luck.

---

