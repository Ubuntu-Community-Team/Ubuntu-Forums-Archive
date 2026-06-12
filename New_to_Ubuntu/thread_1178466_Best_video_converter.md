---
title: "Best video converter?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-06-04
Which is the best video converter to use?
I want to convert lots of .flv's to something easily usable like .avi or on of Ubuntus free formats, preferably a program with batch conversion and something found in the package manager?

Ps. What is Ubuntus standard free video format?

---

### Post by s.fox on 2009-06-04
Hi,

I found [this]("http://ubuntuforums.org/showthread.php?t=567016") in the archives.  It should be of some use to you. :D

-Ash R

---

### Post by kellemes on 2009-06-04
avidemux

---

### Post by CaptainMark on 2009-06-04
Okay, something more specific, which is the best programme to use to encode any video file including dvds, into ipod video formats .mp4?

---

### Post by Tholley on 2009-06-04
If you are just wanting to play different formats using Ubuntu, i have found Ubuntu is very convenient and will play most all formats (.flv, mpeg, .avi) all in the same player(instead of using 3 different players). I don't know if there is any software that will convert like say .flv to .avi, but that is really un-needed in Ubuntu. You will need to install the restricted-extra-package. see this link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 
If you are wanting to encode so as to burn on blank DVD, I find that encoding using DeVeDe and then burn using K3B works best for me.
 
Hope this helps...

---

### Post by vinutux on 2009-06-04
1. There is no [COLOR="DarkOrange"]ubuntu standerd[/COLOR] like what .wmv did in windows. Ogg theora is best fomat to ubuntu coz it natively playable without installing third party codecs. .ogm is the extension of theora. 
So use theora format (it replace flvs future because of new integration of <video> tag in html5)

2. There are alot of tools for converting video.........
[COLOR="Green"]
winff[/COLOR] is simple & good but not support all type of flvs

[COLOR="Green"]Avidemux[/COLOR] is most stable choice but comblex editing software than converter

[COLOR="Green"]Hansbrake[/COLOR] is new converter cum dvd ripper fast one

but i recomended the simple ***[COLOR="Red"]oggconvert[/COLOR]*** .very easy to convert any formats (including flvs) to ogg throra.

install it  

sudo apt-get install oggconvert

done.................:D

home page og oggconvert [http://oggconvert.tristanb.net/download/ubuntu/]("http://oggconvert.tristanb.net/download/ubuntu/")


..................................................................

---

### Post by andrew.46 on 2009-06-04
Hi CaptainMark,

> **CaptainMark said:**
> Which is the best video converter to use?
I want to convert lots of .flv's to something easily usable like .avi or on of Ubuntus free formats, preferably a program with batch conversion and something found in the package manager?

I would recommend learning to use the best tool for this job which is FFmpeg. It is a commandline tool but the commands are fairly straightfoward and become intuitive with use. FFmpeg can be installed from Synaptic but a little more work needs to be done to allow the program to work as its makers intended:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If you have a choice in the matter you would be better to avoid the avi container as it is a little limited. Many are using the mp4 container and the cognoscenti are all using mkv :-).

All the best with this,

Andrew

---

### Post by sandyd on 2009-06-04
Mobile Media Converter

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

### Post by oedha on 2009-06-04
is you dont feel bother to work on CLI..... ffmpeg then
[http://www.ffmpeg.org/ffmpeg-doc.html#SEC7](http://www.ffmpeg.org/ffmpeg-doc.html#SEC7)

regards;
~E~

---

### Post by FakeOutdoorsman on 2009-06-05
If you want batch capability with FFmpeg, I recommend taking a look at Andrew's excellent guide to the *find* command:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937) [ubuntuforums.org]

Edit: I forgot to mention you can get some great results for iPod using the libx264 presets with FFmpeg.  The good thing is FFmpeg in the Jaunty repository comes with these presets, but you'll just need to enable some encoders as Andrew has mentioned above.

Example FFmpeg command for iPod (just change the input file in [color=#FF0000]red[/color]):
```
ffmpeg -y -i [color=#FF0000]input.avi[/color] -pass 1 -vcodec libx264 -vpre fastfirstpass -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod -an /dev/null && ffmpeg -i [color=#FF0000]input.avi[/color] -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre normal -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod output.mp4
```

Above example from: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by sandyd on 2012-12-19
**Necromancing - thread closed**
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old. 

Thanks!

---

