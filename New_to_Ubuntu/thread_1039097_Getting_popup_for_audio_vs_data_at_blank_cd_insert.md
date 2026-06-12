---
title: "Getting popup for audio vs data at blank cd insert"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by DVD-R on 2009-01-14
Hi Gang,
I've searched for this one, but without luck.
I've got a new install of 8.10
The machine is physically located in a closet as its being used for a sound room.
So...that means we can't functionally use the cd built in.
The idea is to use a usb cd burner.
So the internal cd was unplugged.
Now only using the usb cd burner/player.

The issue is, that when I insert a blank CD, I am supposed to get a popup asking to burn it as DATA or AUDIO (cda format)
This does not happen with the usb cdrom drive.

So when I go to burn a cd using CD Creator, it defaults to data only.
How do I fix it so I can choose cda format burning?
Big thanks!!

---

### Post by DVD-R on 2009-01-15
To date I haven't figured it out yet.
But I did find that if I
a) change "blank cd" action within the file manager
to DO NOTHING
b) put in blank cd and wait for it to appear in the desktop
c) open Serpentine
I can burn an mp3 into CDA format on the blank cd.

So at least the CDA burning function is working.
I will keep digging to find out how to get the AUDIO vs DATA prompt to initiate when I insert the blank cd.
Perhaps by calling out this drive as the master in the fstab file.

---

### Post by mc4man on 2009-01-15
Not sure if you mean your getting a pop up or not. (or if no pop up some action does occur upon inserting blank cd (same thing

If you are getting a pop up (or some auto action) then you can pretty much set it up as you want, you just need to decide which app and what do you want to have happen.( if you aren't then it's a moot point till you do

So if you are I'm not clear on which you want to use - Brasero, CD/DVD Creator (nautilus-cd-burner), or Serpentine

Brasero would be quite simple to have open in "New Audio Disk Project" as an auto run for blank cd insertion.
CD/DVD Creator has only one mode, already a default choice.
Serpentine may need a touch extra.

---

### Post by DVD-R on 2009-02-11
Thanks for your response,
I apologize for not being clear.
The way ubuntu is supposed to work with the insert of a blank CD is...

A popup appears asking you if you want to burn a DATA disk or an AUDIO disk.
The burn would be CDA format for audio and otherwise what ever the data files extension might be.

Yes in ubuntu one has the option of assigning a specific application to an inserted blank CD.
But that is a separate function.
If, for example I assign an application to open upon insert of the blank CD, it will simply burn the cd in DATA format as a default, even if I want CDA format.  It simply does not give me any option otherwise.

If, I assign serpentine as to application, when I insert the CD serpentine will come up and then immediately drop.
Don't know why it does that....it just does.

I am not using a internally configured CD machine.
I am using a USB burner.
In this case, ubuntu is not acting normal.

So at the moment I have to insert the CD, give it a minute and then open up serpentine.  Lo and behold, it then will burn CDAs.

At least I'm able to burn-em!!!  :)

I very interested if you think you might have a suggestion.

Thanks

---

### Post by mc4man on 2009-02-11
I don't have an external burner to fool around with and 3 weeks is a long time for my train of thought. See if I can get back on track.

If you open a terminal and use this

```
brasero -a
```

is that what you'd like to see?


As far as serpentine it does not have any available launch options that would be useful in this case (serpentine interfaces much better in 8.04 (maybe they'll be an updated package available, probably not

---

