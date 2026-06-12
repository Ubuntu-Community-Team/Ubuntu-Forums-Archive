---
title: "Rip CDs to mp3 at 320 kbps"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by h2o4444 on 2009-04-01
Is there anyway to rip CDs to 320 kbps mp3?

I am using Sound Juicer and I am using an external CD/DVD-RW drive because my laptop did not come with one. It seems after an hour of ripping I only get mp3 that are 128 kbps music files.

How do I change that to 320 kbps? Do I need another program that does better than Sound Juicer or do I just change some settings within Sound Juicer.

---

### Post by MrWES on 2009-04-01
> **h2o4444 said:**
> Is there anyway to rip CDs to 320 kbps mp3?

I am using Sound Juicer and I am using an external CD/DVD-RW drive because my laptop did not come with one. It seems after an hour of ripping I only get mp3 that are 128 kbps music files.

How do I change that to 320 kbps? Do I need another program that does better than Sound Juicer or do I just change some settings within Sound Juicer.


You could use ABCDE - A Better CD Encoder and edit the lameopts to rips 320kbps.

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

[http://ubuntuforums.org/showthread.php?t=91318]("http://ubuntuforums.org/showthread.php?t=91318")

Use: LAMEOPTS="-k -h -ms -b320" in the .abcde.conf file


Bill

P.S. GO RED SOXS!

---

### Post by h2o4444 on 2009-04-01
Hi Bill,
 I just installed abcde but I can't find it any where. It's not even in Applications > Sound & Video. Is abcde a command-line only program?
Thanks.

---

### Post by MrWES on 2009-04-01
> **h2o4444 said:**
> Hi Bill,
 I just installed abcde but I can't find it any where. It's not even in Applications > Sound & Video. Is abcde a command-line only program?
Thanks.

Yah it's CLI only. This web page is the best HOWTO on setting it up and editing the .abcde.conf file to meet your needs.

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

You can edit the conf file by hitting alt +F2 and then gedit .abcde.conf

Once you get is configured; put a CD in the drive and from the terminal type: abcde and it will look up the cd and ask you a couple of questions and your off! I run two encoders at same time, which of course makes it faster, by putting 

MAXPROCS=2 

in the .abcde.conf file.

Believe me, once you get it configured you'll love it. Great little program.

Bill

---

### Post by CatKiller on 2009-04-01
> **h2o4444 said:**
> s? Do I need another program that does better than Sound Juicer or do I just change some settings within Sound Juicer.

If you open the Preferences screen, you should see the Edit Profiles button. Use this to edit your MP3 profile. If it isn't clear which part of the GStreamer pipeline you need to change, you should be able to find out about the GStreamer and LAME options with Google (sorry, not at my computer at the moment, so I can't remember what the default MP3 profile looks like).

---

### Post by billgoldberg on 2009-04-01
I used RipperX to rip some cd's, very easy to use.

I'm on windows 7 now so I can't check if it supports 320kbps ripping but I seem to remember it does.

Off course, if you want quality, you rip to FLAC.

---

### Post by Yashiro on 2009-04-01
For Sound juicer make sure you've installed ubuntu-restricted-extras (or just the lame,mp3, and mux libs).

Then just edit the mp3 profile string to 320kbps.
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=320 ! id3v2mux

or use VBR
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

There are other apps as suggested. Abcde is terminal based and very handy.
Grip is fairly old but very reliable with regards to quality and complete tagging.

---

### Post by hyper_ch on 2009-04-01
k3b, soundconverter...

---

### Post by logos34 on 2009-04-02
> **h2o4444 said:**
> Is there anyway to rip CDs to 320 kbps mp3?

320 CBR is a complete waste of space for no discernible quality difference.  If you must have the best Cd quality lossy setting, use VBR -V 0 (~245kbps nominal rate).  

> 
[ Best quality: "archiving" -b 320.]("http://wiki.hydrogenaudio.org/index.php?title=Lame#Best_quality:_.22archiving.22")
This is the strongest setting for MP3, with the lowest risk of artifacts. With the exception of a few situations, quality is rarely better than the highest VBR profiles described below. However, 'archiving' music using a lossy format like MP3 is never recommended – no matter how transparent the resulting files might sound. The alternative is to use Lossless formats like WavPack, FLAC etc. that allow true archiving, bit for bit like on the original CD.

So, for Sound-Juicer, do like Yashiro suggested above, but use this gstreamer pipeline:

> audio/x-raw-int,rate=44100,channels=2  !  lame name=enc mode=1 vbr=4 vbr-quality=0 ! id3v2mux

mode=1 --> joint-stereo
vbr=4 --> 'vbr-new'
vbr-quality=0 --> -V 0, best setting

---

### Post by hyper_ch on 2009-04-02
> **logos34 said:**
> 320 CBR is a complete waste of space for no discernible quality difference.  If you must have the best Cd quality lossy setting, use VBR -V 0 (~245kbps nominal rate).  


diskspace is cheap... that's why I use lossless flac nowadays...

---

### Post by anjilslaire on 2009-04-02
KAudio Creator lets you adjust the bitrate as well, too

---

### Post by logos34 on 2009-04-02
> **hyper_ch said:**
> diskspace is cheap... that's why I use lossless flac nowadays...

yeah, the price per gb keeps going down, making it tempting to create lossless archive images of every cd.  (or at the very least, save a lossless copy to DVD_+_R, as I was doing until recently).

---

### Post by h2o4444 on 2009-04-02
Thank you all for helping me. I think I'm going to do what Yashiro said and use
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=320 ! id3v2mux 
in Sound Juicer.

To me it's the easiest way to solve my problem. Learning abcde is too time consuming for me since I'm a newb. Here I just copy and paste a code and everything works.

I don't mind using CVR of 320 kbps because I've been ripping all of my CDs, and my Dad's, using Windows Media Player to 320 kbps mp3s for the longest time before I turned to Ubuntu.

So I want to thank everyone again for your help. I learned a lot!

---

### Post by MrWES on 2009-04-02
> **h2o4444 said:**
> Learning abcde is too time consuming for me since I'm a newb. Here I just copy and paste a code and everything works.

Sigh....:p

---

### Post by gn2 on 2009-04-02
I use Grip.

It can be set to automatically rip, encode, name, tag and eject.

All you need to do is put the CD in and Grip does the rest.

---

### Post by h2o4444 on 2009-04-02
Is there a tutorial on how to use Grip? I installed it but it looked too complicated, thus I didn't try to figure out if I could rip CDs as 320 kbps mp3's.

---

### Post by Steve_G on 2009-04-02
I also use Ripper X. Once you've worked out the configuration settings it works a treat.

I got Sound Juicer to rip at 320 by following an old thread but couldn't work out how to change the bit rate from the default of 128 to, say, 192. I've also tried Grip but couldn't get on with it.

---

### Post by gn2 on 2009-04-02
Open Grip, Config > Encode > Encoder, select Lame, then in Options enter 320 for the Encoding bitrate value.

---

### Post by logos34 on 2009-04-02
> **h2o4444 said:**
> Is there a tutorial on how to use Grip?

the official page is probably the best (but still leaves sth to be desired).

[http://www.nostatic.org/grip/doc/index.html](http://www.nostatic.org/grip/doc/index.html)

grip is a excellent little ripper, but with abcde and Eac around it's not used a lot.  The project is barely maintained anywmore...

---

### Post by andrew.46 on 2009-04-02
Hi logos,

> **logos34 said:**
> grip is a excellent little ripper, but with abcde and Eac around it's not used a lot.  The project is barely maintained anywmore...

Mind you the abcde project looks a little quiet now as well. There is an [svn repository now]("http://code.google.com/p/abcde/") but no meaningful action for quite some time.

Andrew

---

### Post by andrew.46 on 2009-04-02
Hi MrWES,

> **MrWES said:**
> Sigh....:p

Reminded me a little of my favourite Simpson's moment:

> 
**Lisa:** I'm about to read you a classic tale of terror by Edgar Allen Poe.
**Bart:** Wait a minute! That's a schoolbook!
**Lisa:** Don't worry Bart, you won't learn anything.


Apologies to h2o4444 :-).

Andrew

---

### Post by logos34 on 2009-04-02
> **andrew.46 said:**
> Hi logos,



Mind you the abcde project looks a little quiet now as well. There is an [svn repository now]("http://code.google.com/p/abcde/") but no meaningful action for quite some time.
 
yeah, I guess I phrased that wrong...What I meant was, with other rippers drawing users, it is less likely that any given older app like grip will maintained beyond what amounts to life support.

---

### Post by steina4 on 2009-04-19
> **Yashiro said:**
> For Sound juicer make sure you've installed ubuntu-restricted-extras (or just the lame,mp3, and mux libs).

Then just edit the mp3 profile string to 320kbps.


or use VBR


There are other apps as suggested. Abcde is terminal based and very handy.
Grip is fairly old but very reliable with regards to quality and complete tagging.

Thanks you so much... that worked just fine for me.

---

### Post by starcannon on 2009-04-19
> **billgoldberg said:**
> I used RipperX to rip some cd's, very easy to use.

I'm on windows 7 now so I can't check if it supports 320kbps ripping but I seem to remember it does.

Off course, if you want quality, you rip to FLAC.

+1 to ripperX and you are correct, it has 320k as a menu option, so no flags to do, just point and click.

---

### Post by DJonsson2008 on 2009-04-20
Perhaps its just a coincidence but I've found that 320 Mp3 seems to skip less when played on an MP3 CD on my CD player, in fact 320 tracks will not skip when 192 and other rates skip on the same disc. 

Flac is beautiful but since most of my listening is on CDr and CDRW disks, 320 MP3 seems the most reasonable way to go.

If I had a Flac enabled DVD or CD device that would be great but I don't know if such a thing exists.

---

