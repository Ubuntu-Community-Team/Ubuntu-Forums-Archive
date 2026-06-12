---
title: "Burning audio CD's won't play."
date: 2009-11-23
forum: New to Ubuntu
---

### Post by suomalainen on 2009-11-23
Ubunteros,

I"m using Brasero to burn 9 audio tracks to a CD. See attached picture. However, after I'm done burning there is a "Lock" over each file <icon> and when I try to play these files (on  CD) in my cars CD player they won't play.

When I use a Ubuntu player like Rhthymbox they will play.

So I guess I'm doing something wrong what is it????

And yes my car CD player works.

---

### Post by Finland_Penguin on 2009-11-23
> **suomalainen said:**
> Ubunteros,

I"m using Brasero to burn 9 audio tracks to a CD. See attached picture. However, after I'm done burning there is a "Lock" over each file <icon> and when I try to play these files (on  CD) in my cars CD player they won't play.

When I use a Ubuntu player like Rhthymbox they will play.

So I guess I'm doing something wrong what is it????

And yes my car CD player works.

Mita kuuluu suomalainen!

This puzzles me... I've burned CDs this way before, will any other sterio play the file or just rythmbox?

---

### Post by suomalainen on 2009-11-23
Morjes Finland_Penguin,

I want to play this CD that I burnt in my CD player in Car. But it won't play.

However, I can hear the music with the Ubuntu audio players but not from my car stero system.

---

### Post by sgosnell on 2009-11-23
What format are the files in?  If they're mp3, then many CD players can't play them.  They need to be in audio CD format for that.  And some CD players won't play CD-R disks, regardless of the format.

---

### Post by Finland_Penguin on 2009-11-23
> **suomalainen said:**
> Morjes Finland_Penguin,

I want to play this CD that I burnt in my CD player in Car. But it won't play.

However, I can hear the music with the Ubuntu audio players but not from my car stero system.

Do you have any other sterios to try it on?

This is strange to me as I have never seen a problem like this one. It may be a problem with the format the files were burned as. (I hope that made sense) Rythmbox may know that format and be able to play it, but your car sterio may not be familliar with it.

---

### Post by suomalainen on 2009-11-23
look attached file.................................

---

### Post by Finland_Penguin on 2009-11-23
> **suomalainen said:**
> look attached file.................................
I do not think that most car cd players will play .wav files...
It should make them something else if I am correct.

Unsure of specifics.

---

### Post by theozzlives on 2009-11-23
You need to burn it as an audio CD, _NOT_ audio files on a CD.

---

### Post by Finland_Penguin on 2009-11-23
> **theozzlives said:**
> You need to burn it as an audio CD, _NOT_ audio files on a CD.
exactly. Most CD players come equiped to read the main CD format, rather that a CDFS disk containing several .wav files.

---

### Post by suomalainen on 2009-11-23
Isn't that what Brasero does? It says it burns them as traditional audio CD....

---

### Post by Finland_Penguin on 2009-11-23
> **suomalainen said:**
> Isn't that what Brasero does? It says it burns them as traditional audio CD....
thats what it sounds like... my linux laptop is broken at the moment so I couldn't check...

I wish I could help more...
 anteeksi

---

### Post by MiCK.ca on 2009-11-23
don't use Brasero myself but..typically. what it appears from your screen-shots is you made a data cd. The original files were *.wavs? IF this were and audio cd it would have *.cda extensions.

having looked at the picture, nautilus says it's a audio cd. just for grins and giggles, do you have all the codecs installed? codecs for converting wav, mp3, ogg, etc.? make sure you have ***libsndfile1*** installed. it's responsible for reading and writing files..including .wavs

---

### Post by suomalainen on 2009-11-23
Yea I got all that. I also use Sound Converter.

Actually, I made a CD of these very same files a few months back and everything worked just great.... Then my brother came along and took my CD so I'm making a new one, or at least trying too.....

---

### Post by aparkes on 2009-11-23
I've used Rythmbox to burn Audio Cd's that work on all my stereos. You just have to make a play-list then right click it, there is an option to burn audio cd.

---

### Post by lhb1142 on 2009-11-23
First of all, I dislike Brasero and I will not use it any more.

If you want to make perfect copies of CDs or you just want to take some audio files you have and want to burn them to data CDs, in my opinion the best program to use is K3b. Yes, it is a KDE program, but so what? It works better than any other burning program I have found in Linux.

Generally when I copy a CD I convert them to FLAC files first using Asunder CD Ripper. This gets the cddb data. Then I burn the CD with K3b; K3b allows you to edit the cddb data if you wish and also to give the disc a name. And it automatically converts whatever format your files are in to CD audio files which will play on any CD player.

K3b can also make an exact copy of any CD; that's the simplest way and the resultant disc will be an exact duplicate of the original.

It works practically every time (once in a very great while there may be a glitch - but replacing the disc usually fixes whatever problem there was) and all the discs I burn (and I just burned four tonight!) play on my Sony SACD/CD player (Model SCD-CE 595 which displays the CD Text), any of my CD portables (one of which, believe it or not, also displays CD Text), and, most importantly, in our car CD players (we have two Honda Civics with the standard CD players). 

I also use a few other encoding programs from time to time; they are Audio CD Extractor (Sound Juicer), Sound Converter, and, most especially, XCFA. I have just about every audio codec I can find downloaded and installed. Everything I use can be found in the Synaptic Package Manager.

But, having now used Ubuntu since May of 2008, both my wife and I burn exclusively with K3b.

Try it. I think you'll like it. ):P

---

### Post by Georgia boy on 2010-01-23
Let me see if I can understand what I have to do. I had burned a CD from mp3's and ogg that I had downloaded doing a data burn to be able to get as many songs as possible on the CD. I can play them on my player in my SUV with no problems at all. But I created one for my sister and she can't play it at all with her CD player in her old truck. So, what is the best way then for creating a CD that she could be able to play? That means changing the MP3's and Ogg over to something else. Just use Brasero and select the "Audio project create a traditional CD" ? Or do I need to do something else so I can fix one for her to listen to? She's gone on a trip right now. I had told her to try playing on her computer and see if it works that way I'd know that it wasn't a bad CD I had given her.

Thanks

Tom

---

### Post by lhb1142 on 2010-01-24
> **Georgia boy said:**
> Let me see if I can understand what I have to do. I had burned a CD from mp3's and ogg that I had downloaded doing a data burn to be able to get as many songs as possible on the CD. I can play them on my player in my SUV with no problems at all. But I created one for my sister and she can't play it at all with her CD player in her old truck. So, what is the best way then for creating a CD that she could be able to play? That means changing the MP3's and Ogg over to something else. Just use Brasero and select the "Audio project create a traditional CD" ? Or do I need to do something else so I can fix one for her to listen to? She's gone on a trip right now. I had told her to try playing on her computer and see if it works that way I'd know that it wasn't a bad CD I had given her.

Thanks

Tom

Dear Tom,

It almost goes without saying that an older CD player will not play MP3- or OGG-formatted music files. You will have to convert whatever files you wish your sister to have to .WAV form and then burn that to CD. Sound Converter is the program I use to do that.

Of course you will be limited in the play time - for example, you might have ten hours of music on your MP3 or OGG CD but you cannot put that much on a traditional CD.

If you wanted your sister to have, say, ten hours of music, you'd have to burn ten CDs.

One solution would be for her to buy a newer, more modern, CD receiver for her truck which would play MP3 and other such music files but that would be fairly expensive and probably not worth it (especially if her current unit is operating fine).

Another solution might be to eschew CD altogether and have her buy a portable music player (iPod or similar; some are available for less than $20.00) and, if her truck's receiver also plays cassettes, she could play the portable music player through it using a cassette adapter (the best one I have found is the one sold at Radio Shack, about $22.00).

The cheapest, though least convenient, means is to burn the large number of CDs she would need. Blank CDs are inexpensive, almost never more than about fifteen cents apiece and often even less (look for "sales"). Of course you have to carry around all of those CDs.

I hope that helps you.

Lawrence

---

### Post by sgosnell on 2010-01-24
You need to burn the CD as an audio CD, not just a data CD containing files.  Older CD players can't handle anything other than a standard audio CD.

---

### Post by mikechant on 2010-01-25
Older audio CD players can be fussy about poor quality discs, and will work best with CDs burned at the lowest possible speeds.
My ancient CD player (1988ish) generally works OK with Verbatim Discs burned at 4x, but can't read various 'no-name' brands at all - the 'silver on both sides' ones seem particularly bad.

---

### Post by mcduck on 2010-01-25
> **sgosnell said:**
> You need to burn the CD as an audio CD, not just a data CD containing files.  Older CD players can't handle anything other than a standard audio CD.

If you look at his screnshot, you'll notice that it _is_ a proper audio-CD.

I agree with mikechant, many players are a pit picky about the quality of the disks they are able to read, and many older players might actually completely fail reading any CD+R or +/- RW disks.

Try burning a disk using some high-quality media (other brnad than what you are curretly using) and a low burn speed.

(and byt the way, don't bother with empty CD's sold specifically for audio use, they are actually lower quality than normal empty CD's are even though they cost more.. :P)

---

### Post by realzippy on 2010-01-25
> **lhb1142 said:**
> First of all, I dislike Brasero and I will not use it any more.

If you want to make perfect copies of CDs or you just want to take some audio files you have and want to burn them to data CDs, in my opinion the best program to use is K3b. Yes, it is a KDE program, but so what? It works better than any other burning program I have found in Linux.

Generally when I copy a CD I convert them to FLAC files first using Asunder CD Ripper. This gets the cddb data. Then I burn the CD with K3b; K3b allows you to edit the cddb data if you wish and also to give the disc a name. And it automatically converts whatever format your files are in to CD audio files which will play on any CD player.

K3b can also make an exact copy of any CD; that's the simplest way and the resultant disc will be an exact duplicate of the original.

It works practically every time (once in a very great while there may be a glitch - but replacing the disc usually fixes whatever problem there was) and all the discs I burn (and I just burned four tonight!) play on my Sony SACD/CD player (Model SCD-CE 595 which displays the CD Text), any of my CD portables (one of which, believe it or not, also displays CD Text), and, most importantly, in our car CD players (we have two Honda Civics with the standard CD players). 

I also use a few other encoding programs from time to time; they are Audio CD Extractor (Sound Juicer), Sound Converter, and, most especially, XCFA. I have just about every audio codec I can find downloaded and installed. Everything I use can be found in the Synaptic Package Manager.

But, having now used Ubuntu since May of 2008, both my wife and I burn exclusively with K3b.

Try it. I think you'll like it. ):P

+1 on that.
Brasero -dunno why- just does not work correctly with some CDdrives.
Try K3B:

**sudo apt-get install k3b**

---

### Post by sgosnell on 2010-01-26
No, that's not an audio CD in the strict sense.  The files are .wav, not .cda.  An audio CD uses only .cda format.  Just because the dialog says "audio CD" doesn't mean it really is one.

---

### Post by mcduck on 2010-01-26
> **sgosnell said:**
> No, that's not an audio CD in the strict sense.  The files are .wav, not .cda.  An audio CD uses only .cda format.  Just because the dialog says "audio CD" doesn't mean it really is one.

Depending on what packages you have installed the file manager may show the audio-CD's contents as .wav files that can be simply drag&dropped to your computer to rip the tracks.

That dosn't mean that the disk itself would contain .wav files. Even the .cda format is an incorrect representation of the contents of an audio-Cd, as they don't actually contain any files. Not .wav, and not .cda.

---

### Post by mikechant on 2010-01-26
> No, that's not an audio CD in the strict sense. The files are .wav, not .cda. An audio CD uses only .cda format. Just because the dialog says "audio CD" doesn't mean it really is one.

Nautilus shows my (genuine shop bought pressed) audio CDs as a bunch of wav files. As per mcduck above, Nautilus presents audio discs in this way for drag & drop etc. convenience.
When you actually do a drag & drop or similar, it uses the virtual filesystem layer gvfsd-cdda to rip the track and present it as a wav file.

---

### Post by peptobismal on 2010-10-13
> **lhb1142 said:**
> If you want to make perfect copies of CDs or you just want to take some audio files you have and want to burn them to data CDs, in my opinion the best program to use is K3b. Yes, it is a KDE program, but so what? It works better than any other burning program I have found in Linux.
If Brasero doesn't burn CDs properly what makes you think that K3B would? Is it not necessarily the programs' fault less the lack of libraries or dependencies needed to finish this. And just because a program is KDE does not mean that it doesn't work on Gnome all the same. You do not need KDE installed at all to use KDE programs just like any other program it's all about dependencies.

I have just recently upgrade like last week to 64bit and yesterday tried to burn some CDs with K3B and Brasero, both. Neither worked properly. I have the CDRDAO installed. When I had 32bit burning CDs was fine. It's just like the programs freeze up upon starting. Brasero actually burned a CD's information to a disc, plus the disc looks like any other burned CD as it does have the two toned color like it burned the whole image to it, but as far as playing the CD, it shows the files as Wave formats, not a single sound to come out of it. So, what am I missing? The TAO dependencies.. what?

Sorry, about bringing an old thread up, but I just don't like the answer "use K3B" which was not / is not the problem in the least. Absolutely worst possible answer I have ever heard of. How this worked for the guy above I have no clue, but I do know that I usually use K3B; however, yesterday it did not work... low and behold Brasero didn't work either? Which leads me to believe that there is a problem with the drivers and/or dependencies used to burn CDs. I will go on a hunt for these and see what I find, unless someone beats me to it.

```
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
```This is the error code I found in Brasero's log. When running in terminal this appears simultaneously with the error message:

```
Sense key: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0e 0x00 0x00 0x00 0x00 0x92 0x02 0x00 0x00 0x00 0x00 0x00 
```So, what I am doing right now is uninstalling "wodim" which is uninstalling K3B and Brasero as well. I will then re-install it and see if that works?

I am now getting a 255 error? From cdrecord in K3B: **[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/90030](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/90030) shown here, fixed?**

---

### Post by lhb1142 on 2010-10-14
[QUOTE=peptobismal;9968107]: If Brasero doesn't burn CDs properly what makes you think that K3B would? Is it not necessarily the programs' fault less the lack of libraries or dependencies needed to finish this. And just because a program is KDE does not mean that it doesn't work on Gnome all the same. You do not need KDE installed at all to use KDE programs just like any other program it's all about dependencies.

I have just recently upgrade like last week to 64bit and yesterday tried to burn some CDs with K3B and Brasero, both. Neither worked properly. I have the CDRDAO installed. When I had 32bit burning CDs was fine. It's just like the programs freeze up upon starting. Brasero actually burned a CD's information to a disc, plus the disc looks like any other burned CD as it does have the two toned color like it burned the whole image to it, but as far as playing the CD, it shows the files as Wave formats, not a single sound to come out of it. So, what am I missing? The TAO dependencies.. what?

Sorry, about bringing an old thread up, but I just don't like the answer "use K3B" which was not / is not the problem in the least. Absolutely worst possible answer I have ever heard of. How this worked for the guy above I have no clue, but I do know that I usually use K3B; however, yesterday it did not work... low and behold Brasero didn't work either? Which leads me to believe that there is a problem with the drivers and/or dependencies used to burn CDs. I will go on a hunt for these and see what I find, unless someone beats me to it.

============================================================================================================================

I never said that if Brasero doesn't work then k3B will. I stated that I do not like Brasero and I much prefer using k3B. The reason for that preference is the much larger array of options k3B offers.

Obviously you are having a major problem with burning in general. That being the case, unless you can identify the particular reason that burning is impossible with your computer, I can only suggest what I have done in the past when I had an 'insoluble' (for me) problem: that is to completely reinstall Ubuntu from a disk.

Sure that takes some time (especially reconfiguring it the way you like) but the time involved will be much less than a lot of 'hair-pulling' trying to figure out what is wrong.

I always back up all of my Documents/Music/Pictures/Videos on external hard drives so reinstalling them is no problem.

Just go into your applications and jot down the programs you have installed (or, if your memory is good enough, just remember what you have).

Then just completely reinstall Ubuntu, get all the updates, reactivate your choice of repositories, reinstall your programs, and, finally, recopy your Documents, etc. to your computer.

You'll have a fresh installation and it will have taken you only a couple of hours (with no 'hair-pulling!').

At that point everything should work perfectly; it always has for me.

Lawrence

---

### Post by El Zoido on 2010-10-14
For some reasons I hactually had a lot of failed burning sessions on linux using Brasero.
Whether this is Braseros fault or the fault of some dependencies I don't know.

I suspected the problem to be my drive, but it tends to work better under windows and I have the same troubles on different computers, too.

Anyway, especially burning DVDs will work only about 60% of the time for me if using Brasero...

---

### Post by Nightstrike2009 on 2010-10-14
Hiya everyone,

I find Brasero to fail with my CD/DVD writers too I use K3B it works fine on mine, if you dont want to use that try Gnomeburner its lightweight and a gnome app, but it succeeded on mine were brasero failed, I dont rate brasero at all its too un-reliable.

---

