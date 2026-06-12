---
title: "GUI-based Program to Extract audio tracks from DVD"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by swarup on 2010-10-20
Has anyone seen a gui-based program to extract audio tracks from DVD? I refer to DVD's that have video on them. I have seen various forum posts about complex terminal window procedures, but I need something relatively easy to use and comprehensible. Such software is readily available in Windows, and I've been waiting for several years now for something in Ubuntu. Has anyone seen something like this?

---

### Post by coffee412 on 2010-10-20
> **swarup said:**
> Has anyone seen a gui-based program to extract audio tracks from DVD? I refer to DVD's that have video on them. I have seen various forum posts about complex terminal window procedures, but I need something relatively easy to use and comprehensible. Such software is readily available in Windows, and I've been waiting for several years now for something in Ubuntu. Has anyone seen something like this?

Im assuming that on the dvd is something like a concert or movie with music you want. 

I use vobcopy to rip the dvd and then load it in avidemux and just save the sound that you want. Vobcopy is a command line that is ultra easy to use. But really any dvd ripping software would work - like handbrake.

Anyways, Thats how I do it.

:)

---

### Post by swarup on 2010-10-20
It is actually a series of live lectures given in Sanskrit. I want to be able to listen to the lectures on my mp3 player in my car, or wherever I may be. Each DVD has around 4 lectures on it. I'd like to have it extract the 4 sound tracks has separate wav (or separately) mp3 files.

---

### Post by coffee412 on 2010-10-20
> **swarup said:**
> It is actually a series of live lectures given in Sanskrit. I want to be able to listen to the lectures on my mp3 player in my car, or wherever I may be. Each DVD has around 4 lectures on it. I'd like to have it extract the 4 sound tracks has separate wav (or separately) mp3 files.

Well, Just install vobcopy and in a term window make a directory (mkdir) and then move into it (cd <dir>) and run "vobcopy". Its that easy. When its done just load it into avidemux and save only the sound in pcm format. Then use something like k3b to burn to cd(s).

Thats how I would tackle the problem. Of course, In linux there are about 100 different ways to do it :P.

Good luck,

---

### Post by coffeecat on 2010-10-20
If you want an all-GUI solution, install k9copy from the repository. It's a KDE app so if you're running the standard gnome version of Ubuntu, it will pull in a lot of KDE dependencies.

There are various output options in the main window, including "Audio extraction". If you go to Settings > Configure k9copy > encoders > Audio codecs, there are a number of audio codecs to choose from, including mp3.

If you need to rip an encrypted DVD, you need to install libdvdcss2 from [http://medibuntu.org/](http://medibuntu.org/) .

---

### Post by swarup on 2010-10-20
> **coffeecat said:**
> If you want an all-GUI solution, install k9copy from the repository. It's a KDE app so if you're running the standard gnome version of Ubuntu, it will pull in a lot of KDE dependencies.

There are various output options in the main window, including "Audio extraction". If you go to Settings > Configure k9copy > encoders > Audio codecs, there are a number of audio codecs to choose from, including mp3.

If you need to rip an encrypted DVD, you need to install libdvdcss2 from [http://medibuntu.org/](http://medibuntu.org/) .

Yes, I actually have that app., having downloaded it some time ago for some other work. I have set the audio codec to mp3, as you instructed. But I do not see any option in the main window for "audio extraction". Where is that?

---

### Post by coffeecat on 2010-10-20
Have a look at my screenshot for Maverick. I'll boot into Lucid and make sure the option is there too. In the meantime, what version are you using?

**Edit:** yes, there in Lucid too. See second screenshot.

---

### Post by swarup on 2010-10-20
> **coffeecat said:**
> Have a look at my screenshot for Maverick. I'll boot into Lucid and make sure the option is there too. In the meantime, what version are you using?

I'm actually using 9.04 Jaunty. Is that a problem? Let me see if I have the option you are pointing to.

I've just checked-- the "audio extraction" option is not there in the output window in my version. Only the first three options in your screen, are present in mine. Oops! Guess I'll have to install a newer version. I was going to install Lucid anyway. It should be there in Lucid, shouldn't it?

---

### Post by coffeecat on 2010-10-20
> **swarup said:**
> I've just checked-- the "audio extraction" option is not there in the output window in my version. Only the first three options in your screen, are present in mine. Oops! Guess I'll have to install a newer version. I was going to install Lucid anyway. It should be there in Lucid, shouldn't it?

Have a look at my earlier post. I added a Lucid screenshot, and the audio extract option is there. Just for completion, I'm posting from Karmic now, and it's in karmic too. See screenshot.

It's just as well you are thinking of installing Lucid since Jaunty is just about to go end-of-life (no more support) if it hasn't already.

Other dvd ripping apps you might want to check out, although I don't know whether they do audio extraction, are Acidrip and DVD:RIP. Neither of which are as nice or as usable as k9copy in my opinion.

---

### Post by swarup on 2010-10-20
Thank you for your help :)

---

### Post by coffeecat on 2010-10-25
@swarup, I hope you're still subscribed to this thread because I want to report that I've had an odd/unhappy experience trying to extract audio from a DVD with k9copy in Maverick. I got an error message about ffmpeg and it wouldn't extract. Which is a bit ridiculous because it then went on to rip the whole DVD for me even though it has to use ffmpeg for that as well. I then extracted the audio I wanted using coffee412's (there's a lot of coffee around here! :wink:) suggestion of Avidemux. Which is the first time I've found Avidemux properly useful. Most times I've used it for editing video files, I've lost audio/video sync, but since I only wanted the audio this time it didn't seem to matter. :rolleyes:

Then, when I tried to edit the resultant ac3 audio file with audacity I was treated to another moan about ffmpeg. I know the Ubuntu version of ffmpeg is hobbled in some way, but I've never looked into the details. I'll do some digging.

Not a good morning. :|

---

### Post by swarup on 2010-10-26
@coffeecat: I'm really sorry to hear things did not work out with k9copy. I was really looking forward to using it, and was planning on doing so in the next day or so. I guess I'll have to try Coffee412's method as well. I must say I'm not really looking forward to it, as I always seem to run into snags with such terminal operations, and I'll be needing to do this on thirty DVDs. Would have been nice if there were a straightforward GUI for this work. Oh well, I'll give the vobcopy/avidemux plan a try.

---

### Post by coffeecat on 2010-10-26
> **swarup said:**
>  I must say I'm not really looking forward to it, as I always seem to run into snags with such terminal operations

You don't have to use the terminal. If the DVDs are not encrypted, simply open the .vob files directly in avidemux and save the audio that way. If they save as a codec other than mp3, use SoundConverter (it's in the repos) to convert them.

If the DVDs are encrypted, make sure you have libdvdcss2 installed, rip the whole DVD with k9copy and then use avidemux as above to extract the audio.

An alternative for either encrypted or non-encrypted DVDs is to use VLC. You can extract the audio from individual VOBs and edit them or stitch them together later. This will only work if there is just one audio stream on the DVD. I tried this with a commercial DVD with three language tracks and two commentary tracks. The result was - bewildering! :-s

By the way, just to add to my post of yesterday: after audacity audaciously let me down so badly, I simply did my editing in avidemux by setting the two markers before saving the audio and then converting it to mp3 with SoundConverter.

And I've done some investigation. The reason k9copy was complaining is that it needs ffmpeg instead of mencoder set in the audio codecs section of the configuration window. The problem is that your settings do not 'stick' and it keeps complaining. If you use the wizard, it offers you ffmpeg automatically and then promptly crashes. Bizarrely, I managed to get it to extract audio once with a codec 'copy' rather than a conversion to mp3, but on every subsequent attempt it crashed. It still seems to be reliable for whole DVD ripping and I'll limit myself to that in future. I hope some of the options above will help you.

**Edit:** just to add. You may know this already, but in case you don't you'll find a number of .vob files in the VIDEO_TS folder, each 1024MB except the last. If you have four lectures per DVD you'll probably find that each splits inconveniently between the VOB files. Lecture 2 will continue immediately on from 1, and so on. You may need audacity to split and stitch the extracted audio files into four lectures. So long as the audio is not ac3, you should be OK.

---

### Post by swarup on 2010-10-26
Thanks for the helpful reply. I am going to paste the TS folder of two of the DVDs here as a screenshot for you to see. Each DVD has four lectures on it. And there are only two files of any size in each TS folder, making it appear as you say, that there are probably two lectures in each of these files meaning they would need to be split. Or if it is hard or very time-taking to do, I could just leave them together as a series of two lectures. From seeing the two screenshots, can you tell whether the DVDs are encrypted or not? Or if not, then how would I be able to know this? These are lectures made by a non-profit organization, given in and on the subject of Sanskrit. So my guess is they probably did not encrypt them, although I do not know for sure. After seeing these folders, please let me know which method you think would be the easiest, most straightforward, least likely to give me errors/problems on the way. Thank you!

---

### Post by coffeecat on 2010-10-26
Taking each point in turn:

**Encryption.** You can't tell from the contents of the DVD whether it is encrypted or not. Encryption is an anti-piracy device which is certainly used by the big labels for movies, but whether a non-profit organisation would bother, I don't know. Possibly not. Check Synaptic to see if you have the package libdvdcss2 installed. If you don't and you can play the DVD then it is not encrypted. If you do have libdvdcss2 installed then it's going to be difficult to tell. Best to try what I suggest and see what happens.

**VOB files.** First, you can probably ignore the ~5MB VIDEO_TS.VOB files. They are probably an introductory splash screen or copyright warning or somesuch. But in each you have VTS_01_1.VOB VTS_01_2.VOB and VTS_01_3.VOB files. I think you will find that the four lectures are spread sequentially through all three files with sudden breaks between files 1 and 2, and 2 and 3. You don't notice these breaks when playing normally. If you want to see what's in them, install the player VLC from the repository and play them each in turn. You can 'fast-forward' in VLC with the slider. If you explore each VOB with VLC it will tell you more than I can explain.

**Extraction.** This following is what I would try. Copy the three VOB files to a temporary directory on the hard drive - it'll be easier that way. Open the first with Avidemux. It'll ask you if you want to index it. Answer yes. It will then  tell you that there are several mpeg files and ask whether you want to append them. Answer yes. Once it's done its indexing and stitching, you will have the whole video/audio stream in Avidemux. Try playing a bit. If it plays it's almost certainly not encrypted for I'm fairly sure that Avidemux doesn't use libdvdcss2.

Now search for the beginning and end of the first lecture. Use Edit > Set marker A for the beginning and marker B for the end. You can go as accurate as one frame. Once you've marked off lecture 1, go to Audio > save and you have the audio for your first lecture. Now Edit > Reset edits which will move the markers back to the beginning and end of the stream. Find your beginning and end of the second lecture and mark them as before. Save audio as before and you have your second lecture. Same procedure for 3 and 4.

If you haven't discovered the audio codec for the audio files yet, simply right-click on one > Properties > Audio tab. If it's not mp3 and you want mp3, SoundConverter will do the job.

If Avidemux falls down it could be because the DVD is encrypted. If so, make sure you have libdvdcss2 installed (from the Medibuntu repository) and rip the whole DVD with k9copy. You'll get a VIDEO_TS folder virtually the same as on the original DVD, but you'll now be able to use Avidemux to extract the audio.

Good luck!

---

### Post by swarup on 2010-10-26
Thank you very much. I have to go to work tonite, but within the next two days I'm going to try this, and I'll let you know how it goes.

---

