---
title: "Need program to batch convert wmv files"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by salima on 2010-09-08
I have tried everything i could find searching threads and added all the packages and restricted extras and vlc still will not play my wma's.    I need a batch conversion, but even a one on one basis would be easier than playing each cd and copying to the hard drive, i think...   What simple program can i use to convert wma files to anything else that will play on vlc? I have backup for 100 cd's and i am not finding any way to use the wma files. Since they are so windows specific i would just as soon convert them to something else.

---

### Post by Achilles124 on 2010-09-08
Transmageddon comes to my mind, although I have never used it.

Avidemux is another.

---

### Post by mc4man on 2010-09-08
> I have backup for 100 cd's and i am not finding any way to use the wmv files
Are these wmv (video) or wma (audio only) and either way what is the audio - wma2, wmap (wma3pro), or wmal (lossless

---

### Post by salima on 2010-09-08
sorry about that, they are wma files. when i click on properties on them all it tells me is wma. i dont know what format the cd's are in, but i played them with the windows media player on a windows machine (xp pro) years ago and copied them to the hard drive, wma is what they ended up.

---

### Post by spjackson on 2010-09-08
ffmpeg can convert from wma files.

---

### Post by andrew.46 on 2010-09-08
Hi Salima,

Are you running 32 or 64 bit Ubuntu? I have a suspicion that MPlayer + SMPlayer + w32codecs might play your files without the need for conversion...

Andrew

---

### Post by 0N3 on 2010-09-08
Soundconverter simple tool installed on Ubuntu to convert most formats to any format you want.Its under Applications>Sound & Video
can convert more then one at a time think it supports drag and drop too!

---

### Post by 0N3 on 2010-09-08
If its not installed open up Synaptics package manager and search for it soundconverter all one word and mark it for installation

---

### Post by beew on 2010-09-08
WINFF? (a gui frontend to ffmpeg) I never done batch conversion but its option allows you to input a list instead of just a single file.

---

### Post by jtarin on 2010-09-08
Out of curiosity, did you also do research on VLC forum? VLC is known for playing not only these but many other [file types]("http://www.videolan.org/vlc/features.php?cat=audio"). I have a suspicion you have either a bad file or VLC is missing something.

> 1. Native playback supported by VLC 1.0.3 and later. Previous versions could use Windows DMO codecs on 32-bit x86 platforms and allow WMV-3/WMA-3 decoding. This feature was never tested on Intel-based Macs.

---

### Post by salima on 2010-09-09
hi- thanks for the answers, everyone...  i am downloading the soundconverter now from the software center to see if that works.     when i added vlc, i looked into a lot of threads here and added all the things they said...also saw a thread where they said it should be installed in a particular way, so i uninstalled and redid it that was in order to be sure all the right apps were in the right place. but it doesnt play.     i have spent some time on this, and i am thinking conversion may be faster...also i may never have the need to play wma files other than this.   i may check out WINFF-i dont want to get into anything too complicated, i dont do any editing or fancy stuff.     and by the way, i do have 32 bit pc...if i am reading this right: root@salima-desktop:~# lshw  salima-desktop                 description: Desktop Computer      product: P5GC-TVM-SI      vendor: HCL Infosystems Limited      version: System Version      serial: 7073A1002932      width: 32 bits      capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp      configuration: boot=normal chassis=desktop cpus=2 uuid=18F30839-0E12-DC11-ABF0-0C2CFBD7E124   after this first part, 64 bit is mentioned in different places, which confused me, but i think the answer i am supposed to give is still 32 bit.   why am i not able to get spaces in my posts between paragraphs?

---

### Post by seventhsamurai on 2010-09-09
Go to Synaptic Package Manager, search for gnome-Mplayer and install. It plays wma, wmv files perfectly fine for me.

---

### Post by salima on 2010-09-09
> **seventhsamurai said:**
> Go to Synaptic Package Manager, search for gnome-Mplayer and install. It plays wma, wmv files perfectly fine for me.

 i already have it...but when it starts to try and play the file there are a few clicking sounds and then it stops...    from the sticky tutorial (steps 1-5) i had made some changes. maybe something has to be undone now...dont quite understand the messages below on exactly how to remove things  i added medibunto and came across these erros in the log:  W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783   and The following packages were automatically installed and are no longer required:    linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic  Use 'apt-get autoremove' to remove them.    then when i installed gecko i got these errors: The following packages were automatically installed and are no longer required:    linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic  Use 'apt-get autoremove' to remove them.

---

### Post by seventhsamurai on 2010-09-09
Wow! Sounds like quite a mess you have there. I have never had any issues playing wmv files in 32 or 64 bit ubuntu systems.

Trying using winff, handbrake, transmageddon or the likes to convert it to mp4.

Have you checked the wmvs on another system? Are you sure the files arent corrupted?

---

### Post by kevdog on 2010-09-09
I wouldn't worry about those errors you are getting with the package manner.  They can be rectified later and do not have any bearing on the wma ability to play.  As suggested above I would verify you can plays these files on a windows or other machine.  I suspect they may also be corrupted for some strange reason.  If you have multiple copies of the files, you could always compare file signatures with md5sums or sha1sum to see if the file signatures match --- if they don't = corruption.

---

### Post by qyot27 on 2010-09-09
Just because VLC, mplayer, et al are capable of decoding Windows Media Audio does not mean they can necessarily play your .wma files.  If you leave Windows Media Player on its defaults when ripping to WMA, then it encrypts them, and with that in mind, you're up a creek without a paddle.

VLC and the others will only play non-encrypted files.  And the reports of clicking sound very much like what happens when trying to play an encrypted file you don't have the keys for.

---

### Post by andrew.46 on 2010-09-09
Hi salima,

You seem to be getting advice from everywhere :). To tell if you have a 64 bit system or not try the following command, which I have highlighted in red:

```

andrew@ilium:~$ **[COLOR="Red"]uname -m[/COLOR]**
x86_64

```

This is what will show with a 64 bit system, a 32 bit system will return *i686*. (Mind you if qyot is right about encryption/drm all of this will not be helpful unfortunately).

Andrew

---

### Post by salima on 2010-09-09
> **andrew.46 said:**
> Hi salima,

You seem to be getting advice from everywhere :). To tell if you have a 64 bit system or not try the following command, which I have highlighted in red:

```

andrew@ilium:~$ **[COLOR=Red]uname -m[/COLOR]**
x86_64

```This is what will show with a 64 bit system, a 32 bit system will return *i686*. (Mind you if qyot is right about encryption/drm all of this will not be helpful unfortunately).

Andrew

i am probably not understanding the command line right-is this what i was supposed to type?
salima@salima-desktop:~$ salima -m x86_64
well, obviously not because i was told 'command not found' and i tried a few variations...i would like to be really sure what system i have!

it will take a couple days to find someone to play my files, but i can put some on a pen drive and try that.

the cd's play in the cdrom drive...some of them are actual store bought copies and some were made for me by friends. but i will check that out. there are 100 cd's and they are probably not uniform, so checking one with md5sum wouldnt tell me if they were all ok...wow, now i am trying to remember if i didnt have to go back to the pc file to create a new cd for a couple of them-loaned out one and it wasnt returned, one developed a scratch, etc...they might be irreplaceable.

so if the idea is trying to save time, out of the three options; convert the files, figure out how to play what i have without converting them or just copy them over again...do you think i should just start them playing one at a time and copy them? if i go that route, what should i use to copy and what file format should i use? i have brasero of course and i am downloading K3b

---

### Post by spjackson on 2010-09-09
> **salima said:**
> i am probably not understanding the command line right-is this what i was supposed to type?
salima@salima-desktop:~$ salima -m x86_64
well, obviously not because i was told 'command not found' and i tried a few variations...i would like to be really sure what system i have!

It's not salima -m, it is literally
```

uname -m

```as posted by andrew.46.

---

### Post by salima on 2010-09-09
> **qyot27 said:**
> Just because VLC, mplayer, et al are capable of decoding Windows Media Audio does not mean they can necessarily play your .wma files.  If you leave Windows Media Player on its defaults when ripping to WMA, then it encrypts them, and with that in mind, you're up a creek without a paddle.

VLC and the others will only play non-encrypted files.  And the reports of clicking sound very much like what happens when trying to play an encrypted file you don't have the keys for.

aha-that does seem to be the case. now i see an error comes up when i try to play the files in mplayer telling me that they are in fact encrypted. 

do you mean keys in a metaphorical sense, or are there some keys i can download? if it is not possible to play them then i can go on to plan b...make new files from the cd's. 

i wonder what happened to the cd i made from the encrypted file? (i think i did that iwht one of them). it plays on my dvd player...will i be able to copy that with a cd burning program and make it a different format?

---

### Post by salima on 2010-09-09
> **spjackson said:**
> It's not salima -m, it is literally
```

uname -m

```as posted by andrew.46.

thanks both to you and andrew!
i now know for sure that i have a 32 bit system...

---

### Post by jtarin on 2010-09-09
> **salima said:**
> ```
uname -m
```

Maybe it should be ```
What's uname?
```:lolflag:

---

### Post by qyot27 on 2010-09-10
> **salima said:**
> do you mean keys in a metaphorical sense, or are there some keys i can download? if it is not possible to play them then i can go on to plan b...make new files from the cd's.
The encryption scheme that Windows Media uses relies on a set of data keys that are uniquely generated for every file when created.  These are stored locally in one of the Application Data folders in Windows, although verification might be able to be redone online if it was tied to a username/password combo.  Otherwise, if you lose the keys (say, because Windows was reinstalled), you lose the ability to play them back.

> i wonder what happened to the cd i made from the encrypted file? (i think i did that iwht one of them). it plays on my dvd player...will i be able to copy that with a cd burning program and make it a different format?
If the disc made from the encrypted files was made with Windows Media Player, plays on CD or DVD player standalones, and the format registers as PCM, then those are fine.  If the disc stores actual .wma files, it's still probably locked down by the same encryption problem.

So basically, it looks to me that you'll probably have to re-rip everything.  My suggestion would be to choose Vorbis as the format this time, or MP3 if you're concerned about portable music player support (although if said device is an iPod, then you could also choose AAC).  I'm sure Rhythmbox can handle Vorbis or MP3 just fine.

---

### Post by salima on 2010-09-10
> **qyot27 said:**
> The encryption scheme that Windows Media uses relies on a set of data keys that are uniquely generated for every file when created.  These are stored locally in one of the Application Data folders in Windows, although verification might be able to be redone online if it was tied to a username/password combo.  Otherwise, if you lose the keys (say, because Windows was reinstalled), you lose the ability to play them back.


If the disc made from the encrypted files was made with Windows Media Player, plays on CD or DVD player standalones, and the format registers as PCM, then those are fine.  If the disc stores actual .wma files, it's still probably locked down by the same encryption problem.

So basically, it looks to me that you'll probably have to re-rip everything.  My suggestion would be to choose Vorbis as the format this time, or MP3 if you're concerned about portable music player support (although if said device is an iPod, then you could also choose AAC).  I'm sure Rhythmbox can handle Vorbis or MP3 just fine.

i cant even remember if the files played ok on my new (two years old now) desktop-they were originally made on a laptop, and the new desktop is where i now sit with windows deleted forever (and good riddance). the old laptop is just about dead and only needs to be wiped and buried.

then i will go for starting over. i think vorbis plays on vlc, and i always wanted vorbis files anyway, i like the name. 

what is the best application to use for copying the cd's into vorbis format to store on the hard drive? all i have so far is brasero, i was going to install K3b, but if you have a better idea let me know. 
thanks!

---

### Post by jtarin on 2010-09-10
If you want something that will do the job with simplicity and don't need all the bells and whistles I would recommend Gnome Baker.I've used Brasero and K3B....Brasero not again...K3B works best if your running KDE. Gnome Baker isn't multi-session yet but its slated for the future. It's the only thing I miss.

---

### Post by qyot27 on 2010-09-10
That's why I mentioned Rhythmbox, actually - it should be able to rip to Vorbis.  I'm not certain about that, though, since my CD ripping workflow is more involved than simply letting the player save tracks in X format (the aforementioned workflow: bit-exact or near-bit-exact* image creation->Parse image to PCM Wave files->encode to destination format).

*insofar as ditching any CD-EXTRA data and just keeping the audio is considered bit-exact, anyway.

---

### Post by salima on 2010-09-10
i didn't realize rhythmbox could do that-i guess the same as mediaplayer did it for me before. i will also download gnomebaker so i have two to choose from and see what works best.

thanks everyone for the help, i will mark this thread closed...

---

### Post by MooPi on 2010-09-10
This is a script that I use that utilizes mplayer and oggenc. I believe you will need to have restricted formats enabled.
```
#!/bin/bash
mplayer -vc null -vo null -ao pcm:fast **.wma && oggenc -q 10 **.wav && rm audiodump.wav **.wma
```

---

