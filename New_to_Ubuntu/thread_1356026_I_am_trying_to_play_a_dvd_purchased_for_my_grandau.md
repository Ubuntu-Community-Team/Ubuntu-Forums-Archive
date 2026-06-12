---
title: "I am trying to play a dvd purchased for my grandaugher"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by audit on 2009-12-15
I place the the dvd in and i receive an error stating: > Could not open location; you might not have permission to open the file. 

how can i make this play to make her happy.

---

### Post by heyho on 2009-12-15
First port of call would be this thread:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd](http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd)

And if you haven't already, try this:

> sudo apt-get update

> sudo apt-get install ubuntu-restricted-extras

---

### Post by arochester on 2009-12-15
To play an commerical, encrypted DVD you need to install the Medibuntu Repository and then the package libdvdcss2

Medibuntu instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by issih on 2009-12-15
No...you do not need medibuntu at all, not any more:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Shows how you should do it these days, assuming you are using an ubuntu machine running 9.04 or 9.10 (jaunty or karmic), just click on the link below:

[apt:ubuntu-restricted-extras?section=universe?section=multiverse]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")

Then open a terminal (Applications->Accessories->Terminal) and enter:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Enter your login password when prompted (there will be nothing written to the screen as you do so, just enter it and hit enter)

That should be all you need to do

Hope that helps

---

### Post by kansasnoob on 2009-12-15
> **issih said:**
> No...you do not need medibuntu at all, not any more:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Shows how you should do it these days, assuming you are using an ubuntu machine running 9.04 or 9.10 (jaunty or karmic), just click on the link below:

[apt:ubuntu-restricted-extras?section=universe?section=multiverse]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")

Then open a terminal (Applications->Accessories->Terminal) and enter:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Enter your login password when prompted (there will be nothing written to the screen as you do so, just enter it and hit enter)

That should be all you need to do

Hope that helps

I was curious so I tried this beginning by disabling my Medibuntu repo and removing libdvdcss2 and w32codecs. Then I followed your instructions.

I popped in my Hancock vid and no good, just wouldn't play. Restored the Medibuntu apps and away she goes!

---

### Post by running_rabbit07 on 2009-12-15
> **kansasnoob said:**
> I was curious so I tried this beginning by disabling my Medibuntu repo and removing libdvdcss2 and w32codecs. Then I followed your instructions.

I popped in my Hancock vid and no good, just wouldn't play. Restored the Medibuntu apps and away she goes!
I never was able to play DVDs until adding medibuntu also. I had the ubuntu restricted extras before and it alone did not work for DVDs.

---

### Post by 3rdalbum on 2009-12-15
You've always been able to install libdvdcss2 without Medibuntu, but Medibuntu makes it easier and it also pulls in other software that helps read DVDs. Not to mention that Medibuntu is useful for other software.

What program are you trying to use to play the DVD? You should be using VLC Media Player.

---

### Post by audit on 2009-12-15
first I typed this line of code:
```
sudo apt-get install ubuntu-restricted-extras 
```
with no change, so i then typed this line
```
sudo /usr/share/doc/libdvdread4/install-css.sh 
```
still could not pay dvd. So i rebooted--because when all else fails reboot.
And it worked perfectly--thank you all you made my grandaughter very happy--she really needed a Dora fix.

---

### Post by running_rabbit07 on 2009-12-16
I am glad you got that working. I have a 6 year old and and I have seen that look when I told her that her system can't play movies. Her problem is hardware though. She has DVD ROM only.

---

### Post by mc4man on 2009-12-16
That method as posted by issih ( the .sh) is absolutely fine, it's retrieving the same libdvdcss2  (1.2.10) from medibuntu as the repo provides
The only real difference is the ver. number - .2 vs. .3

(they forgot to up the ver.# in the script for karmic
> version=${uversion}-0.2medibuntu1
when it could be this instead
> version=${uversion}-0.3medibuntu1
Same libdvdcss2 anyway

For *enabling dvd playback* in vlc **all** you need is vlc installed and run the script
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

To add dvd playback to gstreamer just the above and the bad plugin, though this would be better than ubunutu-restricted-extras, which is slightly bugged in 2 areas  (blue only for 32 bit and w32codecs

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse [COLOR="Blue"]gstreamer0.10-pitfdll[/COLOR]
```

Medibuntu doesn't offer anything for dvd playback except libdvdcss2, though there are some other packages that could be of interest to some
(the w32codecs and now a faac enabled libavcodec among others

edit:
> So i rebooted
It's somewhat interesting in karmic how often this makes a difference when either adding, removing or changing some things (libs, codecs, ect. ), should almost be a 'recommend'

---

### Post by im_prad on 2009-12-17
"Shows how you should do it these days, assuming you are using an ubuntu machine running 9.04 or 9.10 (jaunty or karmic), just click on the link below:

apt:ubuntu-restricted-extras?section...ion=multiverse"

Doesnt work Although I have VLC installed on my ubuntu and gives error :-

[COLOR="Blue"]"You tried to access the address apt:ubuntu-restricted-extras?section=universe?section=multiverse, which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page."[/COLOR]

I have got ubuntu-restricted-extras installed already

---

### Post by LowSky on 2009-12-17
You need libdvdcss, without adding the medibuntu repos all you need is this commnd

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by LowSky on 2009-12-17
double post

---

### Post by issih on 2009-12-17
> **im_prad said:**
> "Shows how you should do it these days, assuming you are using an ubuntu machine running 9.04 or 9.10 (jaunty or karmic), just click on the link below:

apt:ubuntu-restricted-extras?section...ion=multiverse"

Doesnt work Although I have VLC installed on my ubuntu and gives error :-

[COLOR="Blue"]"You tried to access the address apt:ubuntu-restricted-extras?section=universe?section=multiverse, which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page."[/COLOR]

I have got ubuntu-restricted-extras installed already

All the apt-url is meant to do is install restricted extras...so even if it had worked it wouldn't do you any good, as LowSky said install libdvdcss either using the method in my previous post (the terminal command) or LowSky's method

---

### Post by im_prad on 2009-12-18
No Luck Mate,

Did what you suggested but still can't play .avi or .vob files with VLC in ubuntu, it tries to open and in seconds closes itself off

ran the first command :-

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)


[COLOR="Blue"]prad@PradzWorld:~$ wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
--2009-12-18 11:42:33--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36270 (35K) [application/x-debian-package]
Saving to: `libdvdcss2_1.2.9-2medibuntu4_i386.deb'

100%[======================================>] 36,270      38.5K/s   in 0.9s    

2009-12-18 11:42:35 (38.5 KB/s) - `libdvdcss2_1.2.9-2medibuntu4_i386.deb' saved [36270/36270]
[/COLOR]

The second one :-

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

[COLOR="Blue"]prad@PradzWorld:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
[sudo] password for prad: 
dpkg - warning: downgrading libdvdcss2 from 1.2.10-0.2medibuntu1 to 1.2.9-2medibuntu4.
(Reading database ... 146195 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
prad@PradzWorld:~$ 
[/COLOR]



[LIST]
[/LIST]> **LowSky said:**
> You need libdvdcss, without adding the medibuntu repos all you need is this commnd

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

---

### Post by PaulReaver on 2009-12-18
the restricted extras way worked for me.

although medibuntu repo is usefull for other stuff

---

### Post by bkmfs on 2009-12-18
Yes Ubuntu is very difficult to set up to do the most basic things but easy to do the complicated.  May I suggest LinuxMint or Super OS?  Those are basically the same thing only illegal enough to play the stinkin' dvd where the stinkin' dvd should be playing anyway.  (Your dvd rom should be able to play the movie by the way)

bkmfs
Super OS 9.04

______________________________________________________
"the music industry has already learned that the best way to turn people into theives is to treat them like theives"

---

