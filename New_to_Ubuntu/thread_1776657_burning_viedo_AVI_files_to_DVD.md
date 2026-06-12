---
title: "burning viedo AVI files to DVD"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-06-06
I am looking for a way to burn video AVI files to a DVD so that the DVD can then be put into a DVD player (DivX) and watched on a television.    

All help would be appreciated.

---

### Post by GWBouge on 2011-06-06
I use DeVeDe to convert the media into an actual DVD, so you don't have to worry whether or not your DVD/BluRay/Console can handle a certain video format.  It's available in the repo's.

---

### Post by warfacegod on 2011-06-06
+1 for DeVeDe. If you want to try and see if youe DVD player will read the files open Brasero and choose Data Project.

---

### Post by 3xp10r3r|X13 on 2011-06-06
In my opinion K3b is a really neat tool. It doesn't just create DVDs. You can burn next to everything onto a DVD, using this program. Try it out!

By default it's a KDE application, but you can easily install it using the software center or sudo apt-get install k3b.

Here's the link to their home page, so you can have a look at it:

[http://www.k3b.org/](http://www.k3b.org/)

I have to admit, the website looks pretty crappy, but it really does its job quite well :)

---

### Post by rbowen1 on 2011-06-06
When I try to install DeVeDe, I get the following message:

To install DeVeDe DVD/CD Viedo Creator, these items must be removed:
Libav codec library
libavcodec52
Libav file format library
libavformat52
Libav utility library
libavutil50
Libav video postprocessing library
libpostproc51
Libav video scaling library
libswscale0

Two options:  1.   Cancel   2.  Install anyway

What are these 5 Libav items?  What applications are they used?   Could this cause a conflict if I install anyway?

---

### Post by SeijiSensei on 2011-06-06
> **rbowen1 said:**
> I am looking for a way to burn video AVI files to a DVD so that the DVD can then be put into a DVD player (DivX) and watched on a television.

Before you start removing things, let's try an experiment.  Play one of the files from the command prompt with mplayer ("mplayer /path/to/file.avi") and see what codecs were used to encode the video and audio.  If the video was encoded in DivX or XviD, with MP3 audio, you should be able to play them on your DVD player without any additional massaging.  In K3b, choose "New Data Project," then double-click the files from the directory listing in the top frame.  They'll then appear in the bottom frame which represents the contents of the disk to be created.  Click "Burn", then stick the DVD into the player and see what happens.

---

### Post by rbowen1 on 2011-06-06
Installed Mplayer at the command prompt.   Mplayer does not find the file yet an LS shows the file in the home directory.   The AVI file will play OK in Natty Gui.

command line response:

MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing just.avi.
File not found: 'just.avi'
Failed to open just.avi.


Exiting... (End of file)

Seems like I am getting side tracked.   Any one out there know what the libav files are used for and how would I remove them so I can install DeVeDe application?

---

### Post by crispy_420 on 2011-06-06
You did say that you have a DVD player that supports DivX in the intial post right? Then as long as the avi file is in their supported format (most likely basic Xvid/DivX for video and mp3 for audio portion) it should just play. So my suggestion is just to ensure it is the right format then burn as data disc. You may have no need to do all of these conversions and over complicate the process. 

I have had two Phillips DVD players in a row that support DivX out of the box and this has worked for both units. The second one I got to replace the first unit even has a USB port so I can skip burning discs all together. For $50 a unit I can't complain too much not even taking into account they can easily be made region-free to boot.

Take the easy way out before messing with transcoding formats, it may save you many hours of unneeded work.

---

### Post by rbowen1 on 2011-06-07
Got mplayer to work.   mplayer shows:  
VIDEO:  [XVID]  620x320  24bpp  25.000 fps  756.0 kbps (92.3 kbyte/s)

I do not have the K3b burner so I used Brasero to burn the file as a data disc to DVD.  My DivX DVD player does not recognize the disk & shows as unknown.   First Disc coaster 

mplayer shows that the libav files are being used to play the AVI viedo file.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)

I have searched the forums and it appears that DeVeDe has worked fine on older versions of Ubuntu.  This appears to be an issue with Ubuntu  11.04 and  DeVeDe.     Should I give up on DeVeDe and try Tovid?

---

### Post by ron999 on 2011-06-07
> **rbowen1 said:**
>   Should I give up on DeVeDe and try Tovid?
It's up to you.
Have you decided to convert that avi file into a DVD disc that will play on _any_ DVD player?

---

### Post by rbowen1 on 2011-06-07
> **ron999 said:**
> It's up to you.
Have you decided to convert that avi file into a DVD disc that will play on _any_ DVD player?

Yes, I want to convert the avi file into a DVD disc that will play on _any_ DVD player.  

Perhaps I should select the install anyway for DeVeDe.

---

### Post by jtarin on 2011-06-07
> **crispy_420 said:**
> You did say that you have a DVD player that supports DivX in the intial post right? Then as long as the avi file is in their supported format (most likely basic Xvid/DivX for video and mp3 for audio portion) it should just play. So my suggestion is just to ensure it is the right format then burn as data disc. You may have no need to do all of these conversions and over complicate the process. 

I have had two Phillips DVD players in a row that support DivX out of the box and this has worked for both units. The second one I got to replace the first unit even has a USB port so I can skip burning discs all together. For $50 a unit I can't complain too much not even taking into account they can easily be made region-free to boot.

Take the easy way out before messing with transcoding formats, it may save you many hours of unneeded work.I agree. A conversion tool might be what you need instead of a specific burner..

---

### Post by ron999 on 2011-06-07
> **rbowen1 said:**
> 
Perhaps I should select the install anyway for DeVeDe.

Hi
Go with **DeVeDe** if you like.
If it doesn't work out, you can always un-install it and re-install the five packages again.

It's not difficult to do the job without DeVeDe, using command-line instructions.
Start with an avi file and end up with an iso file ready to burn.;)

---

### Post by rbowen1 on 2011-06-07
> **ron999 said:**
> Hi
Go with **DeVeDe** if you like.
If it doesn't work out, you can always un-install it and re-install the five packages again.

It's not difficult to do the job without DeVeDe, using command-line instructions.
Start with an avi file and end up with an iso file ready to burn.;)

Cool Beans Ron999.  I would like command line instructions.   Thanks!

---

### Post by alphacrucis2 on 2011-06-07
> **rbowen1 said:**
> Cool Beans Ron999.  I would like command line instructions.   Thanks!

DeVeDe is a GUI program. 


Edit ignore me. I realise you want to do it using command line rather than use DeVeDe

---

### Post by ron999 on 2011-06-08
> **rbowen1 said:**
> I would like command line instructions.


Hi
To move from **just.avi** to **just.iso** takes three steps.

_First step:-_
Convert the avi file to MPEG-2.

Install the converter program **FFmpeg**:-
```
sudo apt-get install ffmpeg
```

Convert the file using one of these commands:-
Either
```
ffmpeg -i just.avi -target ntsc-dvd just.mpg
```
Or
```
ffmpeg -i just.avi -target pal-dvd just.mpg
```

When it's finished you'll have a new file named **just.mpg**.


_Second step:-_
Create the DVD file structure.

Install the authoring program **dvdauthor**:-
```
sudo apt-get install dvdauthor
```

Create the DVD structure using this command:-
```
dvdauthor -o DVD/ -t just.mpg && dvdauthor -o DVD/ -T
```

When it's finished you'll have a new folder named **DVD** containing AUDIO_TS and VIDEO_TS folders.


_Last step:-_
Create an iso file from the DVD folder.

Install the iso image program **genisoimage**:-
```
sudo apt-get install genisoimage
```

Create the iso file using this command:-
```
genisoimage -dvd-video -v -o just.iso DVD 
```

When it's finished you'll have a new file named **just.iso**.

---

### Post by Mac-ghost-hunter on 2011-06-08
Try KDENLIVE  That is what I use.
 
Mac-Ghost-hunter

---

### Post by rbowen1 on 2011-06-08
[QUOTE=ron999;10915886
_Last step:-_

```
genisoimage -dvd-video -v -o just.iso DVD 
```When it's finished you'll have a new file named **just.iso**.[/QUOTE]


I got this in the terminal and a just.iso file that has 0 bytes:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.11 (Linux)
Scanning DVD
Scanning DVD/AUDIO_TS
Scanning DVD/VIDEO_TS
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for 'DVD/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents


Step 3 did create a directory called DVD that has two directories.   AUDIO_TS  which is empty  and a VIDEO_TS directory that contains 6 files.  1. /DVD/VIDEO_TS/VTS_01_0.BUP 2.  VIDEO_TS/VTS_01_0.IFO  3.  VIDEO_TS/VTS_01_1.VOB  4. VIDEO_TS/VTS_01_2.VOB  4. VIDEO_TS/VTS_01_3.VOB   4.   VIDEO_TS/VTS_01_4.VOB

Any ideas?

---

### Post by ron999 on 2011-06-08
> **rbowen1 said:**
> 
Any ideas?

Hi
I don't know why that's happening.
Maybe step 2 didn't work properly to make a good DVD folder.
It's OK that the AUDIO_TS folder is empty.
But perhaps there should have been more BUP and IFO files created in the VIDEO_TS folder.

Try deleting the **DVD** folder and the **just.iso** file.

Then do step 2 again, but split it into _**2**_ commands.
Like this:-
```
dvdauthor -o DVD/ -t just.mpg
```
Then this:-
```
dvdauthor -o DVD/ -T
```

Then try step 3 again to make the iso file.

---

### Post by rbowen1 on 2011-06-08
[QUOTE=ron999;10917938Then this:-
[CODE]
dvdauthor -o DVD/ -T

First step went Ok but got this in terminal for 2nd step:  dvdauthor -o DVD/ -T

DVDAuthor::dvdauthor, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>

INFO: no default video format, must explicitly specify NTSC or PAL
INFO: dvdauthor creating table of contents
INFO: Scanning DVD/VIDEO_TS/VTS_01_0.IFO
ERR:  no video format specified for VMGM

Ideas?

---

### Post by ron999 on 2011-06-08
> **rbowen1 said:**
> 

DVDAuthor::dvdauthor, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>

INFO: no default video format, must explicitly specify NTSC or PAL
INFO: dvdauthor creating table of contents
INFO: Scanning DVD/VIDEO_TS/VTS_01_0.IFO
ERR:  no video format specified for VMGM

Ideas?

Hi
I'm using dvdauthor v0.6.14.
You're using dvdauthor v0.7.0.

It seems that the newer version uses a different method.

I think that this is the solution:-
Use a text editor to create a file named **video_format**.
In the file, just type one word...
Either:-
**PAL**
Or:-
**NTSC**

Save this **video_format** file in (hidden) folder **./config**.

Then delete the **DVD** folder and try step 2 again.

---

### Post by rbowen1 on 2011-06-08
Having trouble locating (hidden) folder **./config**.

Can you provide the path?

---

### Post by ron999 on 2011-06-08
> **rbowen1 said:**
> 

Can you provide the path?
It's hidden.
Need to use View and tick 'Show hidden files'.

Path:-
/home/ron/.config

---

### Post by crispy_420 on 2011-06-08
Or just hit 'ctrl + h' to view hidden files.

---

### Post by rbowen1 on 2011-06-08
Thank you so much Ron999.   It appears to work.   The DVD is playing in my DVD player now.   Will watch the movie and let you know the results tomorrow

---

### Post by rbowen1 on 2011-06-09
Very cool beans, ron999.  The DVD will play in any DVD player.    The DVD is in 4:3 (full screen) aspect ratio. 

Final question before I solve this thread.  Can I adjust the process so that the DVD will be in 16:9 (widescreen) aspect ratio?

---

### Post by ricey155 on 2011-06-15
im one fore devede convertor and k3b for burning !! 

it works for me on 11.04 :D

---

### Post by rbowen1 on 2011-06-22
I am solving this thread.   My original problem was not being able to watch AVI files on a DVD in a Divx player.   This was resolved by burning the AVI files to a Data DVD using K3B. 

My thanks to all that responded.

---

