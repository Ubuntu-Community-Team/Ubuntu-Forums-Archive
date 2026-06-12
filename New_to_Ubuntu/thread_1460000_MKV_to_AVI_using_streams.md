---
title: "MKV to AVI using streams"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by satish_j on 2010-04-22
After going through many threads for mkv to avi conversion,i have finally concluded that there is no direct easy way to achieve it.
So,i need help to convert the same by splitting each part of a video file.
Briefly,i have a vid file(mkv) with a size of 1.5GB.I want to convert it to around 700-800 MB avi file.How can i take out the video and audio stream out of the mkv file and then combine them together(not sure,but muxing is the term used for it) again with reduced values for bitrates(so as to achieve reduced resulting filesize).
Any help????

---

### Post by carl4926 on 2010-04-22
Did you look at ffmpeg?

 ```
ffmpeg -i infile.mkv -vcodec copy -acodec copy -y outfile.avi
```

---

### Post by satish_j on 2010-04-22
You have specified vcodec as copy which i suppose will copy the original file video codec(h264),whereas i need xvid codecs of the final output file.
Also,any idea how much time will the mencoder command take to convert a 1.5GB mkv file???
And what about the resolution of final file...will it be same as original HD file???

---

### Post by carl4926 on 2010-04-22
I really can't say
There is a man: [http://ffmpeg.org/ffmpeg-doc.html#SEC5](http://ffmpeg.org/ffmpeg-doc.html#SEC5)

Also in a terminal: man ffmpeg

But it's fairly quick at work from the cli

I don't know if Handbrake will do the job if you prefer a UI

---

### Post by ghostborg on 2010-04-22
Handbrake version 0.93 was the last version to support the avi codec.
Version 0.93 stopped working with Karmic.
You might be able to find repacked versions. 0.94 does not support avi.
You will need to search for a copy of 0.93, I don't think you can download it from the Handbrake site anymore.

I think WinFF might do this.

---

### Post by satish_j on 2010-04-23
Well,after googling for this,I came to know that mkvmergeGui(in windows) can extract the video,audio and subtitles part into separate files--which iam going to try later today..
The question that remains now---How to re-encode the raw video file to divx type and to decrease the resolution and bitrate without susbstantial quality loss in the final avi file???
ANY ANSWERS???

---

### Post by satish_j on 2010-04-24
I have extracted the video and audio files from the mkv file using mkvextract.(The vid file is avi file,though i expected it to be h264).Now,iam not able to successfully use ffmpeg to reduce the resolution of exracted video file to less than 1000
Iam using foll ffmpeg command,but it always gives me the final avi file with same resoltion as original file,even after specifying the reduced values:
```

ffmpeg -i /media/D-Drive/Mkv_files/File1.1080.DivX.AC3_Track1.avi -vcodec copy -vtag xvid -b 800k -an -r 25 -s 640x480 /media/D-Drive/Mkv_files/vid_noAudio.avi

```
Why ffmpeg is not working on resolution??
Requesting for help on this despeartely or any reference to some good forums on Net that may help me..

---

### Post by MrWES on 2010-04-24
> **satish_j said:**
> After going through many threads for mkv to avi conversion,i have finally concluded that there is no direct easy way to achieve it.
So,i need help to convert the same by splitting each part of a video file.
Briefly,i have a vid file(mkv) with a size of 1.5GB.I want to convert it to around 700-800 MB avi file.How can i take out the video and audio stream out of the mkv file and then combine them together(not sure,but muxing is the term used for it) again with reduced values for bitrates(so as to achieve reduced resulting filesize).
Any help????

Here ya go, this is how I convert mkv to mp4 for my PS3 from the command line. I guess you could load the mp4 up in Avidemux and remux it to the 700mb size, or whatever size you wish. 

Command Line Conversion of MKV to MP4

sudo apt-get update && sudo apt-get install gpac mkvtoolnix

{This installs the tools you will use for the conversion.}


$ mkvinfo needles.mkv

{This gives you information about each track in the file so that you can perform the extraction properly (for example: track number 1 is video encoded with AVC/mpeg4 at 23.976 fps; track 2 is AAC audio; track 3 is subtitles in SRT format) Be sure to note the fps for the video track, because you will use this later with MP4Box.}

$ mkvextract tracks needles.mkv 1:needles_video.h264 2:needles_audio.aac 3:needles_subtitles.srt

{This extracts the tracks and names them according to what you specify. Be sure to specify names for the tracks that match the information from mkvinfo}

$ MP4Box -fps 23.976 -add needles_video.h264 -add needles_audio.aac -add needles_subtitles.srt needles_final.mp4

{this tells MP4Box the source material is running at 23.976 fps (change according to fps information from mkvinfo you noted earlier) and to combine your extracted video, audio and subtitles tracks into an mp4 container named "needles_final.mp4"}

*** One after thought, you could use mkvmerge with the  --split (<d[K,M,G]|HH:MM:SS|s> Create a new file after d bytes (KB, MB, GB) or after a specific time.) options to split the mkv first to 700m and then extract each as above and convert to mp4. Just type mkvmerge at the terminal to get a complete list of the syntax required.

---

### Post by satish_j on 2010-04-26
Well thanks MrWes for enlighting about mkvextract for Ubuntu..For the conversion part,i intend to stick to ffmpeg command..
So,if you can suggest the solution for ffmpeg,it will be of much help.
Well,after this post,i dont need to login to XP for extracting the indiviual contents of mkv file...thanks again...

---

### Post by DrDevice on 2010-04-26
> **satish_j said:**
> 
```

ffmpeg -i /media/D-Drive/Mkv_files/File1.1080.DivX.AC3_Track1.avi -vcodec copy -vtag xvid -b 800k -an -r 25 -s 640x480 /media/D-Drive/Mkv_files/vid_noAudio.avi

```
Why ffmpeg is not working on resolution??

Try removing "-vtag xvid" part and change to "-vcodec xvid".  The "-vcodec copy" is telling it to copy the video stream as-is, to hell with your settings. :)  I've never used vtag, so I don't know if that's something you'll need or not.

Also, as mentioned above, try WinFF, it's just a GUI interface for ffmpeg, and comes with a lot of presets that have all the needed settings stored for you.  You can even make your own (but hafta manually edit the preset file before running the program, not hard, but a pain. ;) ).

---

### Post by satish_j on 2010-04-26
> **DrDevice said:**
> Try removing "-vtag xvid" part and change to "-vcodec xvid".
Thanks,that really solved the resolution issue..i have now the final vid file with reduced resolution and now am using foll command to add audio with this vid file to get the final file:
```

ffmpeg -i /media/D-Drive/Mkv_files/vid_noAudio.avi -vcodec copy -i /media/D-Drive/Mkv_files/Audiofile.ac3 -acodec copy FinalFile.avi

``` 
i want to keep audio and video codec same now...so iam using 'copy' above.Pls suggest whether the command is OK???

---

### Post by MrWES on 2010-04-26
> **satish_j said:**
> Well thanks MrWes for enlighting about mkvextract for Ubuntu..For the conversion part,i intend to stick to ffmpeg command..
So,if you can suggest the solution for ffmpeg,it will be of much help.
Well,after this post,i dont need to login to XP for extracting the indiviual contents of mkv file...thanks again...

Why do you want to transcode the file with ffmpeg, when you can just extract the mkv file and put it into an mp4 container without transcoding? Much faster believe me! The process I posted looks time consuming, but it can be done in a matter of minutes, whereas, transcoding with ffmpeg, depending on your machine, will take some time for sure.

Bill

** Never mind, I see you're just copying the vcodec and acodec
*** Oh, and personally, I think the h.264 is superior in quality than xvid

---

### Post by satish_j on 2010-04-27
2 reasons:
<p>1. I want to reduce the size of the final avi file.
   2. My DVD player only supports mpeg4 files</p>
The raw video and audio streams i got from mkvextract are in avi and aac format resp.I know i can put these in avi container,but the size of the final file will be same as that of mkv file(in GBs)..
What iam trying is to convert the avi file i got from mkvextract to same avi format but with reduced bitrate(I know this will reduce the quality,but i have noticed there is not much diff).This final avi file,when combined with audio file will give me avi file(with reduced size),WHICH I SHOULD BE ABLE TO PLAY ON DVD PLAYER..
I have created an avi file with above process,but cannot play it on my DVD player,even though i encoded it with mpeg4 option...The file can be played on PC though..
Any inputs what might be the possible reason of this???

---

### Post by MrWES on 2010-04-27
Like I said in an earlier post, you can split the mkv file into 700mb each with mkvmerge --split and THEN extract each into an mp4 file WITHOUT transcoding OR reducing quality ---- you can't be that with a stick! hehehe....

Bill

** Of course, another after thought. If your DVD player will support vob/mpg files, you can convert the mkv file, without remuxing by using mkv2vob under Wine. I use it all the time. You can either keep the DTS audio source or it will convert it to AC3 for you.

---

### Post by satish_j on 2010-04-28
As i mentioned--reducing the size is also one of my concern.If i split the mkv file,then the combined size of splitted files will be same as original mkv file and if i convert these to vob,i will get file/s with even more size.
I do not see much quality difference after transcoding.I have successfully transcoded an 2GB mkv file to 750 MB avi file,but i cannot play it on my xvid compatible dvd player..
Iam googling now for the possible reasons of the same...

---

### Post by satish_j on 2010-04-29
Solved..:P:P
It was the resolution issue..i transcoded it with 800*600 resolution which,as i came to know,is greater than the standard resolutions accepted for PAL and NTSC systems..
so,re-encoded with 720*576 resolution and the file plays properly on dvd player..
Quality is also very good...
Iam now going to transcode all the big mkv files on my system using this method as iam running out of space on HD..
GREAT UTILITY...FFMPEG!!!!

---

