---
title: "MP3's won't play"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by fatjax on 2011-07-26
I had always waited to switch to linux until the bugs were worked out. I swear I thought it was ready.

Everything works except playing music files. Banshee said it needed plugins or codecs or something so I told it to install. It found 3 codecs labeled Bad and Ugly or something. I installed them and it said they installed but It wasn't what it needed. I try to play the music files and it just sits there, no error messages or anything.

I tried Amorok too and got the same problem.

I'm using Ubuntu 11.4. Would suse be better off for me? I always heard that Ubuntu was better for laptops...

p.s. I took a linux class in Networking school but that was a while back. I don't really remember anything from it.

---

### Post by coffeecat on 2011-07-26
Welcome to the forum.

Quick answer. Install the metapackage ubuntu-restricted-extras. This will bring in most of the restricted codecs (including for mp3) you need as well as Java, flash and Microsoft core fonts.

**EDIT**: or if you just want to support mp3, install the package gstreamer0.10-fluendo-mp3

---

### Post by Cavsfan on 2011-07-26
Try Rhythmbox. It works with MP3s and WMAs also. Just install the plugins as well.

There is also a conkyrhythmbox that displays info about the song that is playing.

Edit: My bad, coffeecat is most probably correct.

---

### Post by astrobob.tk on 2011-07-26
> **fatjax said:**
> I had always waited to switch to linux until the bugs were worked out. I swear I thought it was ready.

Everything works except playing music files. Banshee said it needed plugins or codecs or something so I told it to install. It found 3 codecs labeled Bad and Ugly or something. I installed them and it said they installed but It wasn't what it needed. I try to play the music files and it just sits there, no error messages or anything.

I tried Amorok too and got the same problem.

I'm using Ubuntu 11.4. Would suse be better off for me? I always heard that Ubuntu was better for laptops...

p.s. I took a linux class in Networking school but that was a while back. I don't really remember anything from it.

Welcome to the community,

Do not be frustrated with a problem here & another there, all newbies will. In the overall experience you will have made the righ decision in movign to Ubuntu (the most popular distro)

To solve your problem, run (before running it wait for other replies for alternatives &/or confirmation of my command) the following command in a terminal:

```
sudo aptitude install libdvdnav4 libdvdread4 gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

You will be asked to enter a password (your user pass) which you will not see being typed while entering it.

This command should install all popluar codecs. It works on my 10.04 LTS & i assume it should on yours.

all the best

---

### Post by fatjax on 2011-07-26
how do I find out if I have the 64bit version of ubuntu?

---

### Post by kaldor on 2011-07-26
> **fatjax said:**
> how do I find out if I have the 64bit version of ubuntu?

Open the Terminal program and type:

```
uname -a
```

If it says x86_64 anywhere, it is 64-bit.

To install codecs and other addons, install "ubuntu-restricted-extras" in the Software Centre.

Edit: I am assuming that CoffeeCat's suggestion for *ubuntu-restricted-extras* worked. If not, please let us know :)

---

### Post by Swagman on 2011-07-26
uname -a

if it says i686 or i386 your running 32 bit. If it says x86_64 your running 64 bit

[edit]

I must've been beaten by milliseconds with that reply..

ok.. Quick way to get a terminal is

ctrl + alt +t

---

### Post by fatjax on 2011-07-26
man, you guys are handy. Ok here's one more, I'm about to try the mp3's.

I'm wanting to rip dvd's. Thoggen says I need a decryption library. I already installed you guyses library package. DVD::rip and Acidrip just error w no message..

---

### Post by fatjax on 2011-07-26
ok mp3's work great. thanks.

---

### Post by westie457 on 2011-07-26
> **fatjax said:**
> man, you guys are handy. Ok here's one more, I'm about to try the mp3's.

I'm wanting to rip dvd's. Thoggen says I need a decryption library. I already installed you guyses library package. DVD::rip and Acidrip just error w no message..

Give k3b a try. Install with Software Centre or with Synaptic Package Manager.

---

### Post by fatjax on 2011-07-26
OK. I'm just gonna skip the dvd decrypting I don't really need that. Problem is however, that I cannot watch dvd's either. Same error. DVD is encrypted, no decryption library.

---

### Post by westie457 on 2011-07-26
> **fatjax said:**
> OK. I'm just gonna skip the dvd decrypting I don't really need that. Problem is however, that I cannot watch dvd's either. Same error. DVD is encrypted, no decryption library.

Okay try VLC. I think that has decryption for Region Codes built-in. Install the same way as k3b. Another one that might work is kaffeine.

---

### Post by 3602 on 2011-07-26
> **Cavsfan said:**
> Try Rhythmbox. It works with MP3s and WMAs also.
I'm just here to say thank you. I didn't know that Rhythmbox provided built-in MP3 support. I was wondering how my MP3 files played while I didn't install any Fluendo package.

---

### Post by coffeecat on 2011-07-27
> **fatjax said:**
> OK. I'm just gonna skip the dvd decrypting I don't really need that. Problem is however, that I cannot watch dvd's either. Same error. DVD is encrypted, no decryption library.

Install libdvdcss2 to read encrypted DVDs. It's not in the Ubuntu repositories because of legal issues. Either enable the medibuntu repository:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Or use the commands in this link:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Cavsfan on 2011-07-27
> **3602 said:**
> I'm just here to say thank you. I didn't know that Rhythmbox provided built-in MP3 support. I was wondering how my MP3 files played while I didn't install any Fluendo package.

You are welcome! I love Rhythmbox and if you don't like the way it opens and goes to the top task bar, or does not close when 
you click the X to close it. Just open up **gconf-editor** and click **apps/Rhythmbox/plugins/status-icon** and look at the value of **status-icon-mode**. 
It's default is 3 and I changed mine to 0.

When I open Rhythmbox, it opens, when I close it, it just closes. None of that disappearing into a tray icon stuff which is default.

---

### Post by Cavsfan on 2011-07-27
You should also look into conkyrhythmbox in here: [[COLOR=blue]_Conky Ryhthmbox_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5843297").
It provides a lot of info about the song that is playing along with album art. 
I could give you what I am using but, probably not in this thread. 
I believe my Conky for Rhythmbox is in that thread about page 36.

---

### Post by Don D on 2011-08-26
> **astrobob.tk said:**
> Welcome to the community,

Do not be frustrated with a problem here & another there, all newbies will. In the overall experience you will have made the righ decision in movign to Ubuntu (the most popular distro)

To solve your problem, run (before running it wait for other replies for alternatives &/or confirmation of my command) the following command in a terminal:

```
sudo aptitude install libdvdnav4 libdvdread4 gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

You will be asked to enter a password (your user pass) which you will not see being typed while entering it.

This command should install all popluar codecs. It works on my 10.04 LTS & i assume it should on yours.

all the best
in your CL is included  ...    w32codecs ;          If i'm on a 64-bit machine, do i also include ...             w64codecs              ?
thx in advance; take care

---

### Post by astrobob.tk on 2011-08-27
> **Don D said:**
> in your CL is included  ...    w32codecs ;          If i'm on a 64-bit machine, do i also include ...             w64codecs              ?
thx in advance; take care

mmh; well a quick google search gave me this page: [https://help.ubuntu.com/community/Medibuntu#Playing Non-Native Media Formats](https://help.ubuntu.com/community/Medibuntu#Playing Non-Native Media Formats)

Indeed, it seems u need to use w64codecs instead.

First make sure your system (& not just the hardware) is 64 bit: uname -a (if i686 or i386 then it is 32 bit; if x86 then its 64).

---

