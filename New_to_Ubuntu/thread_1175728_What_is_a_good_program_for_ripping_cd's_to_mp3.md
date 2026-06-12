---
title: "What is a good program for ripping cd's to mp3"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by TheBootstrapKid on 2009-06-01
right now i am using rhythmbox.  it seems kinda slow.

---

### Post by dje on 2009-06-01
you could try sound juicer, open a terminal (Applications >> Accessories >> Terminal) and run:
```
sudo apt-get install sound-juicer
```
Then open Applications >> Sound & Video >> Audio CD Extractor

dje

---

### Post by steeleyuk on 2009-06-01
Sound Juicer usually works fine. Rhythmbox usually rips pretty well, and imports directly into your library as a plus.

---

### Post by Gazneth on 2009-06-01
Maybe try soundjuicer, it works ok for me. My favorite ripping program is CDex which unfortunately is windows only.

---

### Post by gn2 on 2009-06-01
My favourite is Grip.

---

### Post by MrWES on 2009-06-01
> **TheBootstrapKid said:**
> right now i am using rhythmbox.  it seems kinda slow.

ABCDE -- command line, but solid and fast.

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

---

### Post by Therion on 2009-06-01
Just one more suggestion: **GnomeBaker**

It's in the repo, it's easy and it's gnome/gui based.

---

### Post by logos34 on 2009-06-02
I would recommend you NOT to use sound-juicer, especially for mp3, as [detailed here]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding").  Settings config is needlessly confusing (i.e. pipelines), and unless there's been an update, the gstreamer backend will screw up lame vbr output.  A lot of people are blissfully unaware of the problems.  (I've managed to fix mp3 vbr output--*I think*--only by reverting to an earlier gstreamer lame plugin, gstreamer0.10.5.2-plugins-ugly-multiverse).

Use rubyripper (esp. if you want secure rips), abcde or grip

---

### Post by laffinet on 2009-06-02
> **MrWES said:**
> ABCDE -- command line, but solid and fast.

+1 for abcde

Don't let the fact that it's only command line and not GUI turn you away. Once you set it up properly (by editing/creating a config file) it's as simple as plopping in the CD, typing "abcde" in a terminal and Bob's your uncle. 

A few minutes later you have your mp3s in a designated folder, nicely tagged to your liking. Simple, fast, reliable. Love it.

---

### Post by binbash on 2009-06-02
Sound Juicer is good for flac etc but not mp3s

---

### Post by billgoldberg on 2009-06-02
I always use RipperX.

Easy to use and fast.

---

### Post by MichaelSammels on 2009-06-02
I tend to  use abcde

---

### Post by RichardG891 on 2009-06-02
I use ruby ripper, same as logos34 - very slowwww though. Some people have managed to get Exact Audio Copy working under WINE.

---

### Post by sica07 on 2009-06-02
+1 RipperX
Intuitive interface, easy to use and quite fast.

---

### Post by TheBootstrapKid on 2009-06-02
i installed GRIP.  it is ripping to .ogg.  How do i change it to mp3

---

### Post by sica07 on 2009-06-02
[Soundconverter]("http://soundconverter.berlios.de/") it's all that you need.

---

### Post by gn2 on 2009-06-02
> **TheBootstrapKid said:**
> i installed GRIP.  it is ripping to .ogg.  How do i change it to mp3


Config > Encode > Encoder, set to Lame, then in Options you can set the bitrate.

In Config > Rip you can set it to auto rip on insert and auto eject when finished.

---

### Post by steeleyuk on 2009-06-02
> **sica07 said:**
> [Soundconverter]("http://soundconverter.berlios.de/") it's all that you need.

Sound Converter doesn't rip CDs. Its only... converts.

---

### Post by sica07 on 2009-06-02
> **steeleyuk said:**
> Sound Converter doesn't rip CDs. Its only... converts.
I know that. I just thought that: GRIP-rip to ogg && Soundconverter-converts to mp3. (I don't know if GRIP can rip in mp3 format. I never use it)

---

### Post by TheBootstrapKid on 2009-06-02
> **gn2 said:**
> Config > Encode > Encoder, set to Lame, then in Options you can set the bitrate.

In Config > Rip you can set it to auto rip on insert and auto eject when finished.

I did this and now i'm getting the following warning:
Invalid encoder executable
check your encoder config, and ensure that it specifies the full path to the encoder executable.

---

### Post by oldos2er on 2009-06-02
> **TheBootstrapKid said:**
> I did this and now i'm getting the following warning:
Invalid encoder executable
check your encoder config, and ensure that it specifies the full path to the encoder executable.

 Do you have lame installed?

---

### Post by gn2 on 2009-06-02
Run this in a terminal to install Lame and the error should disappear.

```
sudo apt-get install lame
```

---

### Post by TheBootstrapKid on 2009-06-03
I have lame installed and i am still getting the same message.

the encoder is Lame

the encoder executable is Lame

the encoder commandline reads -h -b %b %w %m

the file extension is mp3

and the file format reads ~/ogg/%A/%d/%n.%x

what gives?

---

### Post by oldos2er on 2009-06-03
The encoder executable should be /usr/bin/lame

---

### Post by techstop on 2009-06-03
Here's a great tutorial on how to set up grip in our very own tutorial forum;

[http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

---

