---
title: "Headphone jack not working ubuntu 7.10"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by didibanner on 2008-12-15
Hi I use Ubuntu 7.10 and everything works quite well except for the fact that when headphones are plugged into the jack, sound is piped into the headphone, but the speakers are not muted.

Ubuntu 8.04 and 8.10 don't play nice with my pc.

Any ideas?

btw
I use an HP Pavilion dv6809wm

CPU Type: AMD Turion 64 X2 TL-60 2.0G
Screen: 15.4" WXGA
Memory Size: 3GB DDR2
Hard Disk: 120GB
Optical Drive: DVD Super Multi
Graphics Card: NVIDIA GeForce 7150M
Video Memory: shared memory
Communication: Modem, LAN and WLAN
Card slot: 1 x Express Card
Dimensions: 14.05" x 10.12" x 1.00-1.56"
Weight: 6.06 lbs.

---

### Post by shredder12 on 2008-12-15
Yeah, I have faced this problem sometimes.. but things work out fine when i unplug the headphone and reinsert it into the jack.. 
I hope you have tried doing this..

---

### Post by jpoRS on 2008-12-15
I don't recall exactly what the process is in 7.10, but when you open up the volume window (double click on the speaker) you should be able to go into a preferences menu, check everything.  Go back to the volume window and look for anything that is just a check box, not a slider.  One of those (I believe) turns speakers on/off when headphones are plugged in.  That should do it!

Also, I don't see a reason why a newer version wouldn't work on your machine, how much RAM do you have?  I only say this because if you use 7.10, not only will you be constantly recommended to upgrade every time you post here, but there is the basic fact that things change between upgrades, so some people (like myself) won't remember 7.10 well enough to really help you.

If you are having problems upgrading due to RAM, try Xubuntu, or some other distribution designed for lighter machines.  That way you will be able to keep up to date and still not over tax your system.

Good luck!
jim

---

### Post by didibanner on 2008-12-15
> **jpoRS said:**
> I don't recall exactly what the process is in 7.10, but when you open up the volume window (double click on the speaker) you should be able to go into a preferences menu, check everything.  Go back to the volume window and look for anything that is just a check box, not a slider.  One of those (I believe) turns speakers on/off when headphones are plugged in.  That should do it!

Also, I don't see a reason why a newer version wouldn't work on your machine, how much RAM do you have?  I only say this because if you use 7.10, not only will you be constantly recommended to upgrade every time you post here, but there is the basic fact that things change between upgrades, so some people (like myself) won't remember 7.10 well enough to really help you.

If you are having problems upgrading due to RAM, try Xubuntu, or some other distribution designed for lighter machines.  That way you will be able to keep up to date and still not over tax your system.

Good luck!
jim

Hi Jim,
I looked through all the check boxes and checked and unchecked; tried before restarting and after all to the same effect.

The reason that I use 7.10 instead of 8.04 or 8.10 is that the nautilus file system keeps crashing and I cannot get the microphones working in both. 8.10 often freezes during boot up and only unfreezes when I push a button.

If you happen to know how to solve any of the problems in 8.04 or 8.10, I will be most grateful.

Thanks

---

### Post by didibanner on 2008-12-15
> **shredder12 said:**
> Yeah, I have faced this problem sometimes.. but things work out fine when i unplug the headphone and reinsert it into the jack.. 
I hope you have tried doing this..

Gaaa,
Didn't work for me. I really do wish it was that simple :(
What computer do you use?

---

### Post by jpoRS on 2008-12-15
By the sounds of it, you have a corrupted copy of 8.10  I would try downloading another copy and starting over, but that may or may not be what you are looking for, depending on what you need of the computer you are installing with.

jim

---

### Post by ibizatunes on 2008-12-15
+ 1 about the corrupt 8.10 cd, - burn a cd off at a low speed, then do a check disk on the cd, 
Boot to a live cd and see if your headphone work in 8.04 or 8.10 
also have you checked your hardware is not faulty in mem check (faulty hardware may coarse the crashes in nautilus,  also is the cable definitely ok?

---

### Post by waspbr on 2008-12-15
I did some digging around and your laptop should be supported by the latest releases, 8.04/10. There are two things that may be causing you problems that I can think of: 

1. Bad installation CD, burining your CD at the lowest possible speed usually helps preventing errors

2. graphic drivers issues, these are annoying, though I found that programs like envyng (the package is actually named envyng-gtk*), do a wonderful job at managing drivers. 

Haviong installed ubuntu on a number of HP laptops, I would also think that everything should work out fine.
Here's a link to some to a thread about your lappy([http://ubuntuforums.org/showthread.php?t=942201]("http://ubuntuforums.org/showthread.php?t=942201")).

* for kubuntu users the package envyng-qt should be used

---

### Post by didibanner on 2008-12-15
> **ibizatunes said:**
> + 1 about the corrupt 8.10 cd, - burn a cd off at a low speed, then do a check disk on the cd, 
Boot to a live cd and see if your headphone work in 8.04 or 8.10 
also have you checked your hardware is not faulty in mem check (faulty hardware may coarse the crashes in nautilus,  also is the cable definitely ok?

The headphone jack works in 8.04 and 8.10 but the built-in microphone does not work in either. I think I read somewhere that it might have something to do with pulse-audio. :confused:

---

### Post by didibanner on 2008-12-15
> **jpoRS said:**
> By the sounds of it, you have a corrupted copy of 8.10  I would try downloading another copy and starting over, but that may or may not be what you are looking for, depending on what you need of the computer you are installing with.

jim

Hi Jim,
I just tried this with 8.04 and I think it sorted out the whole crashing thing. Thanks.
But 8.04 still does not recognize my built-in microphone.

---

### Post by didibanner on 2008-12-15
> **waspbr said:**
> I did some digging around and your laptop should be supported by the latest releases, 8.04/10. There are two things that may be causing you problems that I can think of: 

1. Bad installation CD, burining your CD at the lowest possible speed usually helps preventing errors

2. graphic drivers issues, these are annoying, though I found that programs like envyng (the package is actually named envyng-gtk*), do a wonderful job at managing drivers. 

Haviong installed ubuntu on a number of HP laptops, I would also think that everything should work out fine.
Here's a link to some to a thread about your lappy([http://ubuntuforums.org/showthread.php?t=942201]("http://ubuntuforums.org/showthread.php?t=942201")).

* for kubuntu users the package envyng-qt should be used

Hi waspbr,
The HP dv6809wm uses an nVidia geForce 7150M. I usually just use the proprietary driver that you are prompted to install. Do you know if envyng-gtk covers this?

Hey thanks for the digging btw :)

---

### Post by waspbr on 2008-12-16
it should, but if the crashes have stopped, then I would forget about envy, envy is generally a good option when the default graphics drivers have any glitches with the install. Whenever I go about messing with the graphics drivers envy is always there for the rescue. 

no worries about the digging, it's my pleasure to help out

---

### Post by Growbag on 2008-12-16
For the headphone problem do this:

open a terminal and type:


[I]sudo gedit /etc/modprobe.d/alsa-base
[/I]

add this line at the bottom of the file:

   **options snd-hda-intel model=laptop**

save and exit gedit.

then in the same terminal type:

*sudo /etc/init.d/alsa-utils restart*

That will restart the sound system without having to restart the entire computer.  Note that your mixer panel applet might vanish, just restart the mixer applet.

Now try your headphones again, your speakers should now mute when your headphones are plugged in.

---

### Post by didibanner on 2008-12-17
> **Growbag said:**
> For the headphone problem do this:

open a terminal and type:


[I]sudo gedit /etc/modprobe.d/alsa-base
[/I]

add this line at the bottom of the file:

   **options snd-hda-intel model=laptop**

save and exit gedit.

then in the same terminal type:

*sudo /etc/init.d/alsa-utils restart*

That will restart the sound system without having to restart the entire computer.  Note that your mixer panel applet might vanish, just restart the mixer applet.

Now try your headphones again, your speakers should now mute when your headphones are plugged in.


Thanks Growbag, but it didn't work.

---

### Post by Growbag on 2008-12-17
Hmm, ok....

First just undo the editing I told you to do (remove the line), then open a terminal and type:

*lspci | grep udio*

That will tell what type of audio device you have.

Then maybe try searching the web for info on that particular sound card.  The best place would probably be 

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Or search the ubuntu forums.

Sorry, I have no further suggestions, other than trying a different distro, maybe one with a more up-to-date kernel and hopefully newer alsa version :).

One last thought.... you are definitely plugging the headphones into the correct socket?  I'm sure you are, but just to make sure :).

---

### Post by didibanner on 2008-12-17
> **Growbag said:**
> Hmm, ok....

First just undo the editing I told you to do (remove the line), then open a terminal and type:

*lspci | grep udio*

That will tell what type of audio device you have.

Then maybe try searching the web for info on that particular sound card.  The best place would probably be 

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Or search the ubuntu forums.

Sorry, I have no further suggestions, other than trying a different distro, maybe one with a more up-to-date kernel and hopefully newer alsa version :).

One last thought.... you are definitely plugging the headphones into the correct socket?  I'm sure you are, but just to make sure :).

Hi 
The lspci command gave

**00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)**

To the socket thing, there are two headphone jacks and I always try both.
Thanks for all your help.

---

### Post by Coolride on 2008-12-17
It doesn't work on my Toshiba laptop either, I worked on trying to get it going for a week and gave up. I just boot to Vista too listen with my headphones.

---

### Post by juanoleso on 2008-12-17
I don't own a laptop personally, but just some quick trolling brought up these threads...

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=804986[/COLOR] Has a bunch of suggestions.]("http://ubuntuforums.org/showthread.php?t=804986")

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=740702[/COLOR]]("http://ubuntuforums.org/showthread.php?t=740702")

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=806620[/COLOR]]("http://ubuntuforums.org/showthread.php?t=806620")

I didn't quite get whether you up'd to 8.04 Hardy, but if you did I used this thread to fix my pulseaudio:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=789578[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fix")

---

### Post by didibanner on 2008-12-24
> **juanoleso said:**
> I don't own a laptop personally, but just some quick trolling brought up these threads...

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=804986[/COLOR] Has a bunch of suggestions.]("http://ubuntuforums.org/showthread.php?t=804986")

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=740702[/COLOR]]("http://ubuntuforums.org/showthread.php?t=740702")

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=806620[/COLOR]]("http://ubuntuforums.org/showthread.php?t=806620")

I didn't quite get whether you up'd to 8.04 Hardy, but if you did I used this thread to fix my pulseaudio:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=789578[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fix")

Drat,
I think I am just going to get used to the fact that this computer just doesn't want to play nice with Ubuntu. 
The microphone still doesn't work in 8.04 and the headphone still doesn't work in 7.10. I think I'll just stay with 7.10. Everything else works here.

Thank you all so much for your input :)

---

