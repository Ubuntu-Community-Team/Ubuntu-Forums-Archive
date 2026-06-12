---
title: "Error with ITune in Wine &quot;QuickTime Unavailable&quot;"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by sokam on 2009-12-08
When openning iTune 7.2 in Wine 1.0.1, an error message say "QuickTime Unavailable, QuickTime is required to run iTunes. Please reinstall iTunes."

However, when I check c:\Program File\, I found that both Quicktime and Itunes are installed in there.  So why is it telling me quicktime is not install!

This is what it keeps appearing when I run the command in terminal to open itunes.

[INDENT]err:module:import_dll Library QTCF.dll (which is needed by L"C:\\Program Files\\QuickTime\\QTSystem\\QuickTime.qts") not found
[/INDENT]

--------------------------------------
Unbuntu 9.10 dual-boot with Window Vista
AMD Athlon 64x2
4GB DDR2

---

### Post by LuisGMarine on 2009-12-08
I hear iTunes just doesn't work quite well with Wine.  I recommend using an alternate application such as Banshee or Songbird.  If you want to manage your iPod both banshee and Songbird can do it.  You can follow the links on my signature to get you started.  Good luck :popcorn:

---

### Post by sokam on 2009-12-08
Stanford on iTune U only let you run with iTune.  That's the only reason I am using iTune at all.  [http://itunes.stanford.edu/faq.html](http://itunes.stanford.edu/faq.html)

---

### Post by chillyomi on 2009-12-08
yeah I was about to ask you  why are you using itunes I find itunesquite suckish to say the least

---

### Post by ramjet_1953 on 2009-12-08
If you like the look and feel of iTunes, why not use [COLOR="Red"]Rhythmbox[/COLOR] Music Player?

Worth a try.

Install it using Synaptic. Just search for [COLOR="Blue"]rhythmbox[/COLOR]

Or type this in a terminal:

```
sudo apt-get install rhythmbox
```

Regards,
Roger :D

---

### Post by sokam on 2009-12-08
Like I said, Stanford on iTune U only let you run with iTune. That's the only reason I am using iTune at all. [http://itunes.stanford.edu/faq.html](http://itunes.stanford.edu/faq.html)

------

I just restart my computer in Window and installed iTune and able to use the iTune U for Stanford.  Something just not meant for Ubuntu.

---

### Post by Cuco3 on 2009-12-08
> **sokam said:**
> Like I said, Stanford on iTune U only let you run with iTune. That's the only reason I am using iTune at all. [http://itunes.stanford.edu/faq.html](http://itunes.stanford.edu/faq.html)

------

I just restart my computer in Window and installed iTune and able to use the iTune U for Stanford.  Something just not meant for Ubuntu.You can always virtualize Windows within Linux and install iTunes. That's what I did cuz I love Linux/Ubuntu too much to leave it. :p

---

### Post by qyot27 on 2009-12-08
Do podcasts even download on such an outdated version of iTunes?  For all the regular music purchases and so on Apple requires the use of iTunes 9.

Besides, from the page linked:
[I]For those who use another operating system such as Linux or wish to avoid iTunes altogether, we plan to offer podcast (RSS) access in the near future.

You do not need a Macintosh, iTunes, or an iPod to play the audio files. All you will need is a player capable of playing .mp4 AAC (Advanced Audio Codec) files. (AAC is not exclusively Apple's, although Apple prefers it to alternative file formats.)[/I]

---

### Post by sokam on 2009-12-09
> **qyot27 said:**
> Do podcasts even download on such an outdated version of iTunes?  For all the regular music purchases and so on Apple requires the use of iTunes 9.

Besides, from the page linked:
[I]For those who use another operating system such as Linux or wish to avoid iTunes altogether, we plan to offer podcast (RSS) access in the near future.

You do not need a Macintosh, iTunes, or an iPod to play the audio files. All you will need is a player capable of playing .mp4 AAC (Advanced Audio Codec) files. (AAC is not exclusively Apple's, although Apple prefers it to alternative file formats.)[/I]


Yes, I read that too.  But the key sentence is "we plan to offer podcast (RSS) access in the near future" which mean they don't have it yet and can't tell you a date that they will have it.

Regarding the old version of itunes, I actually tried a newer version 9.0.2 and it tells me the installation is completed but it never even bother to create the itunes folder in c:\program file in wine.  So that's why I went with 7.2 and it actually installed but won't run.

---

### Post by NoBugs! on 2010-01-10
[Here]("http://www2.unil.ch/itunesu/index.groovy?handle=http://deimos3.apple.com/WebObjects/Core.woa/Browse/itunes.stanford.edu") is the non-itunes page for stanford's itunesu

---

### Post by TWFJR on 2010-01-20
I could care less about downloading music from iTunes but I need to download business apps to use with my iPhone. I have 7.2 iTunes using WINE but I cannot connect, register, etc. What is necessary is that I can load apts to my iPhone. I've had no success.  Any suggestions or am I up the creek on this one?

---

