---
title: "Firefox/Flash problems. (i think)"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by negative: on 2009-03-19
OK ok, I have searched this forum and found various threads relating to the problems i am having, but none of the solutions seem to work for me, either i'm too stupid to understand them, or they aren't the right solution.

Right, Here goes, I am running Ubuntu 8.04, and Firefox 3.0.7, and everytime i try to watch something on youtube it doesn't work. 

it just hangs there with a black screen and sometimes the sound plays, it is so ******* annoying. i just want it to work, it's the only problem i've got and it can't seem to be fixed. 


HELP ME PLEASEEEEEEEE, lol.

---

### Post by sailthesea on 2009-03-19
This worked for me although on intrepid but it should bust you out too

Open a Terminal and put these in:

1 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
2 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
3 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

 This will find the drivers and install them and should also stop any clashes You can do this same thing in Synaptic and Add /Remove but this is simpler 
 Good luck!

---

### Post by DaveG825 on 2009-03-19
I'm really glad that someone asked this question, because I've been having simpler problems. It seems, sailthesea, as though your simple solution may have worked. I'll let you know for sure tomorrow. :smile:

---

### Post by leonardo_neo on 2009-03-20
I successfully added the keys. Now lets see if it works.

Thanks  :)

---

### Post by ivanvajar on 2009-03-20
If you run 32bit Ubuntu:

> sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

This will install complete multimedia support.

---

### Post by negative: on 2009-03-23
Anybody had any success with any of these solutions. :O

---

### Post by negative: on 2009-03-23
sailthesea;

Thanks so much, your little guide worked a treat, 

I'm not sure what i did. (well, i installed some things and removed some things) but it works perfect now. your description was a little hard to follow, but pretty clear in the end, unlike ivanvajar's post, which was pretty impossible to understand. 

Someone should make this a sticky as i believe this would be a rather common and frustrating problem to beginner users such as myself.

Thanks Again :)

---

### Post by sailthesea on 2009-03-24
No problem:D
It's a simple fix that probably is on a sticky somewhere Its just knowing where yo dig!
Welcome to Ubuntu

---

### Post by BrandonBan6 on 2009-03-25
> **ivanvajar said:**
> If you run 32bit Ubuntu:



This will install complete multimedia support.

Why are you removing all of these? Just asking for clarification :)

---

### Post by sailthesea on 2009-03-25
Only the first 2 lines are removed to clear for the codecs in the rest of the lines

---

### Post by Jackie999 on 2009-03-25
I've noticed in intrepid there is no sound in youtube videos now..not sure when the sound disappeared ...I used to have sound.
I tried the suggestion in this thread and still nothing - did it work for anyone else?

---

### Post by Ammet on 2009-03-25
> **Jackie999 said:**
> I've noticed in intrepid there is no sound in youtube videos now..not sure when the sound disappeared ...I used to have sound.
I tried the suggestion in this thread and still nothing - did it work for anyone else?

Same problem here... no sound for flash/streaming videos. Been searching the forums here for a couple of days and tried nearly every fix I've come across with no success. I too am using Intrepid. :(

---

### Post by oldsoundguy on 2009-03-26
This is what I finally had to do:
I went into Synaptic and un installed EVERYTHING Flash that was green. (searched flash)
Opened the browser and went to a known youtube file that had not launched before.
I got the message that I needed to install Flash.
Clicked on the link and it took me to the Adobe site.
Chose the Flash for 8.40 and installed it.
Flash worked .. but soon got the update notice and guess what?  It was for FLASH!!
Updated
Still works.

---

### Post by Ammet on 2009-03-26
> **oldsoundguy said:**
> This is what I finally had to do:
I went into Synaptic and un installed EVERYTHING Flash that was green. (searched flash)
Opened the browser and went to a known youtube file that had not launched before.
I got the message that I needed to install Flash.
Clicked on the link and it took me to the Adobe site.
Chose the Flash for 8.40 and installed it.
Flash worked .. but soon got the update notice and guess what?  It was for FLASH!!
Updated
Still works.

For what it's worth, just tried this as you described and still no sound. :( Video is great, just no sound.

---

### Post by oldsoundguy on 2009-03-26
> **Ammet said:**
> For what it's worth, just tried this as you described and still no sound. :( Video is great, just no sound.

Have you installed the audio packages? (Pulse Audio with Alsa?)

There is a HUGE thread on that already .. I did it and it WORKS!!

---

### Post by Ammet on 2009-03-26
> **oldsoundguy said:**
> Have you installed the audio packages? (Pulse Audio with Alsa?)

There is a HUGE thread on that already .. I did it and it WORKS!!

I believe so (still new to all this). It's listed in my Synaptic Package Manager as being installed. I also followed the guide found here - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) - and used Part C. The code he mentioned to add in the second part of step 1 wasn't there. So I added and followed the rest of the steps. Wasn't prompted for anything as he notes may happen at the end of step 2. Logged out and back in after it all and still no sound in Flash (and only in Flash... everything else, Rythmbox, games, etc, had sound just fine). 

Is there another guide or info somewhere I've missed? Most seemed to point back to that post. Either way, I appreciate the help.

---

### Post by Ammet on 2009-03-27
My issue of no sound only when streaming flash video in Firefox is FIXED!!! Just wanted to update my post for anyone else in the future here... So as not to repeat myself, I had asked about it in another thread. My fix is here - [http://ubuntuforums.org/showpost.php?p=6969139&postcount=11](http://ubuntuforums.org/showpost.php?p=6969139&postcount=11)

---

### Post by questworld on 2009-03-27
Thanks sailthesea.

Your instruction worked like a treat for me. For others info I intalled this on 8.10 for firefox 3.0.7

---

### Post by Mr. Stabby on 2009-03-28
X

---

### Post by netdevil on 2009-08-06
Thanx sailthesea, your solution worked perfectly for me. I am using Opera 9.64 with Ubuntu 9.04.

---

