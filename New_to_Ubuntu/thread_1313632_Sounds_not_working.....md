---
title: "Sounds not working...."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Harshana on 2009-11-03
I install Ubuntu remix to my HP mini 110-110 tu netbook.I downloaded UNR according to my netbook.But sound not working.No even startup.What would be the problem?

---

### Post by LarsW_Tierp on 2009-11-04
These users may have the answer for you:

 				 				**Re: UNR on HP Mini 1030nr** 			
 			 			 		   		 		 		Re: the volume issue, the fix I mentioned in my original post fixes that.

Go to System -> Preferences -> Sound and in the bottom pane select PCM (not in front of my Ubuntu machine so can't remember what the bottom pane is called). That selects what control the "Volume" slider and thus keyboard control runs.

---

### Post by Harshana on 2009-11-04
> **LarsW_Tierp said:**
> These users may have the answer for you:

 				 				**Re: UNR on HP Mini 1030nr** 			
 			 			 		   		 		 		Re: the volume issue, the fix I mentioned in my original post fixes that.

Go to System -> Preferences -> Sound and in the bottom pane select PCM (not in front of my Ubuntu machine so can't remember what the bottom pane is called). That selects what control the "Volume" slider and thus keyboard control runs.


Thanx.I found it...
:p

---

### Post by nicofaller on 2009-11-04
It still does not work for me... :( 

I did what was told, but still I cant hear any sound even though the volume slider is maxx.

---

### Post by LarsW_Tierp on 2009-11-04
OK, I try to find an answer for you during the day. Cannot promise anything, but i'll try.

---

### Post by LarsW_Tierp on 2009-11-04
[Here]("http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html") is someone that have had the same problem, apparently this is a know bug for HP mini.
Have you tried to boot with a live Karmic release? Every time I have had a problem with mini computers Karmic has in some auto-magically way sorted it out for me.

Good Luck!

---

### Post by Harshana on 2009-11-04
I found it.But it didn't work.Now what?
I like that ubuntu than Windows.But without sound what use.
Isn't there any other ways?

---

### Post by LarsW_Tierp on 2009-11-05
[B][FONT=Arial][SIZE=2]A thread from [ubuntu wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")[/SIZE][/FONT]
[/B]

[B]
[/B]

**HP Mini 110 / Compaq Mini 100c**

 
[LIST]
[*]Ubuntu Netbook Remix 9.10 Karmic: 
[/LIST]
The Karmic version "just work" with almost everything supported without tweaking. Wired nic works nicely. Sound works nicely. The "windows" key however does not work anymore, and the built-in SD card reader has no available driver. 
One user reports a case of the wireless drivers not working initially. Possible Fix [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1669880.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1669880.html)

When I tried it it just worked on every netbook I tried it on.
Test 9.10 Karmic.

BR

Lars

---

### Post by LarsW_Tierp on 2009-11-05
Please run this command:

lspci | grep Audio

And post the result, copy/paste is easiest.

BR

Lars

---

### Post by Harshana on 2009-11-05
> **LarsW_Tierp said:**
> Please run this command:

lspci | grep Audio

And post the result, copy/paste is easiest.

BR

Lars

This is the result i got.........

[COLOR="Blue"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/COLOR]
[COLOR="Black"]Thanx......[/COLOR]

In addition--
 I heard a little noise (like chiri chiri chiri.....) through head phone when play video or audio.(When only play them).....
When i pause player it stops.....

---

### Post by LarsW_Tierp on 2009-11-06
It seems that your sound driver is set to PulseAudio.
There is a excellent [How to here.]("http://ubuntuforums.org/showthread.php?t=789578") 

Hope you get it fixed, I believe that I cannot give more immediate help due to my personal schedule. If the how to doesn't help, please post a new help post in the Absolute beginners area again.

Best of luck!

---

### Post by nadian on 2009-11-06
I had a similar problem, this page helped me fix it :
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
if that doesn't work you could have a look at
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
if you haven;t already.

---

### Post by Harshana on 2009-11-06
> **LarsW_Tierp said:**
> It seems that your sound driver is set to PulseAudio.
There is a excellent [How to here.]("http://ubuntuforums.org/showthread.php?t=789578") 

Hope you get it fixed, I believe that I cannot give more immediate help due to my personal schedule. If the how to doesn't help, please post a new help post in the Absolute beginners area again.

Best of luck!

Thanx.A got it and now i have the sounds.Even only through Head phone, Its ok for now,
Thanx again .............:popcorn:

---

### Post by Harshana on 2009-11-06
> **nadian said:**
> I had a similar problem, this page helped me fix it :
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
if that doesn't work you could have a look at
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
if you haven;t already.

thanx.I think i"ll be able to solve " sound only through headphones" problem.
Those links were Very helpfull.

Thanx...........:p

---

