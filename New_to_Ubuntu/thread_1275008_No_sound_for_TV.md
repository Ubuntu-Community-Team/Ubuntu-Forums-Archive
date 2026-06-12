---
title: "No sound for TV"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by dgub on 2009-09-25
I have been trying to find a TV app from my PCI TV card from Hauppauge. I think it was called Win-TV.

I had a look at Myth TV but cannot get it to install properly and in any case is overkill for my purpose.

I have now found TV Time which install correctly and get a picture but no sound. In the volume control I have enabled Line-in.

I was wondering if Myth TV might be interfering with it. Tried to remove it but it is not listed in the Add/remove list. 

Can someone help me with this please

Should add that this is 8.04

Thanks.

---

### Post by dgub on 2009-09-25
> **dgub said:**
> I have been trying to find a TV app from my PCI TV card from Hauppauge. I think it was called Win-TV.

I had a look at Myth TV but cannot get it to install properly and in any case is overkill for my purpose.

I have now found TV Time which install correctly and get a picture but no sound. In the volume control I have enabled Line-in.

I was wondering if Myth TV might be interfering with it. Tried to remove it but it is not listed in the Add/remove list. 

Can someone help me with this please

Should add that this is 8.04

Thanks.

In case anyone asks. The atartup sounds etc do work, Also I can play videos from You Tube without any problem.

Also the output from the card is connected dirctly to Line in on the sound card

---

### Post by dgub on 2009-09-28
> **dgub said:**
> In case anyone asks. The atartup sounds etc do work, Also I can play videos from You Tube without any problem.

Also the output from the card is connected directly to Line in on the sound card

I have been searching everywhere for a solution to this but cannot find anything that will work for me.

I would appreciate some help on this please.

---

### Post by OffAxis on 2009-09-28
Does your card work with any other multimedia program?

You can record straight from the device to a file with 
```

cat /dev/video0 > TestFile.mpg
```

(assuming your Hauppauge card is listed as video0)

or view it in mplayer with

```
mplayer /dev/video0
```

do those work?

---

### Post by dgub on 2009-09-28
> **OffAxis said:**
> Does your card work with any other multimedia program?

You can record straight from the device to a file with 
```

cat /dev/video0 > TestFile.mpg
```

(assuming your Hauppauge card is listed as video0)

or view it in mplayer with

```
mplayer /dev/video0
```

do those work?

Thanks

First one does not work.

The second one did not work and suggested installing mplayer which I did. Then using the second one again mplayer load with a multi coloured rectangle flashing around the screen. In terminal was the part of the continuous output.

> AC EOB marker is absent pos=65
AC EOB marker is absent pos=65
AC EOB marker is absent pos=73
AC EOB marker is absent pos=65
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=65
AC EOB marker is absent pos=80
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=70
AC EOB marker is absent pos=78
AC EOB marker is absent pos=65
AC EOB marker is absent pos=64
AC EOB marker is absent pos=65


I do not understand the relevance of that message.

---

### Post by dgub on 2009-09-28
I have now installed kdetv. Under settings the 
Channel-File-Location Configuration is shown as 

> Video4Linux2:BT878 vudeo (Hauppauge (bt878)) /home/dg/share/apps/kdetv/channels.xml


Don't know if that has any relevance.

---

### Post by OffAxis on 2009-09-28
do you use a cable box in your setup?

Or are you looking to tune the channel with the card?

Are you sure your card is listed as **/dev/video0** ?

(what card is it, by the way?)

Something should be coming in on that capture card. Since nothing was coming in this time (and you mention in your first post that you did have a picture), did you have the input setup exactly the same?
you can try hooking up a dvd player into it and playing a dvd(or some other video/audio source that you know is working) ; then you'll know you have sound and video.
Whether it's a coaxial card, rca jacks, etc some sort of a signal should be coming in that jack, and mplayer can play just about anything.

---

### Post by howefield on 2009-09-28
> **dgub said:**
> I have now installed kdetv.

Try Kaffeine, the best tv tuner player I have found so far, and where many other programs do not pick up the tuner or have other issues, Kaffeine seems to do the business.

Works with every Hauppauge USB or PCI card I've ever had.

---

### Post by dgub on 2009-09-29
> **OffAxis said:**
> do you use a cable box in your setup?

Or are you looking to tune the channel with the card?

Are you sure your card is listed as **/dev/video0** ?

(what card is it, by the way?)

Something should be coming in on that capture card. Since nothing was coming in this time (and you mention in your first post that you did have a picture), did you have the input setup exactly the same?
you can try hooking up a dvd player into it and playing a dvd(or some other video/audio source that you know is working) ; then you'll know you have sound and video.
Whether it's a coaxial card, rca jacks, etc some sort of a signal should be coming in that jack, and mplayer can play just about anything.

Thanks

TVTime or KDETV work with the card and find all the channels with good output but no sound. This is an analogue card

There is an entry under /dev/video0 but it has zero bytes in it

The card is Hauppauge Win pci TV/FM

I put a dvd into the drive and that plays with sound. 

The sound output on the TV card is linked directly to the line of the sound card. The line input is enabled.

Hope I have given you enough info.

---

### Post by dgub on 2009-09-29
> **howefield said:**
> Try Kaffeine, the best tv tuner player I have found so far, and where many other programs do not pick up the tuner or have other issues, Kaffeine seems to do the business.

Works with every Hauppauge USB or PCI card I've ever had.

Thanks

Tried Kaffeine but it does not even see the TV card and I cannot see there is any option to select it. The version is 0.8.6.

Would welcome any hints please.

---

### Post by dgub on 2009-09-30
With further digging around I discovered that Kaffeine does not work with an analogue card. Not a worry for me since I can connect a Sky DigiBox via the ariel and use the satellite.

On the sound problem, which is pretty universal. On a Suse site someone had success by using KMix. I have installed that and trying all the options I can get sound in both TVTime & KDETV.

The volume control works in TVTime but not in KDETV which has to be controlled via the mixer.

Hope this might help someone.

---

### Post by alekkova on 2010-01-09
You need to use this shell script

#!/bin/bash
sox -r 32000 -2 -t alsa hw:1,0 -t alsa hw:0,0 &        # - Start sox process
/usr/bin/kdetv                                          # - Start KDETV
                                                        # - If stop KDETV
p=$( ps -ef | grep "[s]ox.*3200" | awk '{ print $2 }' ) # - Search sox process
kill -9 ${p} || ferror "Command kill -9 ${p}";         # -- Kill sox process
[ ${?} -eq 0 ] || ferror "echo Error COMMAND : stop sox" # - Exit display on error


Hope that helps.

---

