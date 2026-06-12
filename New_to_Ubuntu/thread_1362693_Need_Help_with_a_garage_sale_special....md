---
title: "Need Help with a garage sale special..."
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-12-23
Ok... So I was at a garage sale just browsing and the lady at the sale just happens to see me looking at the computer stuff....
Anyway, I say what do I need another computer for...
Then see says how about Dell laptop and a Avio desktop for 10bucks....
Well ok.

Soo... at the moment I have puppy linux running on the laptop and Karmic running on the desktop.

The lady said that the Avio
VGC-RA830G ,PCV-A21L just locked up on her.
When I installed the live session it just fired up fine although the drives appeared wiped.

I installed on 1/2 raid drives and everything seems to be going more or less ok on the software side

I think there is something screwy going on the hardware side.
I can hear what sounds like a relay clicking every so often.
Every so often, apps just freeze, although if I wait long enough things come back.

When I Ctrl-Alt F2'd I got a message:
end_request: I/O error dev sda

My understanding is that this might be either a issue with the controller or the hard drive.

Is there a way to isolate this? I suppose if its the drive, I could install on the other hard drive and see if the problem goes away.

Any suggestions would be appreciated.

Thanks
JT

---

### Post by HeadHunter00 on 2009-12-23
> **Jonas thomas said:**
> When I Ctrl-Alt F2'd I got a message:
end_request: I/O error dev sda

My understanding is that this might be either a issue with the controller or the hard drive.
Yeah, the hard drive is messed up or unmounted. You have to open it up and change the hard drive, or check if it's connected or not.

---

### Post by Jonas thomas on 2009-12-23
It seems to be intermittant....
Is there a diagostic routine, that can isolate the issue further?

---

### Post by K.J. on 2009-12-23
There's usually a HDD self-test in bios.

---

### Post by cascade9 on 2009-12-23
> **Jonas thomas said:**
> I think there is something screwy going on the hardware side.
I can hear what sounds like a relay clicking every so often.
Every so often, apps just freeze, although if I wait long enough things come back.

When I Ctrl-Alt F2'd I got a message:
end_request: I/O error dev sda


Classic sign, and sound, of dieing hdd. 

You could try downloading and running hdd manufacturers diagnostic tools. Cant hurt :)

---

### Post by Jonas thomas on 2009-12-23
> **cascade9 said:**
> Classic sign, and sound, of dieing hdd. 

You could try downloading and running hdd manufacturers diagnostic tools. Cant hurt :)

Ok hard drive I can deal with controller would be bad...

I did a little searching this looked interesting...

[http://ubuntuforums.org/showthread.php?t=511346]("http://ubuntuforums.org/showthread.php?t=511346")

has any messed around with smartmontools ?

I'm going to see what I got in the bios for tests..... Back in a few..

---

### Post by PhilMize on 2009-12-23
[Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html")

There are a few hard drive diagnostic tools on that live disc that should help you figure things out. Plus many many other useful tools for other parts of your computer. I suggest you give it a shot.:P

---

### Post by Geoff918 on 2009-12-23
The included disk utility in Karmic (Pamplimpsest - sp?) will provide a disk health reading if you just click on the drive.

It will tell you how many bad sectors, if there are any spin-up, spin-down issues, etc. It's pretty robust when it comes to reporting disk health. It will also provide standard traffic-light indicators (green, yellow, red).

You can always still run it off a live CD and/or a USB flash drive. Hey, for $10 why not?

---

### Post by Jonas thomas on 2009-12-23
> **Geoff918 said:**
> The included disk utility in Karmic (Pamplimpsest - sp?) will provide a disk health reading if you just click on the drive.

It will tell you how many bad sectors, if there are any spin-up, spin-down issues, etc. It's pretty robust when it comes to reporting disk health. It will also provide standard traffic-light indicators (green, yellow, red).

You can always still run it off a live CD and/or a USB flash drive. Hey, for $10 why not?
In the live disk of Karmic on of the start up options is:
"Check disc for defects"
Does this mean hard drive or CD?

---

### Post by Geoff918 on 2009-12-23
> **Jonas thomas said:**
> In the live disk of Karmic on of the start up options is:
"Check disc for defects"
Does this mean hard drive or CD?

The start-up would be checking the LiveCD for defects. Basically making sure there wasn't a burn error. That would not check your hard drive.

If you then boot into the LiveCD you can select the disk utility and mount your HDD and check it there. :)

---

### Post by Jonas thomas on 2009-12-23
> **Geoff918 said:**
> The included disk utility in Karmic (Pamplimpsest - sp?) will provide a disk health reading if you just click on the drive.

It will tell you how many bad sectors, if there are any spin-up, spin-down issues, etc. It's pretty robust when it comes to reporting disk health. It will also provide standard traffic-light indicators (green, yellow, red).

You can always still run it off a live CD and/or a USB flash drive. Hey, for $10 why not?

Ok... I seem to be getting a Reallocated Sector count... and 
"Type""Failure is a sign of immient disk falure(Pre-Fail)
This doesn't sound good. 

I have two 160 gig drives. and one formatted one of them.  I wonder if I should just clone the drive and disconnect the first one. Would that work??

---

### Post by swoody on 2009-12-23
The 'Check disc for errors' checks your installtion medium for errors. I would reccomend - as the others have said - to find a HDD diagnostic tool from the manufacturer, either for the laptop, or the HDD. The clicking is generally a sign of a failing/broken HDD, and that seems to be the obvious first place to check :)

---

### Post by Geoff918 on 2009-12-23
> **Jonas thomas said:**
> Ok... I seem to be getting a Reallocated Sector count... and 
"Type""Failure is a sign of immient disk falure(Pre-Fail)
This doesn't sound good. 

I have two 160 gig drives. and one formatted one of them.  I wonder if I should just clone the drive and disconnect the first one. Would that work??

Sure, that would work. Will you be storing important information on the disk, or can you just run it until failure?

How did you format the one? The reallocated sector count could be a couple of things, whether it has detected bad sectors, or whether the disk size is being misreported from BIOS. Several things, really.

---

### Post by Jonas thomas on 2009-12-23
> **Geoff918 said:**
> Sure, that would work. Will you be storing important information on the disk, or can you just run it until failure?

How did you format the one? The reallocated sector count could be a couple of things, whether it has detected bad sectors, or whether the disk size is being misreported from BIOS. Several things, really.

The pc came with two maxtor 6y160MO 164gb
I guess maxtor was bought out by seagate.
[http://www.maxtor.com/home-en-us.html](http://www.maxtor.com/home-en-us.html)

Nothing critical on the computer yet.. Basically a fresh install with a some tweaks getting the monitor and sound to work.

If this is just a hard drive issue, I wouldn't mind turning this into my primary machine.

---

### Post by Geoff918 on 2009-12-23
> **Jonas thomas said:**
> The pc came with two maxtor 6y160MO 164gb
I guess maxtor was bought out by seagate.
[http://www.maxtor.com/home-en-us.html](http://www.maxtor.com/home-en-us.html)

Nothing critical on the computer yet.. Basically a fresh install with a some tweaks getting the monitor and sound to work.

If this is just a hard drive issue, I wouldn't mind turning this into my primary machine.

Okay, then you'll probably want to install whatever the stable hard drive is for the system. You could also run the second drive at your option, but I would only put non-critical "don't care if it's unrecoverable" type data on there.

---

### Post by Jonas thomas on 2009-12-23
> **Geoff918 said:**
> Okay, then you'll probably want to install whatever the stable hard drive is for the system. You could also run the second drive at your option, but I would only put non-critical "don't care if it's unrecoverable" type data on there.

Is there a utility to clone on the live CD? I suppose once cloned I should figure out how to boot from the other drive and erase the data on the "bad" drive but keep it formatted....  Then again.. I suppose the cleanest would just be to install Linux on the other drive and just reconfigure.... Right???

---

### Post by Geoff918 on 2009-12-23
> **Jonas thomas said:**
> Is there a utility to clone on the live CD? I suppose once cloned I should figure out how to boot from the other drive and erase the data on the "bad" drive but keep it formatted....  Then again.. I suppose the cleanest would just be to install Linux on the other drive and just reconfigure.... Right???

Probably just install Linux on the other drive and it should configure itself.

---

### Post by Jonas thomas on 2009-12-23
> **Geoff918 said:**
> Probably just install Linux on the other drive and it should configure itself.
Ok... I'm not claming I know what I'm doing here....
I disconnected my bad drive and put the data cable from that drive unto the unformatted drive.

When I went to live session and attempted to install I got a message
"No root file system is defined.  Please correct this from the partioning menu"
I seems at ths point I'm stuck in the installer.
I seemed like system=>Administration=>Gparted would be the logical next step.  I'm a little lost here as to what to do.  A huge amount of options non (that I can find) say anything about root file system...
I guess I need to do a little googling here....

---

### Post by Jonas thomas on 2009-12-23
> **Jonas thomas said:**
> Ok... I'm not claming I know what I'm doing here....
I disconnected my bad drive and put the data cable from that drive unto the unformatted drive.

When I went to live session and attempted to install I got a message
"No root file system is defined.  Please correct this from the partioning menu"
I seems at ths point I'm stuck in the installer.
I seemed like system=>Administration=>Gparted would be the logical next step.  I'm a little lost here as to what to do.  A huge amount of options non (that I can find) say anything about root file system...
I guess I need to do a little googling here....

From [http://ubuntuforums.org/showthread.php?t=449116]("http://ubuntuforums.org/showthread.php?t=449116")
The say that I need to change from ext2 to swap.

Only thing I got is Linux-Swap.  I forgot to hit the check box to apply..
If I'm doing something really stupid here, please feel to chime in for I know not where I tread here..
[Edit]
This makes some more sense
[http://ubuntuforums.org/showthread.php?t=449116]("http://ubuntuforums.org/showthread.php?t=449116")
(Getting closer)

---

### Post by Jonas thomas on 2009-12-24
The garage sale special seems to doing ok...
I have Linux on the good drive and iffy drive is there if I need it.
The Bios was setup in a Raid configuration which was screwing up the works.
Once I disabled that, everything went very smoothly.

Best 10 bucks I ever spendt.  :)

---

