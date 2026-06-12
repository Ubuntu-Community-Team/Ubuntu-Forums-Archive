---
title: "Installing VLC 1.1.1 from source"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by gavdari on 2010-07-27
At last I gathered my courage and decided to install something from  source for the first time: VLC 1.1.1 on Lucid. First I tried ./configure, make, make  install but it didn't work, then I noticed that it should be ./configure  --prefix=/usr. First question, what is the different between  ./configure and ./configure --prefix=/usr.? 
When I used the correct  command, something called lua is missing. I disabled it with  --disable-lua and again, mad was missing. --disable-mad returns another  missing plugin. Second question: are they really missing?
I can find lua  1.5.4 on my system, but it seems the installer can't find it. How  should I proceed?

---

### Post by mikewhatever on 2010-07-27
[http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux](http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux)
Check out the howto.

---

### Post by ron999 on 2010-07-27
> **mikewhatever said:**
> [http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux](http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux)
Check out the howto.

Hi
The how-to in the link looks OK.

But what does all this bit mean:-

> There are several options in ./configure to disable and enable various features of vlc while installing. You can see all of them by running

    [shredder12]$ ./configure --help

and if you know what you are doing, you an use those options as per your need.

---

### Post by mc4man on 2010-07-27
> But what does all this bit mean:-

At this point vlc has the bulk of options enabled by default, there may be some things you want enabled that aren't, or you may want to disable some things. (you'll need lua or don't even bother.

Here is the configure for my latest 1.1.1 on maverick and lucid (32 bit
> ./configure  --with-live555-tree=/usr/lib/live --enable-real --enable-realrtsp --enable-snapshot --enable-merge-ffmpeg --disable-x264  --disable-mod --enable-loader

In lucid and earlier if you don't build vlc from a newer ffmpeg than in the ubuntu repos there is little to be gained.

My preferred method is to build a ffmpeg as static just for vlc. 

It's actually easy to do once you've done it - Andrew.46 has an excellent guide for a svn build (vlc 1.2). in the tips forum

He had to use a specific ffmpeg that is a bit outdated now to account for 64 bit users - maybe I'll post a modified version for 1.1.1 there
(32 bit users have no concerns statically linking any recent ffmpeg version

The 1.2 version may or may not be bugged  - bit of hit or miss day by day or less

Note that in maverick the ffmpeg in the repo is pretty up to date as is vlc-1.1.0 (maverick should do one more rebuild - 1.1.0 has some flaws

---

### Post by ron999 on 2010-07-27
OK mc4man
I've already built x264 and ffmpeg using fakeoutdoorman's tutorial.
There isn't a VLC 1.1 ppa for Karmic and it would be good to compile it myself.
But I don't have enough knowledge to decide what to enable and what to disable.
So I'll hold back for now.

---

### Post by Devport on 2010-07-27
Sorry - modified bad post. My PPA suggestion was not for karmic. Did you try to download the lucid packages and install them manually with gdebi ? I think it may be possible if all dependancies are fulfilled on karmic too.

[https://launchpad.net/~c-korn/+archive/vlc/+sourcepub/1245134/+listing-archive-extra](https://launchpad.net/~c-korn/+archive/vlc/+sourcepub/1245134/+listing-archive-extra)

---

### Post by mc4man on 2010-07-28
I just noticed andrew.46 has updated his howto to use the 0.6 ffmpeg which will work just fine.

(you can use the static build ala F.O.'s howto instead, but this is a good method to use and learn. ( plus accounts for 64 bit users by patching the ffmpeg source - the current asm patch probably won't work with the latest svn.

[http://ubuntuforums.org/showthread.php?t=1398119&highlight=vlc+svn](http://ubuntuforums.org/showthread.php?t=1398119&highlight=vlc+svn)

For a 1.1.1 build you'll need to make some small changes to the build vlc section (use different source mainly

If you want vp8 support you'll need to add that to ffmpeg build.
If you want sdl and or sdl_image support no big deal to enable

The build deps shown should be ok for karmic - may need to change a name or 2.

The libtag version on karmic and possibly lucid will produce an error - easy to fix or one can disable taglib in the vlc configure.

Am on 10.10 atm and have got to go  - can ck. karmic later.

To give some idea on how straightforward it becomes as Ex. (don't follow) these small set of commands produced a good build in maverick and lucid (I used a current svn, but that's not always a given - the 0.6 source as in guide will be good, especially for first time around

> mkdir -p ~/vlc_build/vlcdeps && cd vlc_build  

svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg && cd ffmpeg

./configure --prefix=$HOME/vlc_build/vlcdeps/usr --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-ffmpeg --disable-ffplay --disable-ffserver --disable-doc --disable-decoder-amr --enable-libvpx

make
make install-libs install-headers
make distclean

cd ..
wget [http://sourceforge.net/projects/vlc/files/1.1.1/vlc-1.1.1.tar.bz2/download](http://sourceforge.net/projects/vlc/files/1.1.1/vlc-1.1.1.tar.bz2/download)

tar -xvjf vlc-1.1.1.tar.bz2

cd vlc-1.1.1

export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"

./configure --enable-real --enable-realrtsp  --enable-snapshot --enable-merge-ffmpeg --disable-x264 --with-live555-tree=/usr/lib/live --enable-loader
make 
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc --pkgversion "1.1.1-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default

sudo ldconfig

screen shows a build folder in karmic from a few weeks ago for builds of 1.1.1 and 1.2 - I guess I decided the libtag 1.6.3 was the way to go  - it was built and installed into the vlcdeps dir ala ffmpeg.

Trust me - after a build or to it's a piece of cake, as will be modding for oneself if desired
(removing, adding support, vaapi ect.

---

