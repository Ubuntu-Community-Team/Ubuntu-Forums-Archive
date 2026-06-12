---
title: "Convert flac to ogg useing aoTuV."
date: 2008-12-27
forum: New to Ubuntu
---

### Post by osc1882 on 2008-12-27
That's it. That's all I need to do. I already have aoTuV downloaded and i'm useing it to rip cd's to ogg with Ruby Ripper. But I need to convert some flac to that format and I spent a good hour searching online and these forums and I still don't know how to do it. Can anyone please help, pretty please.

---

### Post by Hospadar on 2008-12-27
i would look into mencoder, It can do just about  anything in terms of trancoding

---

### Post by andrew.46 on 2008-12-27
Hi osc1882,

> **osc1882 said:**
> That's it. That's all I need to do. I already have aoTuV downloaded and i'm useing it to rip cd's to ogg with Ruby Ripper. But I need to convert some flac to that format and I spent a good hour searching online and these forums and I still don't know how to do it. Can anyone please help, pretty please.

Unfortunately I am not familiar with aoTuV. But if nobody can guide with this an alternative is using oggenc. You will need the vorbis-tools package:

```
$ sudo apt-get install vorbis-tools
```

and the syntax to convert the files is pretty straightforward:

```
$ oggenc -q 6 input.flac -o output.ogg 
```

with 'input' and 'output' being names of your choice of course. You do not have to specify the '-o' option as oggenc will simply name the output file 'input.ogg'.

Andrew

---

### Post by ubuntu27 on 2008-12-27
How about trying **OggConvert**?

[OggConvert]("http://oggconvert.tristanb.net/") is a small GNOME utility which uses GStreamer to convert
(almost) any media file to the patent-free Ogg Vorbis, Theora and
Dirac formats.

```
sudo apt-get install oggconvert
```

Homepage: [http://oggconvert.tristanb.net/](http://oggconvert.tristanb.net/)

Linux.com review (2007): [http://www.linux.com/feature/123574](http://www.linux.com/feature/123574)

---

### Post by osc1882 on 2008-12-27
I really should be aoTuV. I'll give mencoder a look.

---

### Post by osc1882 on 2008-12-27
Man.... I need a GUI for this program. or a little help or something.

---

### Post by jocheem67 on 2008-12-27
Don't stick to a program that won't do it for you.
There's enough alternatives:

Soundconverter
Oggconvert

They both are simple to use, with GUI

If you're using Kubuntu, there's Soundkonverter...

---

### Post by osc1882 on 2008-12-27
I have both of those programs and they don't let you choose your own encoder (aoTuV), it just uses whatever is already installed in ubuntu.

---

### Post by jocheem67 on 2008-12-27
Well I noticed that it's possible to compile an aotuv ogg encoder under linux.
One can choose to overwrite the ubuntu own libs, which are I guess the official ones from xiph.org. It should be possible then to use the overwritten ogg libs from the command-line.

However you have to know what you're doing. Documentation is pretty rudimentair.

[http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV](http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV)

I don't really see the need for using the altered ogg enc. But you could ofcourse try....Cheers:)

---

### Post by logos34 on 2008-12-27
> **osc1882 said:**
> I have both of those programs and they don't let you choose your own encoder (aoTuV), it just uses whatever is already installed in ubuntu.

> **jocheem67 said:**
> One can choose to overwrite the ubuntu own libs, which are I guess the official ones from xiph.org.

it's the standard now (since hardy). I'm pretty sure, that is, because I went through a lot of trouble to switch 9 months ago, only to have the devs change to the aotuv b5 encoder for Hardy.  When I upgraded I switch the paths from /usr/local/bin (where I had my aotuv back to the default /usr/bin.  

So whether you rip or convert it will call the default oggenc2 in your path (/usr/bin):

Check a converted file 

ogginfo file.ogg

and you should see

> Vendor: AO; aoTuV b5 [20061024] (based on Xiph.Org's libVorbis)

instead of 

> Vendor: Xiph.Org libVorbis I 20070622 (1.2.0)

---

### Post by jocheem67 on 2008-12-30
I managed to use the aotuv oggenc to convert a flac to ogg..

I used foobar with wine and the win32 aotuv encoder....

Very neat as I may say so.:guitar:

```
Verwerken bestand "Aren't You Kinda Glad We Did.ogg"...

Nieuwe logische stroom (#1, serienr: 000062f9): soort vorbis
Vorbis koppen ingelezen voor stroom 1, informatie volgt...
Versie: 0
Maker: AO; aoTuV b5c [20081215] (based on Xiph.Org's libVorbis)
Kanalen: 2
Frequentie: 44100

```

Hope the topicstarter will see this, as foobar is easily installed with wine. I already did some converting to mp3 from cd with wine/foobar, and it's good to know that it's also capable of converting to ogg using aotuv.

By the way, I had to rename the aotuv encoder to "oggenc.exe" in order to let foobar recognize it.

---

### Post by doug1212 on 2008-12-30
Hi,
Here is a PPA back port repo for aotuv oggenc:

[HTML]https://launchpad.net/~pjssilva/+archive[/HTML]

I use this nautilus extension to convert flac to ogg for my dap:

[HTML]http://phorolinux.com/nautilus-flac-converter-convert-flac-to-ogg-from-nautilus.html[/HTML]

Have fun,
Doug.

---

### Post by osc1882 on 2008-12-31
Sorry to say that hardy seems to still use the old ogg:

grammatrain@tprb:~/Desktop$ ogginfo t.ogg
Processing file "t.ogg"...

New logical stream (#1, serial: 49498d4c): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: Xiph.Org libVorbis I 20070622
Channels: 2
Rate: 44100

Nominal bitrate: 256.000000 kb/s
Upper bitrate not set
Lower bitrate not set
User comments section follows...
	ARTIST=All Star United
	TITLE=Smash Hit
	ALBUM=Smash Hits
	GENRE=Unknown
	TRACKNUMBER=1
	TRACKTOTAL=15
Vorbis stream 1:
	Total data length: 6495304 bytes
	Playback length: 3m:26.186s
	Average bitrate: 252.016451 kb/s
Logical stream 1 ended


I'll try this foobar but i would like to get aoTuV as my default inside of Ubuntu.

---

### Post by logos34 on 2008-12-31
> **osc1882 said:**
> Sorry to say that hardy seems to still use the old ogg:

grammatrain@tprb:~/Desktop$ ogginfo t.ogg
Processing file "t.ogg"...

New logical stream (#1, serial: 49498d4c): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: Xiph.Org libVorbis I 20070622
Channels: 2
Rate: 44100



I wish I knew how I ended up with aoTuVb5 as the default...if only I'd written down the steps I went through...hmm

EDIT:  maybe I patched the libvorbis like this:

[http://www.hydrogenaudio.org/forums/index.php?showtopic=67477](http://www.hydrogenaudio.org/forums/index.php?showtopic=67477)

---

### Post by jocheem67 on 2008-12-31
Well, using wine is not that "un-linux"

Here's a mini-howto:

Install wine from the repo's

Go to applications --- configure wine --- sound

I use alsa as backend and have turned on emulation ( it's down in the menu )
I also use alsa from the ubuntu sound-preferences ( preferences --sound you know? I don't like this pulse stuff )

Download foobar to your home folder or desktop

[http://www.foobar2000.org/?page=Download](http://www.foobar2000.org/?page=Download)

Rightclick the exe and install foobar

I let wine/foobar create a desktop icon which goes to my homefolder, You can drag it to your desktop then....

The possibility to convert files is installed by default, however when installing foobar you'll get some options like file-operations and freedb-tagging and archive-reading...these can be very handy!

Fire up foobar.

First time there's the possibility to use a certain layout, the first option is pretty neat already..

Well to convert then:

foobar ---- files ---- add files

Rightclick the file(s).

Convert --- this will lead you to the converter setup, where it all happens.

Oops, we'll need ofcourse the encoder..

[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)

We're using the win32 ref library, you can down it to your desktop or so....
Important, you have to rename it to "oggenc.exe" after unzipping it.

Back to foobar and the converter menu.

Chosse ogg from the menu, at the right you can control your quality settings. There are way more options like location of the converted file and the naming of it , and so on...

Next, foobar will ask you to locate "oggenc.exe" Point the prog to it....
( The renamed aotuv ).

There you go...

[http://ubuntuforums.org/showthread.php?t=904145&page=2](http://ubuntuforums.org/showthread.php?t=904145&page=2)

This is an other thread concerning foobar and converting....fyi:D

---

### Post by sojyujai on 2009-02-01
Late, but better late than never...
There's a really easy way to get aotuv support for ogg vorbis by default in ubuntu - doug1212 mentioned it above, but I'll give a bit more detail:

A while ago a user named pjssilva incorporated the aotuv tunings into the ubuntu vorbis libraries and set up a ppa repository with the binaries.  Here's the original thread where it's described in more detail:
[http://ubuntuforums.org/showthread.php?t=651980]("http://ubuntuforums.org/showthread.php?t=651980")

The repo was originally set up for gutsy but it's still working fine for intrepid. It's simple to use.  For intrepid go to 'System > Administration > Software Sources' and click the 'Third Party Software' tab.  Click 'Add' and enter this line:
deb [http://ppa.launchpad.net/pjssilva/ubuntu](http://ppa.launchpad.net/pjssilva/ubuntu) intrepid main

You can now just wait for your automatic updates, or if you're impatient run an apt-get update/upgrade.

Afterwards any software that uses Ubuntu's vorbis libraries (soundconverter, sound-juicer, oggenc...) for encoding ogg vorbis will make use of the aotuv tunings.

---

### Post by ariel on 2009-11-22
> **osc1882 said:**
> That's it. That's all I need to do. I already have aoTuV downloaded and i'm useing it to rip cd's to ogg with Ruby Ripper. But I need to convert some flac to that format and I spent a good hour searching online and these forums and I still don't know how to do it. Can anyone please help, pretty please.

for what is worth... I wrote a small howto for aotuv compilation from sources and installation in Ubuntu a while ago, still working fine under karmic
It is here: [http://ubuntuforums.org/showthread.php?t=1137670](http://ubuntuforums.org/showthread.php?t=1137670)

---

