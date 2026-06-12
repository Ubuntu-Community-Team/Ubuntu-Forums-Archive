---
title: "Handbrake under Karmic"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by MrWES on 2009-10-29
Anyone have a clue as to why Handbrake will not run under Karmic?

Here's a link to the error:

[http://img163.imageshack.us/img163/4121/handbrakeerror.png](http://img163.imageshack.us/img163/4121/handbrakeerror.png)


Bill

---

### Post by fenian on 2009-10-29
Handbrake is dependent on an older version of webkit.Hopefully it will be fixed soon but the newer versions of Handbrake have dropped support for Xvid.

---

### Post by Henrikx on 2009-10-29
handbrake subversion (self-compiled) works.

[[IMG]http://i.imagehost.org/t/0048/screenshot_002.jpg[/IMG]]("http://i.imagehost.org/view/0048/screenshot_002")

---

### Post by MrWES on 2009-10-29
> **Henrikx said:**
> handbrake subversion (self-compiled) works.

[[IMG]http://i.imagehost.org/t/0048/screenshot_002.jpg[/IMG]]("http://i.imagehost.org/view/0048/screenshot_002")

Good to know -- I'll grab the source and compile it.


Thanks,
Bill

Update:
Getting the following error when running the make command:
```
Link HandBrakeCLI
/usr/bin/ld: cannot find -lbz2
collect2: ld returned 1 exit status
Compile line for ../HandBrakeCLI was:
g++ -I../libhb -o ../HandBrakeCLI test.o parsecsv.o ../libhb/libhb.a ../contrib/lib/liba52.a ../contrib/lib/libmkv.a ../contrib/lib/libavformat.a ../contrib/lib/libavcodec.a ../contrib/lib/libavutil.a ../contrib/lib/libdca.a ../contrib/lib/libdvdread.a ../contrib/lib/libfaac.a ../contrib/lib/libmp3lame.a ../contrib/lib/libmpeg2.a ../contrib/lib/libvorbis.a ../contrib/lib/libvorbisenc.a ../contrib/lib/libogg.a ../contrib/lib/libsamplerate.a ../contrib/lib/libx264.a ../contrib/lib/libxvidcore.a ../contrib/lib/libmp4v2.a ../contrib/lib/libswscale.a ../contrib/lib/libtheora.a ../contrib/lib/libfaad.a -lbz2 -ldl -lz -lpthread
make[1]: *** [../HandBrakeCLI] Error 1

```

---

### Post by Henrikx on 2009-10-29
• subversion
    • yasm
    • build-essential
    • autoconf
    • libtool
    • zlib1g-dev
    • **libbz2-dev**
    • intltool (gui)
    • libglib2.0-dev (gui)
    • libdbus-glib-1-dev (gui)
    • libgtk2.0-dev (gui)
    • libhal-dev (gui)
    • libhal-storage-dev (gui)
    • libwebkit-dev (gui)
    • libnotify-dev (gui)
    • libgstreamer0.10-dev (gui)
    • libgstreamer-plugins-base0.10-dev (gui)

---

### Post by MrWES on 2009-10-29
> **Henrikx said:**
> &#8226; subversion
    &#8226; yasm
    &#8226; build-essential
    &#8226; autoconf
    &#8226; libtool
    &#8226; zlib1g-dev
    &#8226; **libbz2-dev**
    &#8226; intltool (gui)
    &#8226; libglib2.0-dev (gui)
    &#8226; libdbus-glib-1-dev (gui)
    &#8226; libgtk2.0-dev (gui)
    &#8226; libhal-dev (gui)
    &#8226; libhal-storage-dev (gui)
    &#8226; libwebkit-dev (gui)
    &#8226; libnotify-dev (gui)
    &#8226; libgstreamer0.10-dev (gui)
    &#8226; libgstreamer-plugins-base0.10-dev (gui)

Ok, HandbrakeCLI compiled and installed. I went into the gtk directory and ran ./autogen and I'm getting the following errors now:
```
checking for GHB... configure: error: Package requirements (gtk+-2.0 >= 2.8 gio-2.0 hal hal-storage libgtkhtml-3.14) were not met:

No package 'hal' found
No package 'hal-storage' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GHB_CFLAGS
and GHB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Duh! -- I installed 
libhal-dev (gui)
libhal-storage-dev (gui)

and it's compiling now

---

### Post by MrWES on 2009-10-29
Still getting the original error:

Unable to create ghb.

Bill

---

### Post by Henrikx on 2009-10-29
• subversion
    • yasm
    • build-essential
    • autoconf
    • libtool
    • zlib1g-dev
    • libbz2-dev
    • intltool (gui)
    • libglib2.0-dev (gui)
    • libdbus-glib-1-dev (gui)
    • libgtk2.0-dev (gui)
    • libhal-dev (gui)
    • libhal-storage-dev (gui)
    • libwebkit-dev (gui)
    • libnotify-dev (gui)
    • libgstreamer0.10-dev (gui)
    • libgstreamer-plugins-base0.10-dev (gui) 

1.
svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake-source

2.
cd /HandBrake-source

3.
./configure --launch

4.
cd /build

5.
sudo make install

If you don´t want to install handbrake

cd /HandBrake-source/build/gtk/src
./ghb

---

### Post by MrWES on 2009-10-29
That will install CLI and the GUI?

Danke sehr :)

---

### Post by MrWES on 2009-10-29
> **MrWES said:**
> That will install CLI and the GUI?

Danke sehr :)

Thanks for your help and patience.

~Bill

---

### Post by Henrikx on 2009-10-30
> Danke sehr):P
Thank you!

---

### Post by ghostborg on 2009-10-30
[http://forum.handbrake.fr/viewtopic.php?f=13&t=12647]("http://forum.handbrake.fr/viewtopic.php?f=13&t=12647")

Download svn2845

use the force and sym link commands as posted remember to use dpkg not pkg.
use correct path to where you downloaded the svn

no xvid, sucks- uou

---

### Post by coffeecat on 2009-10-30
> **ghostborg said:**
> [http://forum.handbrake.fr/viewtopic.php?f=13&t=12647](http://forum.handbrake.fr/viewtopic.php?f=13&t=12647)

Download svn2845

use the force and sym link commands as posted remember to use dpkg not pkg.
use correct path to where you downloaded the svn

no xvid, sucks- uou

Unfortunately, if you follow that method, Synaptic marks Handbrake as broken and neither Synaptic nor Update Manager will do any updates until you fix broken packages. But if you do that Handbrake gets uninstalled. Recognise the voice of experience here? :(

Anyway, check that Handbrake forum link again. One of the Handbrake devs is preparing a future snapshot suitable for Karmic. Hopefully we won't have to wait long.

But it won't have XviD support. Or AVI.

---

### Post by umr3b3l on 2009-10-30
Wow I tried 7 other programs on karmic and they all had issues ripping.  Either they would freeze or crash.  this method of installing handbrake worked flawlessly.  THANK YOU Henrikx :)

---

### Post by MrWES on 2009-10-30
Same here -- spot on!

---

### Post by jasonditz on 2009-10-31
> **Henrikx said:**
> • subversion
    • yasm
    • build-essential
    • autoconf
    • libtool
    • zlib1g-dev
    • libbz2-dev
    • intltool (gui)
    • libglib2.0-dev (gui)
    • libdbus-glib-1-dev (gui)
    • libgtk2.0-dev (gui)
    • libhal-dev (gui)
    • libhal-storage-dev (gui)
    • libwebkit-dev (gui)
    • libnotify-dev (gui)
    • libgstreamer0.10-dev (gui)
    • libgstreamer-plugins-base0.10-dev (gui) 

1.
svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake-source

2.
cd /HandBrake-source

3.
./configure --launch

4.
cd /build

5.
sudo make install

If you don´t want to install handbrake

cd /HandBrake-source/build/gtk/src
./ghb

Ugh, the svn I just got failed half way through.

---

### Post by fenian on 2009-10-31
In a terminal entr these lines

For the dependencies...

> sudo apt-get install subversion yasm build-essential autoconf libtool zlib1g-dev libbz2-dev intltool libglib2.0-dev libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev libwebkit-dev libnotify-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev checkinstall

Download the source

> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake-source

Navigate to the source

> cd ./HandBrake-source

Configure handbrake...

> ./configure --launch

Navigate to assembled source...

> cd ./build

Create Handbrake .deb and install...

> sudo checkinstall

Make sure to name the file Handbrake-SVN
If you want remove handbrake you can do it in Synaptic.

---

### Post by Henrikx on 2009-10-31
Why with "."

> cd ./HandBrake-source                      cd /HandBrake-source    (without "."  )

> cd ./build                      cd /build  (without "."  )


**If you want update handbrake**

1.
cd /HandBrake-source

2.
rm -rf build

3.
svn update

4.
./configure --launch

---

### Post by p-dh on 2009-10-31
Thanks Fenian,

Your directions worked like a charm. Helps us newbies to know what to put in. One correction, you need to get rid of the (gui) from the apt-get file list.

Thanks for all.

Paul

---

### Post by crackinwindow on 2009-10-31
This solution worked perfectly for me, by why is there no .avi support?

---

### Post by fenian on 2009-10-31
> **Henrikx said:**
> Why with "."



That's just how I do it,/HandBrake-source does not work for me (and I've never done it that way) see picture for more details.

---

### Post by Tulsapoke on 2009-11-01
Thanks for these instructions. I am now converting all the video off my wife's camera that I had been waiting to use my shiny new Karmic system for.

---

### Post by hugmenot on 2009-11-01
Karmic snapshot is available as of Nov 1:

[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

---

### Post by ghostborg on 2009-11-03
Handbrake developers dropped Xvid as it was there number one support issue.
People keep insisting that we should all use h.264, but some equipment does not support it. Like MP3's, Xvid(Divx) are kind of an Internet standard.

---

### Post by hugmenot on 2009-11-04
But you can still encode to FFmpeg Mpeg-4. Isn&#8217;t that the same thing?

---

### Post by coffeecat on 2009-11-04
> **hugmenot said:**
> But you can still encode to FFmpeg Mpeg-4. Isn’t that the same thing?

I seem to remember reading that the ffmpeg mpeg-4 video quality was inferior to XviD. Perhaps someone can confirm or correct this.

My disappointment is the dropping of AVI support, although I respect the developers' stated reasons for so doing. My media player will only play AVIs or raw mpeg files. It doesn't recognise the containers that Handbrake now favours.

Darn. :(

---

### Post by hugmenot on 2009-11-05
> **coffeecat said:**
> I seem to remember reading that the ffmpeg mpeg-4 video quality was inferior to XviD. Perhaps someone can confirm or correct this.

FFmpeg Mpeg4 ASP is up there with XViD. It gives you better quality even, but XviD encodes faster.

> My disappointment is the dropping of AVI support, although I respect the developers' stated reasons for so doing. My media player will only play AVIs or raw mpeg files. It doesn't recognise the containers that Handbrake now favours.

Darn. :(

There are many other popular tools available. I for one welcome the change. AVI RIFF needs to die.

---

### Post by Drew Woodard on 2009-11-15
Installed the .deb package for the dev version from the website that supposedly works with Karmic but it just crashed at launch.

followed instructions by Henrikx to manually build and that worked, thanks.

---

### Post by JPorter on 2009-11-23
The lack of a working Handbrake package is a pretty big problem... what is the plan for getting this fixed?

---

### Post by JohnAStebbins on 2009-11-24
> The lack of a working Handbrake package is a pretty big problem... what is the plan for getting this fixed? 
[HandBrake 0.9.4]("http://handbrake.fr/") was released today.  And if you have a problem with handbrake, wouldn't it make since to ask your question on the handbrake forums?

---

### Post by ssuuddoo on 2010-12-14
I needed 2 use handbrake for building avi files. so I installed 0.9.3 on maverick. (the actual version works, but I need 2 make an AVI). 
but the old version sais:

ghb: error while loading shared libraries: libhal-storage.so.1: cannot open shared object file: No such file or directory

...even though the libraries are present on the system. 
any help? 

existing libraries:
/usr/lib/libhal-storage.so.1
/usr/lib/libhal-storage.so.1.0.0

---

### Post by hugmenot on 2010-12-14
y dont u use ffmpeg to remux. is easy as &#960;.

---

### Post by ssuuddoo on 2010-12-15
hmmm. but using anything I want, the output in the actual version is not AVI, since the support is dropped. I tried the ffmpeg before, but after that when trying to cut off some parts of the video the audio was dissorted, because avidemux detected H.264 and had lost frame accuracy due 2 some b-frames issue. Maybe U'll tell me I shouldn't use avidemux, but what then? 

thnx

---

### Post by hugmenot on 2010-12-15
H.264 is not suitable for editing precisely because of its highly compact frame interdependence. Use a intra only format for editing. It’s much larger but as with image editing you save lossy only in the end you the distribution format. And for that H.264 in MP4 is just fine. I would suggest Huffy codec, or dnxhd in MXF container. H.264 for editing is the wrong way to go.

u dig?

---

### Post by ssuuddoo on 2010-12-16
:D hmmm. obviously, I don't dig. :D

AVI-xvid seems from the handbrake developers should be obsolete comparing 2 the h.264, but from this point of view it seems 2 me as a little new ****, when it is not as easy to manipulate. grrrr (I know, it has more features and chapters and others, but sorry dude, I don't need them, I just wanna convert, cut and combine two simple mpeg2 files without messing the audio timing. 


and could U please show me, where 2 find that Huffy codec, or dnxhd in MXF container? 
thnx

or. the easy way, as I asked the first time, how 2 get ghb 0.9.3 work on maverick? 
thnx again dude

---

### Post by hugmenot on 2010-12-16
D00d, mpeg2 is just fine for cutting 2. Just leave it as mpeg2 for editing and export the final publishable result to H.264. Avi doesn’t play into this at all.

No idea how to run old versions.

---

### Post by ssuuddoo on 2010-12-16
I have tried 2 cut the mpeg2 on the 1st line, but it was messed. I dunno why. 
now it is well. I have converted both mpeg2 files on a second comp with vin.xp and ghb 0.9.3 and cut and combined the resulted avi files on avidemux here on tux and now everything is well. thnx 4 help

---

