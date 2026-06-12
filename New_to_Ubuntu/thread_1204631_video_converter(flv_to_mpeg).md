---
title: "video converter???(flv to mpeg)"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by koyakishore on 2009-07-05
hi friends..
i'm downloading youtube videos..

as you know, they are of flv file format..
but i want to change the format to MPEG..

is there any video converter for this purpose..??

---

### Post by samh785 on 2009-07-05
Just use this website for conversions:

[http://www.zamzar.com/url/](http://www.zamzar.com/url/)

You put the url of the video that you want converted and they convert it for you.
They do the conversion in 30 mins to an hour and send you a link to it by email. 
You don't need to make an account or anything.
:guitar:

---

### Post by cronos on 2009-07-05
Try Mobile Media Converter ([www.miksoft.net/mobileMediaConverter.htm](www.miksoft.net/mobileMediaConverter.htm))

---

### Post by spcwingo on 2009-07-05
I believe pytube will also handle this task.  You can read more about it [[COLOR="Red"]here[/COLOR]]("http://www.marcosrodriguez.me/pytube/").

---

### Post by Bradtek on 2009-07-05
> **koyakishore said:**
> is there any video converter for this purpose..??

Off the top of my head

avidemux 
```
sudo apt-get install avidemux
```

WinFF 
[http://winff.org/html_new/](http://winff.org/html_new/)

Handbrake 
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by powel212 on 2009-07-05
+1 Avidemux.

It is awesome and easy to use.

Powel

---

### Post by powel212 on 2009-07-05
There is also the free GOMEncoder.
[http://www.gomlab.com/eng/GE_Introduction.html](http://www.gomlab.com/eng/GE_Introduction.html)

It is an awesome windows based program which I sometimes use in a VirtualBox Windows guest.

It is super powerful and easy to use and free.

I am testing it in wine now and will post the results shortly.

Powel

---

### Post by powel212 on 2009-07-05
Well I tried to convert flv in Avidemux and failed so I tried GOM in Wine and failed again.

So I tried Kdenlive and finally found success.


KdenLive is also in the repositories.

Powel

---

### Post by powel212 on 2009-07-05
after updating to Mobile Media Converter 1.4.3 

Found success again

Powel

to install MMC on 64Bit ubuntu download the package and drop it in "root" /

then run

```
sudo dpkg --force-architecture -i /mmc_1.4.3_i386.deb
```

Powel

---

### Post by whitethorn on 2009-07-05
I use ffmpeg to convert almost everything I need.  You can also download winff as a gui for it.

Here's a guide for installing ffmpeg with mp3 encoding.

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I don't use winff, here's a code I use to convert .flv's to avi so that they'll play on my mp3 player.

```


ffmpeg -i /path/to/fole.flv -vcodec mpeg4 -s 320x240 -g 300 -r 29.97 -acodec mp3 -ab 128 -ac 2 /path/to/where/newfile_should_be_saved.avi

```

It let's you do alot.  If you want I could also give you my command for stripping and encoding mp3s from youtube videos.

---

### Post by pehden on 2010-05-29
I would like any video format to mp4 for xbox360 command line code.

> **whitethorn said:**
> 
```


ffmpeg -i /path/to/fole.flv -vcodec mpeg4 -s 320x240 -g 300 -r 29.97 -acodec mp3 -ab 128 -ac 2 /path/to/where/newfile_should_be_saved.avi

```

It let's you do alot.  If you want I could also give you my command for stripping and encoding mp3s from youtube videos.

---

### Post by k3lt01 on 2010-05-29
Old thread I know but someone else resurected it so I'll just say use Pitivi it's standard in Lucid and it works very well.

---

### Post by quinnten83 on 2010-05-29
> **Bradtek said:**
> Off the top of my head

avidemux 
```
sudo apt-get install avidemux
```

WinFF 
[http://winff.org/html_new/](http://winff.org/html_new/)

Handbrake 
[http://handbrake.fr/](http://handbrake.fr/)

+1 on handbrake, although the current version does not seem to work in Lucid.

---

### Post by pehden on 2010-05-29
I loaded that but that doesnt just convert video files. I know winFF does i have the gui version on my laptop mut i need to put it on my server so i would like a command that will tell the server to convert selected file to a certain format.
> **k3lt01 said:**
> Old thread I know but someone else resurected it so I'll just say use Pitivi it's standard in Lucid and it works very well.

---

### Post by SoFl W on 2010-05-29
Old thread but I believe the FireFox plug in Videodownloader will convert.  (never used the converter)

I use [VLC]("http://www.videolan.org/") for conversions.

---

### Post by MrWES on 2010-05-29
> **koyakishore said:**
> hi friends..
i'm downloading youtube videos..

as you know, they are of flv file format..
but i want to change the format to MPEG..

is there any video converter for this purpose..??

Snipped from ubuntugeek.com -- using ffmpeg of course.

convert .flv to .mpg using ffmpeg

First you need to download your .flv file to a folder and you need to Open a terminal window and go in to the .flv file folder and type the following command

ffmpeg -i jokes.flv -ab 56 -ar 22050 -b 500 -s 320×240 jokes.mpg

jokes.flv is the file you want to convert, so the name must be the same as the source file.You can name jokes.mpg whatever you want as long as it has the .mpg extension.

-b bitrate: set the video bitrate in kbit/s (default = 200 kb/s)

-ab bitrate: set the audio bitrate in kbit/s (default = 64)

-ar sample rate: set the audio samplerate in Hz (default = 44100 Hz)

-s size: set frame size. The format is WxH (default 160×128 )

---

### Post by mapes12 on 2010-05-29
Video DowloadHelper is a FF Add On that does the conversion on the fly i.e. it converts the flv to mpeg at the same time as the download. Therefore, you do not have to download the flv and then convert it as a separate task. Search for it in the FF Add on section. I've posted a screenshot of its home page. 

I've tried loads and this one is the best IMHO.

---

### Post by jerenept on 2010-05-29
Du tu dut duh... try arista transcoder.

---

### Post by JohnAStebbins on 2010-05-29
> **quinnten83 said:**
> +1 on handbrake, although the current version does not seem to work in Lucid.

As HandBrake's download page plainly says
> 0.9.4 is no longer available for ubuntu due to compatibility issues with the newer version of gnome. You can instead, download a nightly (pre-release) build of HandBrake from the Ubuntu PPA page.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by pehden on 2010-10-12
> **MrWES said:**
> Snipped from ubuntugeek.com -- using ffmpeg of course.

convert .flv to .mpg using ffmpeg

First you need to download your .flv file to a folder and you need to Open a terminal window and go in to the .flv file folder and type the following command

ffmpeg -i jokes.flv -ab 56 -ar 22050 -b 500 -s 320×240 jokes.mpg

jokes.flv is the file you want to convert, so the name must be the same as the source file.You can name jokes.mpg whatever you want as long as it has the .mpg extension.

-b bitrate: set the video bitrate in kbit/s (default = 200 kb/s)

-ab bitrate: set the audio bitrate in kbit/s (default = 64)

-ar sample rate: set the audio samplerate in Hz (default = 44100 Hz)

-s size: set frame size. The format is WxH (default 160×128 )




Is exactly what I was needing.

---

