---
title: "Trying to install adobe flash 10.0 on my 64 bit os"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by savyboy24 on 2010-02-07
Hey guys,

So I just installed Ubuntu on my laptop it is dual booted and I have no experience with linux. I have been trying to use my flash but had no luck. So I have been working on the instructions below. I am at step for and when I enter the command I get this "mv libflashplayer.so ~/.mozilla/plugins
mv: cannot stat `libflashplayer.so': No such file or directory" but the directory is clearly there as I can see it in my documents or on the desktop I tried both.

Any help would be great!!

Also how do I install 
1) mkv player (ex divx) or get the proper codecs
2) get a player to run my mp3...right now they dont work
3) and the other player to play mp4 ect

I have patience and and willing to try many things I just need more knowledge.
 

> **Flash plug-in installation:** 

Flash installation Under 8.04-9.10 can be accomplished using using synaptic, or the command below. All dependencies should be installed automatically. 
 	Code:
 	sudo aptitude install flashplugin-nonfree 
Regarding the native alpha 64-bit flash: This can be manually installed using the below information. Note: This done at your own risk, also make sure you un-install any previous version of flash player you might have installed.
Step one: go to [Adobe Labs Downloads Flash Player 10 for 64-bit Linux]("http://labs.adobe.com/downloads/flashplayer10.html")

Step two: cd to where the file was saved after the download is finished, and untar and uncompressed the tarball using the below command. 
 	Code:
 	tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz 
Step three: Create a plugins directory inside ~/.mozilla using the below command.
 	Code:
 	mkdir ~/.mozilla/plugins 
Step four: Copy the libflashplayer.so  file into this directory:
 	Code:
 	mv libflashplayer.so ~/.mozilla/plugins


---

### Post by skymera on 2010-02-07
Download the file from that Adobe link.
Extract the archive.
Open the folder and move the file to /home/USER/.mozilla/plugins

As for MP3 and Video, when you try and play them a window should pop up asking you to install some codecs.

---

### Post by plucky on 2010-02-07
To install Adobe Flash 10 See [Here](http://www.ubuntugeek.com/adobe-flash-player-10-for-64-bit-linux-released-and-ubuntu-installation-instructions.html)

> Also how do I install
1) mkv player (ex divx) or get the proper codecs
2) get a player to run my mp3...right now they dont work
3) and the other player to play mp4 ect


```
sudo apt-get install ubuntu-restricted-extras
```

Also see [here](https://help.ubuntu.com/community/Medibuntu) for adding the Medibuntu Repository to get the **w64codecs**

Good Luck

---

### Post by nhasian on 2010-02-07
you want the 64 bit version from:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

extract the libflashplayer.so file from the tar archive and then you need to copy it to /usr/lib/mozilla/plugins/ with the following command:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

if you have trouble copying it from the terminal you can use nautilus with the command:

```
gksu nautilus
```

---

### Post by oldos2er on 2010-02-07
> **plucky said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```


You don't really want to run that command on 64-bit; it will overwrite 64-bit flash with 32-bit flash + nspluginwrapper. A better command would be ```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ttf-mscorefonts-installer unrar gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg libavcodec52 libavformat52 libpostproc51 libswscale0 sun-java6-plugin icedtea6-plugin libmp4v2-0
```

---

### Post by savyboy24 on 2010-02-08
Ok I am a little confused now. 

!)So Oldos2er, what will happen if I do what you say and how is that different from nhasian says?

2)Which will play flash the smoothest?

3)What plucky is saying then is only adding the 32 bit on my 64 bit system? 

4)Plucky said I can use these > Also see [here]("https://help.ubuntu.com/community/Medibuntu") for adding  the Medibuntu Repository to get the **w64codecs**  for my MKV, avi ect ect...are these 64 bit plucky? The only reason I ask is I play a lot of 720 and 1080 movies through my comp using divx at the moment and I want to find a way to do this with Ubuntu without losing quality. From what I have read anything is possible it is just a metter of finding and applying.  

Thanks for all you help I am enjoying Ubuntu so far and I am trying to learn all I can!!!!

---

### Post by savyboy24 on 2010-02-08
Can bad things happen if I do this wrong?

---

### Post by oldos2er on 2010-02-08
nhasian gave you instructions on how to install flash. My instructions will install every package except flash in ubuntu-restricted-extras. ubuntu-restricted-extras is a popular package to install since it contains mp3 codec, java, and some other goodies.

I've found 64-bit flash works better for me than 32-bit flash + nspluginwrapper.

---

### Post by Leppie on 2010-02-08
there is a very easy to follow howto on installing flash on x64: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by durand on 2010-02-08
Whats wrong with using Ubuntu Software Center, searching for adobe flash and pressing install? Works here

---

### Post by tom.swartz07 on 2010-02-08
> **durand said:**
> Whats wrong with using Ubuntu Software Center, searching for adobe flash and pressing install? Works here

The official Adobe plugin is better supported for x64 systems. Although the software center version 'works' there are some annoying little glitches (not being able to click things sometimes, weird artifacts, etc)

The official one tends to clear up those problems, and wont use as much CPU when youre running high def videos.

---

### Post by durand on 2010-02-08
> **tom.swartz07 said:**
> The official Adobe plugin is better supported for x64 systems. Although the software center version 'works' there are some annoying little glitches (not being able to click things sometimes, weird artifacts, etc)

The official one tends to clear up those problems, and wont use as much CPU when youre running high def videos.

Oh. I have actually been having those problems but I thought it was just a problem at my end :S Thanks!

---

### Post by tom.swartz07 on 2010-02-08
> **durand said:**
> Oh. I have actually been having those problems but I thought it was just a problem at my end :S Thanks!

HAHA! sure! theres a link in my sig if you need further help- some of the guides ive seen in this thread kinda dance around what you need to do and never specifically say what you need. 

My link will show you what you need to do and how to do it.

---

### Post by durand on 2010-02-08
> **tom.swartz07 said:**
> HAHA! sure! theres a link in my sig if you need further help- some of the guides ive seen in this thread kinda dance around what you need to do and never specifically say what you need. 

My link will show you what you need to do and how to do it.

Yup, did use your link and it's working now. Thanks!

---

### Post by savyboy24 on 2010-02-09
gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:2278): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2278): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2278): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

What does this mean????

---

### Post by savyboy24 on 2010-02-09
WOW...thanks guys...I finally got the flash to install. Now the only problem is it plays very fast like 2x what it should. What do I do now?

---

### Post by savyboy24 on 2010-02-10
> **oldos2er said:**
> nhasian gave you instructions on how to install flash. My instructions will install every package except flash in ubuntu-restricted-extras. ubuntu-restricted-extras is a popular package to install since it contains mp3 codec, java, and some other goodies.

I've found 64-bit flash works better for me than 32-bit flash + nspluginwrapper.

I did what you said and I got the flash working but it works now at like 2 or 3 x speed and I have no sound.

---

### Post by nhasian on 2010-02-10
savyboy24, i'd like for you to give us the output of a few more commands if you dont mind:

first in a terminal type:

```
sudo updatedb
```

then give us the output of:

```
locate libflashplayer.so
```

also i would like the output of:

```
uname -a
```

finally in firefox, in the url type:

```
about:plugins
```

give us the output of that as well.

that should give us all the information we need.

> **savyboy24 said:**
> I did what you said and I got the flash working but it works now at like 2 or 3 x speed and I have no sound.

---

### Post by savyboy24 on 2010-02-10
So this is what I got I did what you said and got this:

maverick@Maverick-laptop:~$ sudo updatedb
maverick@Maverick-laptop:~$ locate libflashplayer.so
/home/maverick/libflashplayer.so
/home/maverick/Documents/libflashplayer.so
/home/maverick/Downloads/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/pluginens/libflashplayer.so
maverick@Maverick-laptop:~$ uname -a
Linux Maverick-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

Then in the URL I got this:

**Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **VLC Multimedia Plugin (compatible Totem 2.28.2)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.28.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.28.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.28.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r42   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
Hope this helps......

---

### Post by savyboy24 on 2010-02-10
So I just installed the proprietary drivers and get the speed normal. But still no sound...

This is my graphics driver info:
maverick@Maverick-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 2.1.9016

---

### Post by savyboy24 on 2010-02-10
Made some adjustments and got sound...does evrything else look ok. Thanks for your help, one thing left how do I get the codec to play my .264 movies. In windows I use the divx pro.

---

### Post by savyboy24 on 2010-02-10
Thanks guys I got it!!!! YAY!!! Now what to do? Can I check to see if my proprietary drivers are are to date?

---

### Post by nhasian on 2010-02-10
It looks like your using the latest version of adobe flash for 64 bit. lets get rid of those other libflashplayer.so files so there is no confusion in the future. You want to delete these:

/home/maverick/libflashplayer.so
/home/maverick/Documents/libflashplayer.so
/home/maverick/Downloads/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so

you only want to keep:

/usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by savyboy24 on 2010-02-10
Thanks...deleted the rest of these files. Now on to other things.
What programs are must have for Ubuntu (games, things to help with schooling ect ect)

---

### Post by chaparrazo on 2010-02-10
i've got a question here if i may: 

my son is whining about one of his games not playing right and we found this thread. 

my about:plugins lists 

Shockwave Flash 9.0 r260 
application/x-shockwave-flash
application/futuresplash

at the top - and 

Shockwave Flash 10.0 b218 at the bottom 
application/x-shockwave-flash
application/futuresplash

at the bottom. does the old version have to be removed or is it possibly interfering with the new? 

Thanks!

---

### Post by bruno9779 on 2010-02-10
I have tried everything possible to get flash working smoothly for some crappy games, and I have found the best results for my box to be:

1 - Installing the official Adobe flash payer 64 bit in firefox as described above.

2 - Add chromium-browser ppa, install it, and follow the prompts to import plugins from firefox. 

(there is a more proper way to install the plugin and having chromium to use it, but this is the easiest way by far).

add the ppa:

```
sudo add-apt-repository ppa:chromium-daily/ppa
```

update, upgrade and install chromium browser:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install chromium-browser
```

and follow the prompts.


This works simply great for me. Firefox, even with the best set-up always has "choppiness" on some sites that in chrome run great,

**EVEN WHEN THEY USE THE SAME PLUGIN!!!!!**
 
I wasn't to happy about a google browser, but the ability of playing every silly flash app with fluidity has conviced me...

---

### Post by Leppie on 2010-02-10
> **chaparrazo said:**
> i've got a question here if i may: 

my son is whining about one of his games not playing right and we found this thread. 

my about:plugins lists 

Shockwave Flash 9.0 r260 
application/x-shockwave-flash
application/futuresplash

at the top - and 

Shockwave Flash 10.0 b218 at the bottom 
application/x-shockwave-flash
application/futuresplash

at the bottom. does the old version have to be removed or is it possibly interfering with the new? 

Thanks!
you may actually want to remove both versions and install the latest available ;)

---

### Post by Leppie on 2010-02-10
> **bruno9779 said:**
> Firefox, even with the best set-up always has "choppiness" on some sites that in chrome run great,
which sites have "choppiness" in firefox for you? i haven't come across any yet...

---

### Post by bruno9779 on 2010-02-10
Many games at [Kongregate]("http://www.kongregate.com/") are only playable on chrome on my box (in sig.).

They are playable in firefox too, but far from smooth, and I have chromium using the same firefox does. (I discover by chance by killing the omnius *exe* process, and getting an error message in chrome with /mozilla/libflash.so)

---

### Post by Leppie on 2010-02-10
hmmm... i don't really play flash games... :P

---

### Post by HappyFeet on 2010-02-10
> **bruno9779 said:**
> Many games at [Kongregate]("http://www.kongregate.com/") are only playable on chrome on my box (in sig.).

They are playable in firefox too, but far from smooth

Kongregate works perfect for me with the 64bit flash plugin. Hmmmmmm.

---

### Post by Leppie on 2010-02-10
[bruno9779]("http://ubuntuforums.org/member.php?u=479264"), how many tabs do you usually open in ff and how many do you open in chrome?
ff uses a bit more resources when opening just a couple of tabs, whereas chrome uses quite a significant amount more resources when like 10+ tabs are opened.

and if you mostly play flash games and browse the web, you may actually be better of with the 32bit system ;)

---

### Post by bruno9779 on 2010-02-12
Lol, I do not play almost any games anymore, except at work, where we have some little competitions, mostly on some flash games.

Responsiveness and fluidity are something else entirely on flash-chrome.

I do not find that chrome uses more resources than firefox. 
If i open 2 or more flash games in FF they are all gonna be rendered also if minimized, adding some nasty choppiness.

Chromium only renders the visible window/tab apparently: if i switch from a flash tab to a text one, resource usage drops greatly, also if flash is just minimized and running.

---

