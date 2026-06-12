---
title: "No audio when I copy a .mpg video file to a DVD"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by ridisempre on 2010-12-02
Hi!

I'm having a problem with some video files in .mpg format that work fine on my computer, but when I copy them to a DVD to watch from a DVD player, there is no more audio. Is it a codec problem? Here is the audio information for the files:

Codec: Dolby Digital (AC-3)
Sample Rate: 48000 Hz
Bitrate: 256 kbps

Any help would be greatly appreciated!

---

### Post by Zookalicious on 2010-12-02
It's most likely the software you're using to burn the DVD. Try using a different application, easy enough to find a good one through google or the software center. I would advise you on one but I don't remember the last time I had to burn a DVD :P

---

### Post by ridisempre on 2010-12-03
I'm not burning the DVD with anything special. I'm just copying and pasting them onto a dvd using ubuntu folders....

---

### Post by migs73 on 2010-12-03
> **ridisempre said:**
> I'm not burning the DVD with anything special. I'm just copying and pasting them onto a dvd using ubuntu folders....

And there lies the problem me thinks!

Try one of the DVD writing packages in the Software Centre. Brasero is the first one that springs to mind. I've not used it to write a video DVD but it has worked for all my data writing needs.

---

### Post by Zookalicious on 2010-12-03
Brasero is installed by default. So just go to Applications > Sound & Video > Brasero Disc Burner.

Select Video Project and just add your .mpg there.

---

### Post by ridisempre on 2010-12-09
I tried to burn it with Brasero, but now I'm having another problem. When it's time to burn the disc, it ejects it and says an internal error has occurred. When I save the error log, it says "Unsupported type of task operation". Any ideas?
Thanks!

---

### Post by mcduck on 2010-12-09
> **migs73 said:**
> And there lies the problem me thinks!

Try one of the DVD writing packages in the Software Centre. Brasero is the first one that springs to mind. I've not used it to write a video DVD but it has worked for all my data writing needs.

+1 to this.

You can't create a video DVD playable on standalone DVD players by just dropping the movie file to a disc.

At the very minimum, you need to convert it into proper .VOB files, and place them into appropriate directories. Although using a burning application that does all the required work is highly recommended...

edit: DeVeDe is a decent DVD authoring app for Linux. Of course if you don't mind using command-line, then you could use dvdauthor and mkisofs directly.

[http://davestechsupport.com/blog/2009/01/03/making-a-video-dvd-in-ubuntu-linux/]("http://davestechsupport.com/blog/2009/01/03/making-a-video-dvd-in-ubuntu-linux/")
[http://www.ivankristianto.com/os/ubuntu/tutorial-make-dvd-video-in-ubuntu/546/]("http://www.ivankristianto.com/os/ubuntu/tutorial-make-dvd-video-in-ubuntu/546/")

---

### Post by ridisempre on 2010-12-09
It's not a standalone DVD. It usually palys .avi and .mpg4 files... i just don't know what the problem is with the audio this time. Could it be because these files came from a camcorder?

---

### Post by ridisempre on 2010-12-09
Thanks- It works! Is there anyway to get DeVeDe to burn directly to a DVD instead of making an image first?

---

### Post by mcduck on 2010-12-09
I don't think so, it's just a DVD authoring tool, not a burning tool.

---

### Post by amsterdamharu on 2010-12-09
> It's not a standalone DVD. It usually palys .avi and .mpg4 files... i  just don't know what the problem is with the audio this time. Could it  be because these files came from a camcorder?

Did you re-encode the files?
If you use devede and add the files to your project make sure you check the box "this file is already a DVD/xCD-subable MPEG-PS file" under the file properties -> misc tab. Otherwise devede will re-encode the files for you and that could take ages.

I wonder what format the files are, could you post the output of ffmpeg for me?
```
ffmpeg -i myvidiofile.mpg
```

If your DVD can play AVI it probably has a usb port somewhere where you can test if it plays the files when you copy them on a usb stick.

---

