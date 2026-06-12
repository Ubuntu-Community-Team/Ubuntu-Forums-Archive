---
title: "my wall-e dvd will not play in ubuntu"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2009-02-10
wall-e will not play in ubuntu makes me sad 
some googleing sugjested that maybe a normal thing
but all my other dvds play
and some people have gotten it to work after upgradeing libdvdread or dvdread or something not to sure how to do that
but please help me play my wall-e on my compy

---

### Post by hyper_ch on 2009-02-10
(1) Add the medibuntu repos

(2) Add then to following packages:

ubuntu-restricted-extra
libdvdcss2
w32codecs (or w64codecs if you're using 64bit)
vlc

(3) open it in vlc, that should work

---

### Post by mc4man on 2009-02-10
As suggested vlc may be your best bet. That title has a really 'unfriendly' form of structure protection. Basically there are 99 VTS's, the majority of which are total garbage. To make things worse many appear as the main movie title in size and structure. (IIRC the disc will appear to be about 50+ Gb in size.

If that doesn't work and you know how to run mplayer from the command line the real movie is title 30 so your basic command without any desired add. parameters (assuming drive is the mplayer default of /dev/dvd

```
mplayer dvd://30
```

or if /dev/dvd1


```
mplayer -dvd-device /dev/dvd1 dvd://30
```

Otherwise you could try totem-xine (requires libxine1-ffmpeg) or a licensed player would probably work (powerdvd

---

### Post by &lt;&lt;joe&gt;&gt; on 2009-02-11
well i tried the 2 previous post and still no go
i am not scared of compiling stuff or any thing. So if i need to do that it really wouldn't bug me.

Thinking that dvdread is in gstreamer and that some one else said that a newer version of that helped them, so i tried to complie that. but i don't know how to get ubuntu to use my complied version insted of the installed version when i use vlc or totem movie player. was thinking i would have to compile totem useing the newer version or some thing 
very confused

---

### Post by hyper_ch on 2009-02-11
libdvdread3 is also in the medibuntu repos

---

### Post by bailbath on 2009-02-11
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

Here is a guide hope it helps.
Ian

---

### Post by mc4man on 2009-02-11
> some one else said that a newer version of that helped them,
Installing a newer libdvdread (libdvdread4) isn't going to help because your current players don't/won't use it. (you are free to install it alongside libdvdread3
[http://packages.debian.org/experimental/libdvdread4](http://packages.debian.org/experimental/libdvdread4)

If you are running Hardy (8.04) you can install one of the newer libdvdnav4's which your current players will use. This libdvdnav4 has been patched for UDF structure protection problems caused by 'protect-x' style protections. (whether it helps in this case I don't know. 
Typical R1 releases using this protection were only from New Line Cimema, not Disney, more widespread in R2

[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)
If you were to install then just do a direct download and install with Gdebi, don't remove current libdvdnav4 first

If you are using Intrepid then you already have the patched libdvdnav4.

Vlc will run off libdvdread4 only if you build a 0.9.x or 1.0 git source off of it (libdvdread4-dev

,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

The current smplayer ppa will install newer versions of both libdvdread and libdvdnav4 for both hardy and intrepid and does have an mplayer build that uses them.

[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)

I'm pretty sure though that his mplayer build will not work with wall-e, it's dvdnav enabled and that could be a problem with this title. (otherwise a good mplayer build and great front end

I do know I could play the disk, but in both hardy and intrepid I use self built versions of both mplayer and vlc (though I've re installed vlc 0.8.6 in hardy and just run and rebuild a 1.0 from the build folder to see what fixes have occurred. (getting better, still has problems

---

### Post by Jingle on 2009-02-12
> **hyper_ch said:**
> (1) Add the medibuntu repos

(2) Add then to following packages:

ubuntu-restricted-extra
libdvdcss2
w32codecs (or w64codecs if you're using 64bit)
vlc

(3) open it in vlc, that should work

Ok how do I add the "medibuntu" repository?  I've got "multiverse" checked in Synaptic.   Currently when I: ```
sudo apt-get install w32codecs libdvdcss2
``` I get the following:

```
jingle@desktop:~$ sudo apt-get install w32codecs
[sudo] password for jingle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
jingle@desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

I already have VLC installed

---

### Post by hyper_ch on 2009-02-12
If you make a google search for "medibuntu" it will tell you.

---

### Post by mehturt on 2010-01-12
Does not work for me in 9.10.
I can play VOBs but there isn't a way to choose another language (or is there?).

---

