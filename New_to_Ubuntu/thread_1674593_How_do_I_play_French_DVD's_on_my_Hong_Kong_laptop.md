---
title: "How do I play French DVD's on my Hong Kong laptop"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by emailadress on 2011-01-24
Dear all!

I want to play French DVD's on my laptop which I bought in Hong Kong. If I remember correctly from Windows, there is a way to change the settings of the built in DVD player to work for a different country setting. I also remember that one could only do that a couple of times before it was locked. Is this a hardware issue? I use an HP ProBook 4415s and when I insert DVD's it starts and stops a couple of times, then does nothing.

I would appreciate your help very much!

cheers,
Jakob

p.s.: Please redirect me if there already is a thread like this, I usually solve my problems without having to ask again. This time, however, google or the search here didn't help me.

---

### Post by mastablasta on 2011-01-24
did you install libdvdcss2 found in medibunti repositories?

---

### Post by bioterror on 2011-01-24
I've never had problems playing another region DVD's, but this is a good to have.
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")

---

### Post by emailadress on 2011-01-24
thanks a lot for the quick answers! 

@mastablasta:
I followed this guide: 

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

libdvdread4 was already installed as I could see in the Synaptic Package Manager, so I just copied the last two command lines given. The Terminal did something, installed something and didn't give me error messages, so I guess I installed it... ;-)

This did not solve the problem, however. 

Maybe my DVD player is just shitty?

edit:

@bioterror: the command given there tells me, that "libdvdcss2 is already the newest version", guess this answers the question above as well...
[IMG]http://img710.imageshack.us/i/screenshotvad.png/[/IMG]

---

### Post by NightwishFan on 2011-01-24
Run:
```
sudo sh /usr/share/doc/libdvdread4/install-css.sh
```

All should be well.

---

### Post by cascade9 on 2011-01-24
If you've got libdvdcss/libdvdread installed, and it will play DVDs from HK, then you've probabyl got a DVD drive that is region locked. 

[http://en.wikipedia.org/wiki/DVD_region_code](http://en.wikipedia.org/wiki/DVD_region_code)

I've seen people say that libdvdcss doesnt need to have a region set- 

> According to [http://developers.videolan.org/libdvdcss/index.html](http://developers.videolan.org/libdvdcss/index.html), libdvdcss (which is used for reading and decoding DVDs by most Linux software) does not require the region to be set, even on the RPC2 drives described below. It manages to read from the DVD regardless.

[http://trillian.randomstuff.org.uk/~stephen/linux/DVD.shtml#regionset](http://trillian.randomstuff.org.uk/~stephen/linux/DVD.shtml#regionset)

BTW, RPC-1 is region free, RCP-2 is region locked. 

I dont have any DVD from a different region to test that however. 

There is directions for how to set the regoin here- 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

Be warned that lots of region locked DVD drives can only change the region 5 times. On the 5th change, that region is locked forever in some cases (sometimes you can get aroudn that by flashing new firmware, etc.)
[FONT=monospace][/FONT]

---

### Post by sdowney717 on 2011-01-24
> Parting words

Before you buy a DVD-ROM make sure that there's RPC-1 firmware for it if you intend to watch DVDs that come from outside your region. And make sure you flash the drive with the right firmware.

[http://www.doom9.org/](http://www.doom9.org/)

click the basics
then 
click how to make you dvd-rom region free.

---

### Post by sdowney717 on 2011-01-24
[http://en.wikipedia.org/wiki/Libdvdcss](http://en.wikipedia.org/wiki/Libdvdcss)

> libdvdcss is not to be confused with DeCSS. While DeCSS uses a cracked DVD player key to perform authentication, libdvdcss uses a generated list of possible player keys. If none of them works (for instance, when the DVD drive enforces region coding) a brute force algorithm is tried so the region code of a DVD is ignored. Unlike DeCSS, libdvdcss has never been legally challenged.
[edit] 

ignoring the region code?
how well does that work for libdvdcss?

---

### Post by sdowney717 on 2011-01-24
[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

> Just better. Unlike most similar projects, libdvdcss doesn't require the region of your drive to be set. 

so then what does this mean if the region of the drive is set?
versus the region of the drive is not set.

---

### Post by emailadress on 2011-01-25
thanks for all the answers!

@nightwishfan: the terminal did a lot and didn't spit out errors (that usually means I installed something ;-) ) but the problem didn't change unfortunately.

@cascade9: yes, that was my guess as well. I wouldn't mind at all changing my region to Europe, I live there... Hong Kong was just an exchange semester and now I'm stuck with those DVD's :-D 

I downloaded the small program, but when I type 'sudo regionset', I get this:

> jakob@jakob-laptop:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
jakob@jakob-laptop:~$ so maybe it is a hardware problem? There was a DVD in the drive but again, it started/stopped a couple of times, then fell silent. I tried it several times again. I don't have any non-french DVD's here to verify but I used to be able to play DVD's. I can verify this by the end of this week, I was just hoping to still watch some French movies before I leave. I will update this thread as soon as I verified that my DVD drive actually works... Maybe we should let it rest till then.

Cheers,
Jakob

---

### Post by mastablasta on 2011-01-25
last solution - get a new DVD drive, maybe USB?!

---

### Post by matthewbpt on 2011-01-25
This is very strange, I was under the impression that using libdvdcss meant that region codes no longer mattered, and in all my drives across the various computers I've had I have been able to play DVDs from Europe and North America without a problem. Have you tried using vlc to play them?

```
sudo apt-get install vlc
```

---

### Post by cascade9 on 2011-01-25
> **emailadress said:**
> @cascade9: yes, that was my guess as well. I wouldn't mind at all changing my region to Europe, I live there... Hong Kong was just an exchange semester and now I'm stuck with those DVD's :-D 

I downloaded the small program, but when I type 'sudo regionset', I get this:

so maybe it is a hardware problem? There was a DVD in the drive but again, it started/stopped a couple of times, then fell silent. I tried it several times again. I don't have any non-french DVD's here to verify but I used to be able to play DVD's. I can verify this by the end of this week, I was just hoping to still watch some French movies before I leave. I will update this thread as soon as I verified that my DVD drive actually works... Maybe we should let it rest till then.

Its possible that you've had a DVD drive failure of some type. Without a DVD to test with its pretty hard to know for sure.

---

### Post by williamts99 on 2011-01-25
This does sound like it might be a hardware problem.  I have played different region dvds with no issues.  libdvdcss doesn't even look at the regioncode, unless your hardware is somehow blocking it.  I would check for a firmware upgrade for your drive, see if there are any related fixes.  If you plan on booting back into Windows, I would look for a RPC firmware for your drive [http://tdb.rpc1.org/](http://tdb.rpc1.org/).  Try using a regular cd with the regionset command.

Lastly, try accessing a data dvd, it could be a hardware failure.

---

