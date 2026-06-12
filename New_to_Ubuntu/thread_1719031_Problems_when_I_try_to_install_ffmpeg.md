---
title: "Problems when I try to install ffmpeg"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by milindo on 2011-04-01
What happens when I want ffmpeg: 
```

me@computer:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ffmpeg : Depends: libavcodec52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavdevice52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavfilter0 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavformat52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavutil50 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libpostproc51 (>= 5:0.5+svn20091116) but 4:0.6-2ubuntu6 is to be installed
          Depends: libswscale0 (>= 5:0.5+svn20091116) but 4:0.6-2ubuntu6 is to be installed
E: Broken packages


```
I understand that a dependancy isn't there, but why the Error broken packages. Thanks :)

---

### Post by nothingspecial on 2011-04-01
Try enabling the universe and multiverse repositories, then update and try again.

---

### Post by Thund3rstruck on 2011-04-01
Also you should know that the Ubuntu build of ffmpeg is totally broken. I wrote a nautilus script to rip the audio from mp4 files and save them to mp3 and it worked great on Fedora but blew up on Ubuntu. It turns out that Ubuntu's ffmpeg doesn't come compiled with any proprietary codec support. 

I used this guide to build a legit version of ffmpeg:
[http://ubuntuforums.org/showthread.php?t=786095 ]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by FakeOutdoorsman on 2011-04-01
> **milindo said:**
> ...
I understand that a dependancy isn't there, but why the Error broken packages. Thanks :)

You probably have a third-party PPA interfering with your installation of FFmpeg. Remove the PPA, run **sudo apt-get update**, and then try re-installing FFmpeg.

> **Thund3rstruck said:**
> It turns out that Ubuntu's ffmpeg doesn't come compiled with any proprietary codec support.

Several additional encoders can be enabled with one package as shown here:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Thund3rstruck on 2011-04-01
> Several additional encoders can be enabled with one package as shown here:

Oh wow... that's awesome! Thanks!

---

