---
title: "dvd and mpeg.ts files"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by malp on 2011-02-03
Hi
can anyone tell me what I need to make dvds using mpeg.ts files.
The files that are created with my foxsat pvr are mpeg .ts files.
I have no problem burning these as a dvd video using nero10 in windows but ubuntu does not recognise them. This is strange as the operating system of the foxsat pvr is linux based.
I would like to use something simple like nero were you just add the file and then create a dvd that can be used on a dvd player.
Thanks for any help
malc

---

### Post by mcduck on 2011-02-03
You need some tool that's able to convert the files from MPEG Transport Stream into MPEG Program Stream. After that the videos should work just fine (and the conversion is fairly quick to do, and has no effect on quality. It doesn't need to change the compression of the video, only stream type).

I can't tell you exactly what program to use for the task, but as all Ffmpeg, VLC, Xine and Gstreamer are able to handle transport stream, any editor based on one of those should work (at least in theory).

---

### Post by malp on 2011-02-03
hi thanks for the info. I have searched and i am unable to find a converter but as you say some apps will play the file.
I have played the transport stream using gnome mplayer.
What I need is someway to burn a video dvd with the file so it will play on a standard dvd player.
Even in windows the only ways I have found to do this is with nero or roxio.
I know transport stream is very nearly ps and I would have thought that if gnome mplayer can play it there must be someway in ubuntu to convert and write it to a dvd but I have next to no knowledge of linux and ubuntu.
thanks for your help
malc

---

### Post by ron999 on 2011-02-03
> **malp said:**
> 
What I need is someway to burn a video dvd with the file so it will play on a standard dvd player....
 there must be someway in ubuntu to convert and write it to a dvd 

Look in the repo for a program called **DeVeDe**.;)

Otherwise it's not difficult to do the job from command-line instructions if you're interested.
:guitar:

---

### Post by coffeecat on 2011-02-03
> **ron999 said:**
> Look in the repo for a program called **DeVeDe**.;)

+1.

DeVeDe is what you need. It can create dvd menus and prepares an ISO ready for burning to DVD with any burning software. The resultant DVDs will play on Ubuntu, Windows, MacOS and the DVD player sitting near your TV.

---

### Post by malp on 2011-02-04
Hi
For anyone that wants to create a dvd from the mpeg transport stream from a pvr like the foxsat I have finally achieved it with the advise given above but it needs 3 apps and a lot of time.
First use WinFF to convert the ts to dvd mpeg
Then use DeVeDe to create the dvd structure
Then use K3b to burn the dvd to disc.
This works but the convert takes a considerable time.
all the best
malc

---

### Post by coffeecat on 2011-02-04
> **malp said:**
> First use WinFF to convert the ts to dvd mpeg

Are you sure you need this step? DeVeDe should do this for you. DeVeDe is quite happy with TS mpegs from UK terrestrial digital broadcasts as source video.

---

### Post by malp on 2011-02-04
Hi
yes when i tried it with DeVeDe alone it froze and just sat there.
I will try it again when I get time but i happy with the way I am doing it it
thanks
malc

---

### Post by BLTicklemonster on 2012-03-10
Devede and BombonoDVD create some awesome coasters that appear to resemble actual DVDs. 

Well, they play okay on a computer, but once you put them in a real DVD player, they don't work at all.

I'm at a loss as to what to do.

I'm This Close to having a working DVD.

---

### Post by sudodus on 2012-03-10
Would it work to convert the file(s) to mp4 with ffmpeg like this?

```
ffmpeg -i input-file.MTS -sameq output-file.mp4
```

Of course you can also change the frame size and other parameters if necessary, but that may be taken care of by the program writing to the DVD.

---

### Post by BLTicklemonster on 2012-03-10
I think my problem is the program writing the dvd isn't making a dvd that is recognized by the player.

---

