---
title: "LOST MY SOUND ubuntu 9.10"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Virtueofselfishness on 2009-12-30
i recently lost my sound on my comp i didnt make any changes recently it was working fine then all of a sudden no sound.

i read thru some threads and i saw that someone asked anohter memeber with the same problem to type thissudo lshw -C multimedia in terminal so they can show there output this is mine

 *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:9000(size=256) ioport:8800(size=64) memory:e3000000-e30001ff memory:e2800000-e28000ff

---

### Post by Virtueofselfishness on 2009-12-30
bump!

---

### Post by Chris Edgell on 2009-12-30
Here's the MY SOUND story, I don't know how it translates to 9.10, but you can scan through and see what applies.  (So many problems are caused by "Muted".)[SIZE="6"][/SIZE]

THE FIRST STEPS

For me this was really all beside the point - this was about making sure I had all the necessary programs installed.  Acrobat, Java, and probably etc, etc. If you need to see about those there are easier descriptions than MY thread about it:
[http://ubuntuforums.org/showthread.php?t=1285131](http://ubuntuforums.org/showthread.php?t=1285131)  

[SIZE="3"]The real purpose of this post is to show you how to check the 3 following places to see if it is just something that is muted, turned off, not activated..
[/SIZE]


THE FIRST PLACE TO CHECK
Applications > Multimedia > Mixer

I had struggled for some time to discover where that AlsaMixer had popped out from -- (and it apparently had popped out from a multimedia click).  I had slid the volume slide to quitehigh...still no sound.   Then it seemed so long until someone pointed out those little red X's at the bottom of each slide (in the AlsaMixer) -- indicated muted -- click red x to unmute.)  You will also notice in the bottom left-hand corner, click that button marked "Select Controls" and inside you will see about 20 places that can be activated for sound (or at least says, "Select which controls should be visible".  Be sure to click master.  See the first screenshot.
				....................................

THE SECOND PLACE TO CHECK
Applications > Accessories > Terminal  (type in alsamixer)

This is the second screenshot.  I'm showing the Mixer too.  You can see that the mixer [SIZE="3"]causes[/SIZE] what you are seeing in the terminal.  If the terminal is showing red, the mixer volume slide can be adjusted then and there -- and you'll see it reflected in the terminal.  Also notice that when you mute in the Mixer, you will see a fated "mm" at the bottom of the slide in the terminal that stands for mute: the OO is unmuted.  Again you see how the changes made in the mixer are reflected in the terminal.  The terminal is the static reflection of what IS in this case.  Don't just sit and read this, do this that I have just described.  Experience how the mixer window CAUSES the changes to the Altamixer in the terminal.  Remember how to type it into the terminal:  alsamixer       

				..................................

THIS IS THE THIRD PLACE

So today after the subject had come up again, I said, "I'm going to click around and see what those other [SIZE="2"]applications[/SIZE] look like, I have not really explored here."   I saw "aumix", I have NEVER even heard of it, never saw it either...let's click and see."  This is the third screenshot.

Applications > Multimedia > aumix

"What the heck is it?" I asked. It looked like sound and volume, there was a word unmute, I clicked it... various little "O" position markers all reset to ZEROs at the starting point.

I was quite sure I could click on the word "Mute" (that the unmute had changed to), and that it would change back to how it had been. But NO...The word changed back to unmute but all the zeros stayed at first position (instead of all the various positions on an very pale horizontal scale). I went to the AlsaMixer and the mute was not marked with the red X.....but there was now NO SOUND.  I could press mute on the aumix and all the zeroes  popped to the starting point, and the little red X showed up at the base of all the slides in the mixer.

Can you believe, I went to examine aumix again and on the odd chance, I clicked far along that  horizontal, turquoise line...and the Zeros positioned where I clicked...and now I have sound again, although in the between time I happened to have made sure that the mixer had no red x, because now as I'm defining for YOU, I discover that if I had not happened to have removed those red mutes, even when I moved those zeroes up the scale, I still would NOT have gotten sound, because of having reimposed the mutes into the mixer.

Also this aumix is a TERMINAL that has been arrived at NOT by clicking "Terminal", I don't really know how it got to the multimedia position-it had to have come there when I installed something...but now I see it can be gotten by means of the regular terminal click.  So we could skip the convoluted way I got to "aumix".   But tell me about it, is it a third way that people could have lost their sound?  I have never seen it mentioned as a possible "cure" for sound problems.  I have never seen it mentioned at all...maybe because I wasn't looking to notice a word I had never heard.


...................................

---

### Post by m0nstersnatch on 2009-12-31
> **Virtueofselfishness said:**
> i recently lost my sound on my comp i didnt make any changes recently it was working fine then all of a sudden no sound.
This happed 3h ago on my Jaunty installation. The issue here beeing that on a working system with sound you make no changes to any configs or settings, reboot and then listen to all that silence..
It freaked me out a lil bit..

Here are some info regarding my sound config:

[output from alsa-info.sh]("http://www.alsa-project.org/db/?f=54f1e63412030f07118f12ed6f364a3f94bc5047")

```
$sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```
Any help would be most welcome..

---

### Post by Virtueofselfishness on 2009-12-31
chris thanks for the reply but i couldnt get my sound to work

is there a step by step thing i can do thats pretty easy to do im new to ubuntu and im barely learning the ropes 

i feel like im deaf in RL i miss my sound :(

---

### Post by Virtueofselfishness on 2009-12-31
btw i dont even have the sound speaker on the top panel anymore 
i clicked on
system>preference>sound
and i get a message saying "waiting for sound to respond" but it doesant seem like its going anywhere.

i been following many steps but im guessing im doing them wrong and it has ruined my sound even worse :confused:

---

### Post by Virtueofselfishness on 2009-12-31
Bump

---

### Post by Chris Edgell on 2009-12-31
It happened to me too that I even lost the speaker in the top panel.

I am a newbee too...also I have Jaunty 9.4 and you with Karmic 9.10...so I don't know what yours looks like.  Do you know how to make a screenshot?  

(Also, you may know a lot more than I do and just be new to Linux/Ubuntu, whereas I am coming from knowing next to nothing about computer at all.  My learning is trying to conceptualize everything too.)  Which is to say, if we go through stuff step by step, forgive me, if I, as a beginner, treat you like a beginner too.

So, if you have a camera in your panel, be ready to take screenshots. If you don't you must download one. 

Also tell me if you know where your AlsaMixer is, do you know where it is in your terminal, do you know about aumix? 

You may speak of the virtue of selfishness, but I adore the power of love!

Happy new year to you!
Christine

---

### Post by m0nstersnatch on 2010-01-01
> **m0nstersnatch said:**
> 

Here are some info regarding my sound config:

[output from alsa-info.sh]("http://www.alsa-project.org/db/?f=54f1e63412030f07118f12ed6f364a3f94bc5047")

```
$sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```Any help would be most welcome..

I compared the output from alsa-info.sh (above on 9.04) with the [output on 9.10]("http://www.alsa-project.org/db/?f=a5f966ba7ca83c6998578f11c1ad0d40dad85858") and there is "snd-hda-intel: power_save=10 power_save_controller=N" additional. Could it be that I have lost somehow a module on my Jaunty installation? 
Very odd..

---

### Post by Chris Edgell on 2010-01-01
I have added the screenshots to post #3, I have edited some of the language, trying to make it more clear.

---

### Post by Virtueofselfishness on 2010-01-01
i give up im just gonna reinstall ubuntu 

good idea or should i keep trying to fix it.

i dont have much on my comp since i barely made the switch to ubuntu 

i have an external HD so i wont have problem backing up my music an pictures

---

### Post by eeeandrew on 2010-01-01
I'm using an intel 82801G. Slightly different model from yours but if you check my wiki page at [http://wiki.ubuntu.com/eeeandrew](http://wiki.ubuntu.com/eeeandrew) You'll see how I fixed it. You can try that fix and see if it works. If that fails you can check this thread [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) to find out which numbers should be in there.

Hope this helps.

---

### Post by Chris Edgell on 2010-01-01
To virtueofselfishness,

I guess I must reassess how much time to give when there is no real feedback or signs of tracking with what I'm trying to communicate.

I'll learn as I go along too, just like you.

Good luck to ya' and a happy new year
Christine
(I know, I shouldn't take too much stuff personally, but life is so personal to me, you know??!!)

---

