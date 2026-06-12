---
title: "Flash Trouble"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by bbucsis on 2009-08-20
Hey Everyone. I'm very new with Ubuntu, but not with computers, so I have been able to carefully walk my way through the OSs use so far. However I have been having trouble with Flash on Ubuntu. Sites like youtube, newgrounds, etc do not display properly. Videos on youtube do notplay and the sound is choppy, and games are unable to load whatsoever.

I have downloaded the Ubuntu Restricted Extras which includes Adobe Flash (I think?) and still have not had any luck. I know flash is installed because the videos try to play, along with the games, however it just doesn't seem to WORK.

I tried searching the forums for threads about this but could not find anything amidst the mess.... Please help if you can, or if you have another thread that may hold the solution please point me there so I may read it.

Thank you in advance!

---

### Post by nhasian on 2009-08-20
Hello bbucsis,

what version of ubuntu are you using?  8.04, 9.10?  is it 32-bit or 64-bit?

in your web browser type:

```
about:plugins
```

what does it say for flash?

for example mine says:
> 
    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

---

### Post by bbucsis on 2009-08-20
> **nhasian said:**
> Hello bbucsis,

what version of ubuntu are you using?  8.04, 9.10?  is it 32-bit or 64-bit?

in your web browser type:

```
about:plugins
```what does it say for flash?

for example mine says:

Hi there. I'm running the newest version of Ubuntu, I believe 9.04? 32 bit

And I get this for my flash plugins:
File name:  libswfdecmozilla.so
Shockwave Flash 9.0 r999

---

### Post by lovinglinux on 2009-08-20
> **bbucsis said:**
> Hi there. I'm running the newest version of Ubuntu, I believe 9.04? 32 bit

And I get this for my flash plugins:
File name:  libswfdecmozilla.so
Shockwave Flash 9.0 r999

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by woedend on 2009-08-20
Without trying to confuse you, I too have trouble with flash in a lot of distros or perhaps performance is suffering.  I ALWAYS get it directly from adobe's website in zip format if youd like to remove the version you have and try it -
1 - locate the newest flash for linux from adobes website and download
2 - extract the libflashplayer.so file to the desktop
3 - from terminal I change to the desktop directory(cd Desktop)
4 - sudo mv libflash* /usr/lib/mozilla/plugins
5 - restart firefox

In fact, AFAIK, this is the way it has to be done to get 64 bit to work well.(flash 10 alpha here...works amazing)

---

### Post by bbucsis on 2009-08-20
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

This got it working, thanks so much for the support!

---

### Post by lovinglinux on 2009-08-21
> **bbucsis said:**
> This got it working, thanks so much for the support!

You are welcome.

---

