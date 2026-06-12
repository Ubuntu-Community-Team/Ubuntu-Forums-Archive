---
title: "Skype on 8.10?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-14
Hi,
Wondering if anyone knows if there is .deb of the latest version of skype?
Had look but cannot find! argh!!! Maybe it's because I can't access the english site, coz I'm in China. Incidentally, how do I stop sites from directing me to only certain countries versions of the site?

TFC!
orb

---

### Post by s.fox on 2009-04-14
Hi,

The skype website only has download link for Ubuntu 7.04 - 8.04.   Here is the [link]("http://www.skype.com/go/getskype-linux-ubuntu")

Looks like 8.10 version is not out yet.

-Ash R

---

### Post by Jacdeb6009 on 2009-04-14
AFAIK, there are two other options available to you.  One is to add the Medibuntu repository to you list of repositories in the Synpatics package manager, the other is to use the Skype repository itself.

The Skype repository can be added as follows:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

The Medibuntu repository (for Intrepid):

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

The Medibuntu repository (for Hardy):

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Personally I would use the Medibuntu repos.  Be aware that under Intrepid there are some problems with Skype and sound, if you have a problem (generally with the microphone), check out [http://www.wiredrevolution.com](http://www.wiredrevolution.com) and search for fixing Skype on Ubuntu.  There are also plenty of useful threads in these forums.

Hope this helps and happy Skypeing... :)

---

### Post by hungryOrb on 2009-04-14
Thanks for reply guys, I wanted to install the latest because after installing 8.10 I found skype had a 'Problem with Audio Playback' when trying to make a call or test call. 
Anyone had this problem before in 8.10?

TFC!
<3
Robin

---

### Post by Jacdeb6009 on 2009-04-14
Yes, I had exactly the same problem (Dell Vostro 1400).

After quite a bit of Googling and reading I came across the following:

[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

(This was the link I meant to include in my previous post).  I know that there are folk who say the removing Pulse is silly, but it worked for me.  If all else fails it is worth a shot, it certainly solved my problem.

Note thought that I still run Hardy as my main Linux box for other reasons.

Hope you get it sorted!!

---

### Post by LowSky on 2009-04-14
> **hungryOrb said:**
> Thanks for reply guys, I wanted to install the latest because after installing 8.10 I found skype had a 'Problem with Audio Playback' when trying to make a call or test call. 
Anyone had this problem before in 8.10?

TFC!
<3
Robin
You need to change the audio settings form within skype. very easy thing to do

---

### Post by hungryOrb on 2009-04-14
JDB,
Thankyou! Worked 100%~!
<3
mmmmmmmmmmmmUAH!

---

### Post by xoorox on 2009-04-14
I managed to get it working without uninstalling PulseAudio ...in Skype audio settings I read somewhere that it was important to have the "Allow Skype to automatically adjust my mixer levels" unchecked.  Sound Out and Ringing needed to be set to Pulse but Sound In I had to play around and workout which hw:X was required.

---

### Post by Jacdeb6009 on 2009-04-14
> **hungryOrb said:**
> JDB,
Thankyou! Worked 100%~!
<3
mmmmmmmmmmmmUAH!

It's a pleasure, it's what the forums are all about.

Xoorox, your solution works on certain hardware, but on others not.  With my machine, installing ALSA again was the only option... trust me, I did not like the idea at all, but after two weeks of messing around and not having Skype, it was a last resort that worked.

---

