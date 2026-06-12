---
title: "ubuntu 9.10 64 bit Need help in joining mpeg files"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by zerobinary on 2010-04-23
ubuntu 9.10 64 bit 
Need help in joining mpeg files using a gui program.
I have installed handbrake and avidemux.
Need help

---

### Post by kanikilu on 2010-04-23
I'd imagine MPlayer can accomplish this, but I've never really had the need to do that, so am not sure exactly how to go about it.

Never really thought of it before, but apparently good ol' **cat** and simple file redirection can do this:

[http://ubuntuforums.org/showthread.php?t=85718](http://ubuntuforums.org/showthread.php?t=85718)

But that's CLI, not GUI.

---

### Post by oldrocker99 on 2010-04-23
For files which end in .001, .002, etc., sometimes QuickPar, and sometimes HJSplit both work for me. They are both free and both run perfectly under Wine.

:guitar:

---

### Post by zerobinary on 2010-04-23
The cat command isn't really working.
It did semi-combine the file.
Need some help!
I want to use some gui app

---

### Post by anewguy on 2010-04-23
If these are video version mpg files, you might see if OpenShot Video Editor will work.  User Carlee put me on to it and it works great so far for everything I've needed to do.

Dave ;)

---

### Post by zerobinary on 2010-04-23
> If these are video version mpg files, you might see if OpenShot Video Editor will work. User Carlee put me on to it and it works great so far for everything I've needed to do.

I have installed OpenShot Video Editor, but I have no idea on how to use it!
Need some help

---

### Post by MrWES on 2010-04-23
[http://manpages.ubuntu.com/manpages/lucid/man1/mpgtx.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/mpgtx.1.html")

I'm sure it's available for Jaunty too.

Bill

---

### Post by zerobinary on 2010-04-23
```
aliceminer@aliceminer-desktop:~/Fleshlight$ mpgtx -j file1.mpg file2.mpg file3.mpg> fleshlight.mpg
Skipped -2 zeroes at start of file
mpgtx: AT EOF - please stop me!
mmm, this file does not start with a pack, offset: -2 
use the desperate_mode switch as the first option -X to search for a header in the whole file!
if you want to force the operation. May yield to an endless loop if no valid header is found!
Does not even begin with a 00 00 01 xx sequence!

No success at all.
file1.mpg is not a valid mpeg file
```
Mpgtx command is not working for me

---

### Post by anewguy on 2010-04-23
Start up Openshot Video Editor

click on the green "+" next to the solid red circle

browse for a video

repeat until all videos are added

The video files you selected will show in the bigger window below those buttons under "Project Files".

Just drag each video from there to the track(s) below.  You can add transitions, titles, etc., 

Then select "Export" (the big red circle, or from the file menu) to save the combined video as you want.


Dave ;)

---

### Post by zerobinary on 2010-04-23
I am missing the plugin for the combined video

---

### Post by bark50 on 2010-04-23
HJSplit has worked for me.  Download the HJSplit for Java .jar file from here:  [http://www.freebyte.com/hjsplit/#java]("http://www.freebyte.com/hjsplit/#java")  Don't download the Linux version; a lot of people have had problems with it.  Once it's downloaded, right-click on the downloaded jar file and select something that says "Open with Java" or something like that.  Also, you'll probably need to rename the movie files you want to join.  So, if you have, for example, movie1.mpg, movie2.mpg, and movie3.mpg, you want to rename them movie.mpg.001, movie.mpg.002, and movie.mpg.003.  That's the only way I've gotten HJSplit to work.

---

### Post by anewguy on 2010-04-23
Start Synaptic Package Manager (System/Administration/Synaptic Package Manager).  Do a search for libxvid - my search returned 3 hits - one is a development library you shouldn't need, but the other 2 - libxvidcore4 and avifile-xvid-plugin - I would install.

I use some avi files via Openshot Video Editor, and all I have installed is the libxvidcore4, but it can't hurt to install both!

Dave ;)

---

### Post by zerobinary on 2010-04-24
I have joined the video together, but the problem is it is missing part.
The total video time should be 15 minutes, but when I join them together there is only 5 min video time.
Moreover, I have checked synaptic package manager that I have installed every missing plugin it asked for.
But it is still not working

---

### Post by alphacrucis2 on 2010-04-24
> **zerobinary said:**
> ubuntu 9.10 64 bit 
Need help in joining mpeg files using a gui program.
I have installed handbrake and avidemux.
Need help

In avidemux you just append them in order after opening the first.

---

### Post by zerobinary on 2010-04-24
> In avidemux you just append them in order after opening the first.

I did, but I cannot find the output file except .idx files and etc...

---

### Post by anewguy on 2010-04-24
If you have libxvidcore4 already installed, then you may also need to look at the avi libs.  I have libavformat52 and libmjpegtools-1.9 installed as well. 

I have edited, combined, stripped out, etc., several versions of mpg files as well as avi and divx (note that avi and divx go hand-in-hand).

If you have the above mentioned 3 libs already installed, and still have trouble, either take a screen shot of the error or write it down and post it back here.

In addition, if you could screen-shot what you have in Openshot video editor and how you are trying to export it, it would also help.

If the trouble is with input to Openshot, please post a screen shot of the error as well.

Dave ;)

---

### Post by anewguy on 2010-04-24
I noticed on one of your screen shots that there is a box about something not being installed, but it is partially hidden by another box, so I cannot tell what the name is.

For the combined video appearing as only 5 minutes - did you drag each of the mpg files down to the timeline?

And finally, what output type are you trying to export the file as?

Thanks
Dave ;)

---

### Post by anewguy on 2010-04-24
Looking through some things on the net, I think I found the solution for your problems in Openshot.

Open Synaptic Package Manager and put libavcodec in the search string.  You should come up with packages including the following:

libavcodec52
libavcodec-extra-52

Make sure BOTH of these are selected, then click apply.

Try Openshot again and try your export.  If that works, then post back if you need help if you are only getting 5 minutes of video again.

Dave ;)

---

### Post by alphacrucis2 on 2010-04-25
> **zerobinary said:**
> I did, but I cannot find the output file except .idx files and etc...

You just do a save As to create the joined file. If you leave the video and audio encoding set to copy it just saves it as is, otherwise you can change the video, audio encoding and container, apply various filters etc, it then effectively does a render when you do the Save As.

---

