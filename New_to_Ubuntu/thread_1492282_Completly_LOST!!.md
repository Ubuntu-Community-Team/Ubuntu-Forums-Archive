---
title: "Completly LOST!!"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by kiceman699 on 2010-05-24
Ok so I am new to all of this And Am trying to install on a Fresh HD in a Dell Inspiron notebook and am having nothing but problems!

If I try to install off the CD I burned from the site it is for version 10.4 and I start the computer with the CD in the drive set to load from CD and it loads to a point that says INVALID OPERATION SYSTEM!..
And from that point nothing!
I have another computer that I am using right now to get the info I want this laptop to be Ubuntu alone Operation system. 
The only thing on the Drvie right now is A Partition. 

Is there a link I can go to that will give me a Step by step! or for that mater can someone tell me what the problem is? 

I just can figer it out and am lost!


THANK YOU IN ADVANCE!!

---

### Post by roger_1960 on 2010-05-24
Hi

You need to use the "install using entire disk" (or similar) option.  It will not work using WUBI.

---

### Post by theozzlives on 2010-05-24
sounds like a bad burn, or .ISO

---

### Post by MrOneEyedBoh on 2010-05-24
Yep from what all I've gathered researching this all day long, it seems that it should be an easy install. try to reburn the image.

---

### Post by SlidingHorn on 2010-05-24
I don't know whether or not the .iso is your problem, but if you're going to go that route, make sure you check the md5 and burn at a low speed (4x would be ideal)

---

### Post by bodhi.zazen on 2010-05-24
> **kiceman699 said:**
> Ok so I am new to all of this And Am trying to install on a Fresh HD in a Dell Inspiron notebook and am having nothing but problems!

If I try to install off the CD I burned from the site it is for version 10.4 and I start the computer with the CD in the drive set to load from CD and it loads to a point that says INVALID OPERATION SYSTEM!..
And from that point nothing!
I have another computer that I am using right now to get the info I want this laptop to be Ubuntu alone Operation system. 
The only thing on the Drvie right now is A Partition. 

Is there a link I can go to that will give me a Step by step! or for that mater can someone tell me what the problem is? 

I just can figer it out and am lost!


THANK YOU IN ADVANCE!!

Are you trying to install a 64 bit OS on a 32 bit CPU ?

Otherwise, I assume you have a bad burn.

For a step-by-step guide see:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The screen shots are for Ubuntu 9.10, but the general options are the same.

---

### Post by sandyd on 2010-05-24
> **kiceman699 said:**
> Ok so I am new to all of this And Am trying to install on a Fresh HD in a Dell Inspiron notebook and am having nothing but problems!

If I try to install off the CD I burned from the site it is for version 10.4 and I start the computer with the CD in the drive set to load from CD and it loads to a point that says INVALID OPERATION SYSTEM!..
And from that point nothing!
I have another computer that I am using right now to get the info I want this laptop to be Ubuntu alone Operation system. 
The only thing on the Drvie right now is A Partition. 

Is there a link I can go to that will give me a Step by step! or for that mater can someone tell me what the problem is? 

I just can figer it out and am lost!


THANK YOU IN ADVANCE!!

are you burning the iso as a data file, or actually burning the iso to disk?

---

### Post by lisati on 2010-05-24
Some of the replies so far have suggested checking the downloaded file for errors. Some information can be found here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Another thing to check that has already been mentioned is **how** you burned the file. More information can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by nothingspecial on 2010-05-24
> **kiceman699 said:**
>  INVALID OPERATION SYSTEM!..

Does it actually say that? Post [COLOR="Red"]exactly[/COLOR] what it says.

> **kiceman699 said:**
> I just can figer it out and am lost!

Don`t worry, I was too. :)

---

### Post by kiceman699 on 2010-05-24
It dose Say Invalid Operating system!

And I have checked and rechecked the Burn I am sure it is a ISO it installs on another HD using My Hot swap Drive USB system to A 3.5 IDE HD.
in windows. so I dont know I am more so having a problem getting any of the HD's to be id'd 

ps sorry about the Spelling! that was never a Strong point of mine!

Also it is a 32 bit system.

I cant seem to get the Laptop to Id The HD's They both have a Partion on them and I don't know I just cant seem to figer this out! and it is getting under my skin! big time!

---

### Post by anarchywolf46 on 2010-05-24
I came across this problem on a Sony Vaio, the problem is your HDD is shot. I couldn't even access one with knoppix and had to force the computer to boot from a CD after I managed to get it past POST. The exact error message I would get otherwise was "Invalid operating system". Get a new HDD. If you don't believe me, try accessing the HDD with something like spinrite or knoppix. It will say the hdd is unrecognizable.

---

### Post by kiceman699 on 2010-05-24
Just went out and got a New HD And It is in there and still getting it!

---

### Post by halitech on 2010-05-24
what is the exact file name of the iso you downloaded?

---

### Post by anarchywolf46 on 2010-05-24
Check in the BIOS to make sure the HDD is being recognized and functioning.

During POST with the boot disk in, press 'esc' to enter the setup menu to choose what device to boot from and force it to boot from the CD.

If that doesn't work, make sure you don't have something jammed up in the connection. May need to clean it out.

Btw, is the voltage and amps required being supplied to the drive? There is an off chance you just keep frying the driver. Dell computers usually need Dell brands to function, as they get temperamental with other hardware.

---

### Post by SRST Technologies on 2010-05-24
> **kiceman699 said:**
> Ok so I am new to all of this And Am trying to install on a Fresh HD in a Dell Inspiron notebook and am having nothing but problems!

If I try to install off the CD I burned from the site it is for version 10.4 and I start the computer with the CD in the drive set to load from CD and it loads to a point that says INVALID OPERATION SYSTEM!.

In another post in this thread you said that with a USB disk the computer is working correctly.

I have no idea why another poster said to get another hard drive, it's impossible to tell if the hard drive is damaged at this point with what the information you have given us is so far.  Considering that you said it's a fresh hard drive, one would logically assume that the drive is fine since you've said nothing about POST errors being given.  I'm also assuming that the drive is showing up in BIOS CMOS Setup just fine.  In short, forget entirely that you were told to get another drive.

What's happening is that you've burned the ISO as a single file on a CD and tried to use that.  Then when you tried to install it to the USB drive, the installer you used is correctly extracting and setting up the contents of the ISO.

An ISO is a file, yes, but it's not just a regular file.  An ISO file is an exact (more or less) image of the contents of an entire CD (or other type of drive, but that's not important here).  If you were to open the ISO file in the Windows program WinRAR, you'd see that that ISO file has tons of files inside of it.  DO NOT EXTRACT THE ISO AND TRY TO USE IT.

Hard drives and CDs have a special spot on them called the Boot Sector which will not be extracted or usable when you extract the ISO.  Instead, find a good ISO Burning utility for Windows and burn the ISO file with that utility (as an "image" instead of as a "file").  Then try to boot that CD.  Burning an ISO as one file onto a disk does not produce a usable and bootable CD.  That's why you're getting an Invalid Operating System error.  The CD is not in the proper format, and the fresh Hard Drive has nothing on it.  Since the computer is not finding any usable bootable device, it quits trying and tells you there's no Operating System to use.

---

### Post by SRST Technologies on 2010-05-24
> **anarchywolf46 said:**
> 
Btw, is the voltage and amps required being supplied to the drive? There is an off chance you just keep frying the driver.

Pardon?  What driver, if there's no operating system loaded?  What power supplies do you use that can fry the bits and bytes in RAM that makes hardware work?

---

### Post by anarchywolf46 on 2010-05-24
> **SRST Technologies said:**
> Pardon?  What driver, if there's no operating system loaded?  What power supplies do you use that can fry the bits and bytes in RAM that makes hardware work?
What is loaded is the firmware chips that enable the computer parts to talk to each other. Since it is not built into the computer, it needs to tell the computer how to talk to it. Drivers are not only in the OS. The bits and bytes do not just exist in RAM, and chips can be very sensitive. To my knowledge, wrong power settings can fry a chip even in small amounts depending on the chip and also to my knowledge, computers need BIOS instructions to communicate with hardware, which is also why you can load a computer without a HDD, because it is not essential for a computer, only for permanent storage as you can remove the HDD and load up a live disk.

Also, I never said frying data in the RAM would make the hardware work. I would like to know what you read where I said frying data in the RAM makes hardware work.

The reason I suggested get a new HDD is because I have come across the problem before, and no data recovery tool could access it. It also gave no POST errors but just held the POST for a few extra minutes. If daring enough, try a live disk or see if it shows up in the BIOS, see if anything can access it.

Also, I was under the assumption he was burning the ISO correctly, but if not, hey I was wrong. But from my experience of running into that error, I spoke of what happened in my encounter. Sorry for stating my experience as fact, poor wording on my part. I'll have to proofread next to avoid that in the future.

---

### Post by SRST Technologies on 2010-05-24
... I think I'm just going to let this one go.

---

### Post by anarchywolf46 on 2010-05-24
> **SRST Technologies said:**
> ... I think I'm just going to let this one go.
Lol, if I am wrong somewhere down the line, it may be because I need sleep. Feel free to pm me if something I said wasn't true or misinformed. I thank you for your patience and maturity, cause clearly I'm not. But in all seriousness, if something is misinformed that I said, pm me and point it out to me so I can learn and not make the same mistake twice.

---

### Post by kiceman699 on 2010-05-24
> **SRST Technologies said:**
> In another post in this thread you said that with a USB disk the computer is working correctly.

I have no idea why another poster said to get another hard drive, it's impossible to tell if the hard drive is damaged at this point with what the information you have given us is so far.  Considering that you said it's a fresh hard drive, one would logically assume that the drive is fine since you've said nothing about POST errors being given.  I'm also assuming that the drive is showing up in BIOS CMOS Setup just fine.  In short, forget entirely that you were told to get another drive.

What's happening is that you've burned the ISO as a single file on a CD and tried to use that.  Then when you tried to install it to the USB drive, the installer you used is correctly extracting and setting up the contents of the ISO.

An ISO is a file, yes, but it's not just a regular file.  An ISO file is an exact (more or less) image of the contents of an entire CD (or other type of drive, but that's not important here).  If you were to open the ISO file in the Windows program WinRAR, you'd see that that ISO file has tons of files inside of it.  DO NOT EXTRACT THE ISO AND TRY TO USE IT.

Hard drives and CDs have a special spot on them called the Boot Sector which will not be extracted or usable when you extract the ISO.  Instead, find a good ISO Burning utility for Windows and burn the ISO file with that utility (as an "image" instead of as a "file").  Then try to boot that CD.  Burning an ISO as one file onto a disk does not produce a usable and bootable CD.  That's why you're getting an Invalid Operating System error.  The CD is not in the proper format, and the fresh Hard Drive has nothing on it.  Since the computer is not finding any usable bootable device, it quits trying and tells you there's no Operating System to use.



I think This mite be it!! I was over looking the fact that When I DL anything that is A ISO I have Power ISO and it Opens it and I mite have over looked it!

I will try this and get back to you I thank you all for what you have giving me so far it seems to be getting me going in the right way.

also the HD is brand new has a Partion on it that I have put on it. the drive shows up in post and is reg. in the Bios the computer that I am trying to get going will load cds but if I am in fact missing the fact and burning it wrong! that could vary well be.

Again Thanks I will let you know after I burn another disk!

---

### Post by kiceman699 on 2010-05-25
Thank you all for your help At this point I have got as far as the computer will let me at this point! 

I am setting this up for someone else by the way and they told me it is good to go and By the way I have now found out that There is not Enough Ram in it!! 

So I Thank all of you for your Time and help I am going to close this thread now that I have got to this point!

---

