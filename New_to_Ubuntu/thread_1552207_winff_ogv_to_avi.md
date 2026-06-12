---
title: "winff ogv to avi"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by DarinB on 2010-08-13
I am trying to use winff to convert a desktop vid to avi. 
i get this error message and i tried making it a ms compatible avi and got another error any ideas what to do,,,i think i am missing some libs.[ATTACH]166331[/ATTACH]

[ATTACH]166332[/ATTACH]
I am not sure what the problem is with libmp3lame or libxvid ????

---

### Post by Paul820 on 2010-08-13
Do you have ffmpeg installed?

---

### Post by inameiname on 2010-08-13
If all else fails with winff, an alternative is using this script, which uses mencoder. Works for me.

---

### Post by bodhi.zazen on 2010-08-13
> **Paul820 said:**
> Do you have ffmpeg installed?

These files are containers or wrappers.

So if the graphical tools fail you need to look under the hood. How is the video encoded ? The audio ?

ffmpeg will help, but it takes a little time investment to learn to use.

The pay off is you can convert files easier, with more control, and better conversion / fine tuning over quality and size of the files (IMO).

See :

[FFmpeg Basics for Beginners | Linuxers]("http://linuxers.org/tutorial/ffmpeg-basics-beginners") 

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

In particular, I like this image (from the second link):

[IMG]http://howto-pages.org/ffmpeg/avmux.png[/IMG]

Which is why I am asking what format the video and audio is in (not the name of the container).

---

### Post by DarinB on 2010-08-13
how do i use this script

---

### Post by ron999 on 2010-08-13
@DarinB
To allow WinFF and ffmpeg to use the libmp3lame and libxvid codecs you have to enable the **Medibuntu** repository.
Use _**option C**_ in this link here:-[http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by inameiname on 2010-08-13
To use the script, just copy and paste it into your /home/(your username)/.gnome2/nautilus-scripts folder somewhere and then all you ever have to do is right click the ogv file and select the script and it'll do it all for you.

Technically you could also extract the terminal line from the script and use it in the terminal and it'll work too. You just have to ensure you have the right file location specified that you want to convert.

Personally, I have hundreds of nautilus scripts that I use and find it far far easier for the little things.

---

### Post by DarinB on 2010-08-13
hey ron999 i followed the link but in the end ffmpeg did not install 
therefore i reinstalled the one in synaptic and i suppose adding all the libs helped another problem and now it works for converting .flv to mp3 with no error of liblame or libxvid but it still does not convert ogv to avi. i get an error about 
***cannot get resampling content***

[ATTACH]166359[/ATTACH]

---

### Post by ron999 on 2010-08-13
OK
I think you're having problems with Winff/ffmpeg because it's not the latest version.

Try using mencoder from the command line like this:-

```
mencoder "/home/darin/Downloads/testdesktopvideo4.ogv" -o testdesktopvideo4.avi -ovc lavc -oac mp3lame

```
Just copy and paste that command into the monitor.

---

### Post by DarinB on 2010-08-13
this is the error i got i had to change the location of the file since it was on my Desktop....

darin@darin-desktop ~ $ mencoder "/home/darin/Desktop/desktop video.ogv" -o desktop video.avi -ovc lavc -oac mp3lame
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x6f5584
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1440x896  24bpp  22.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1440x896  fps:22.000  ftime:=0.0455
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 16000 Hz, 1 ch, s16le, 100.0 kbit/39.06% (ratio: 12499->32000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x9cd22d0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1440 x 896 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.61:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1440x896 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   1.0s     22f ( 7%)  0.00fps Trem:   0min   5mb  A-V:0.095 [0:52]
Skipping frame!
Pos:   1.7s     39f ( 7%)  0.00fps Trem:   0min   6mb  A-V:0.093 [2011:52]
Skipping frame!
File not found: 'video.avi'9.47fps Trem:   0min   4mb  A-V:-0.009 [881:52]
Failed to open video.avi.
Cannot open file/device.

Exiting...
darin@darin-desktop ~ $

---

### Post by ron999 on 2010-08-13
Hi
There's something wrong with that command.
Get the file names right.
It needs to be one word.
Like this:-
[SIZE="5"]desktopvideo.ogv
desktopvideo.avi[/SIZE]

No gaps between the words.

These aren't acceptable:-
[SIZE="5"]desktop video.ogv
desktop video.avi [/SIZE]

---

### Post by bodhi.zazen on 2010-08-13
> **ron999 said:**
> Hi
There's something wrong with that command.
Get the file names right.
It needs to be one word.
Like this:-
[SIZE=5]desktopvideo.ogv
desktopvideo.avi[/SIZE]

No gaps between the words.

These aren't acceptable:-
[SIZE=5]desktop video.ogv
desktop video.avi [/SIZE]

Informational post : If the file name has a space, you can use quotes, as was done in at least one post. I did not read all the posts to see if they were missing.

---

### Post by DarinB on 2010-08-13
i have a space in the actual file name should i remove the space. Or
mencoder "/home/darin/Desktop/desktop video.ogv" -o "desktop video.avi" -ovc lavc -oac mp3lame

---

### Post by DarinB on 2010-08-13
awesome! it works with the quotes above... Ubuntu Guru comes through with stuff very few know thanks ....AND Thanks Ron999 for the mencoder stuff
is there a gui for this or am i now being a little glutinous????

---

### Post by DarinB on 2010-08-13
the gtk-mydesktopvideo with the mencoder to convert it works like a charm.
if you were curious what my purpose was.

---

### Post by ron999 on 2010-08-13
> **DarinB said:**
> the gtk-mydesktopvideo with the mencoder to convert it works like a charm.
if you were curious what my purpose was.

I thought that's what you were up to.:D
Glad it worked out.
Next time you can try the command from inameiname's script.
It's just the same as your command.
Except, instead of this:-
[SIZE="5"]-ovc lavc[/SIZE]

you substitute this:-
[SIZE="5"]-ovc xvid[/SIZE]

See if one is better than the other.8-)

I don't know whether there's a GUI for mencoder.:(

---

### Post by DarinB on 2010-08-14
I have never used scripts in Ubuntu. not sure how. I did once with win2k. but that was in a class so, it served no purpose. this stuff only gets learned when you write them yourself and execute them yourself. 
I have the script i downloaded it **How do i Run it? **it seems like it would be easier than opening a terminal each time. I did get the sound going with a mike I found an easy tutorial on you tube. this is awesome stuff gtk-mydesktopvideo...i already sent a little tweak to a friend i converted to ubuntu...now i put her on LM9 saved me tons of time since all the video and proprietary repos are all set up. Linux Mint rocks!
thanks again

---

### Post by inameiname on 2010-08-14
To run the script, as I said, it's merely putting it into your /home/(your username)/.gnome2/nautilus-scripts folder (anywhere in it), and then whenever you need to convert ogv to avi, just right click the ogv file in nautilus and go to the 'scripts' folder in your context menu that pops up with a right click, and select the script. Then it runs automatically and converts that very ogv, and in the end you will have an avi. That is all.

And for any other scripts, you can do the same. Just put inside that folder and voila, you can run them just by selecting them in your right click context menu. Makes things far easier than using the terminal for many things. (FYI, if you don't immediately see the script in your scripts folder in your context menu, it is probably because you need to refresh things, so just a restart to your computer will fix that.)

Finally, before I forget, the script MUST be set to executable before it can ever run, whether you double click and try to run it directly or through the nautilus-scripts folder. So just ensure it is before you put it inside your nautilus-scripts folder, by right clicking it, and going to 'properties', and then click the 'permissions' tab, and make sure the 'Allow executing file as a program' option is checked. 

This all sounds complicated I'm sure, but it's actually quite easy in the end and will be even easier when you wish to convert things. I actually have scripts such as this one for all sorts of formats. And if you ever truly find scripts to rock your world, here is a link to download a bunch of them: [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/). [http://www.gnome-look.org](http://www.gnome-look.org) also has tons of really cool user-made ones for all sorts of handy little things.

---

### Post by DarinB on 2010-08-14
Thanks iname,
it works but the name is just the first work of the file with nothing else....i renamed it and added the extension. is there a way to get it to be named just like the .ogv but with an .avi???

---

### Post by inameiname on 2010-08-14
I'm not sure what you are talking about in regards to it working but the name is merely the first work of the file. From my recollection, I thought it did just what you want it to do. So to test it, I recorded a few seconds from gtk-RecordMyDesktop, which produces an ogv file in which I called it 'test.ogv' prior to starting the recording, and when finished I right clicked it and selected the script, and it resulted in an avi called 'test.avi'. So from my example, it seems to have done for me what you were trying to get it to do. Therefore, I'm afraid I'm not sure what was different. 

UPDATE:

When you say 'first work of the file', do you mean your filename has more than one word, such as something like this: 'Testing File.ogv'? If that is the case, I know what you mean, as I did this test as well out of curiosity, and from a file called 'Test File.ogv', when converted, it merely gave me an avi called 'Test'. I'm afraid I'm not entirely sure how to fix this issue, as spaces in filenames always bring up issues in Linux. I'm certain there is a simple line of test to replace in the script and it'll work, but I don't really know for sure what it may be. Obviously, it's this part of the script: "filename=${1%.*}" that needs changed to something that will handle spaces.

---

### Post by DarinB on 2010-08-14
thanks i figured it out as well to remove the spaces. and i meant the first word of the file name, I am a crappy typist. 
when i have not spaces in the file name it comes up properly. 
thanks again great script.

---

### Post by bodhi.zazen on 2010-08-14
> **DarinB said:**
> thanks i figured it out as well to remove the spaces. and i meant the first word of the file name, I am a crappy typist. 
when i have not spaces in the file name it comes up properly. 
thanks again great script.

Linux does not like spaces in file names.

You can use underscores (common work around) so 

file with spaces.txt

becomes

file_with_spaces.txt

Or , if you want to use spaces you can 

1. escape them with a \

> file\ with\ spaces.txt

2. use quotes (you can use single or double quotes)

> "file with spaces.txt"

3. Or use tab completion (type part of the file name, then hit the tab key, the shell will complete the file nam).

> file<tab>

---

### Post by DarinB on 2010-08-16
i have thousand of OO files with spaces is that bad?

---

### Post by bodhi.zazen on 2010-08-16
> **DarinB said:**
> i have thousand of OO files with spaces is that bad?

It does not matter so long as you escape or quote the files or use tab completion (on the command line).

---

### Post by ubudog on 2012-08-16
Old thread closed.

---

