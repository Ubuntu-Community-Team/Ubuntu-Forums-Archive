---
title: "convert ogv to avi"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by hellomoto on 2010-07-22
Hello I have an ogv file that I would like to convert to avi. 

I would however like to do this with as little loss of audio and video quality as possible.

I ran: 
```
 mencoder /path/to/file.old_file.ogv -o /output/path/new_file.avi -ovc lavc -oac pcm 
```

this resulted in a conversion to avi but at the expense of poor quality, (the file was further compressed). Can anyone tell me how to edit the above command to retain the maximum quality from my ogv.

---

### Post by hellomoto on 2010-07-22
bump

---

### Post by bodhi.zazen on 2010-07-22
FYI it is considered poor netiquette to bump your threads in anything less then 24 hours.

Personally I use ffmpeg to convert .

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

You can use the command line options to determine the quality of the source file and optimize the conversion.

There are several graphical front ends for ffmpeg, and detailed instructions would be dependent on the graphical interface.

After a little trial and error , ffmpeg seems to work well.

---

### Post by FakeOutdoorsman on 2010-07-22
FFmpeg will certainly do this unless the OGV is from recordMyDesktop and you're using an older FFmpeg revision:
```
ffmpeg -i input.ogv -qscale 3 -vcodec libmp3lame -aq 4 output.avi
```
Adjust *-qscale* to change video quality (and therefore output filesize). A value of 2 can be considered roughly visually lossless and 3-5 is a good balance.  The *-aq* option when used with *-vcodec libmp3lame* is similar to the *-V* option for lame.  See *lame --help* for more info on that.

Why AVI though?  It's such a dated container format.

If you are attempting to convert a video from recordMyDesktop and get this error:
```
Stream #0.0: Invalid Codec type -1
```
then you'll need to compile FFmpeg as shown here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by mubtasim123 on 2011-02-06
Hey guys their is a simple program you can use to convert and it will be high quality :confused:
:pI am not a expert but I think this video might help:razz: you out :  [http://www.youtube.com/watch?v=9jqYOhpv6hg&feature=related](http://www.youtube.com/watch?v=9jqYOhpv6hg&feature=related)

---

