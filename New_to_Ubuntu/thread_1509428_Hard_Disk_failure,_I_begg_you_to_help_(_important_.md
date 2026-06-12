---
title: "Hard Disk failure, I begg you to help :( important data"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by medya on 2010-06-14
I had a 160 GB IDE hard disk, I used it for my download folder ,
it had two EXT3 partiions , 

for two nights, the Transmission gave me this error after some hours of downloading [read only partition] blah blah


then I ignored it,  I could hear some nasty noises in the hard disk and I gnored it as well, then I tried to analys the problem using the Disk Utiliy

it gave me two warnings , one of them was "imminent"  warning
the ther was "rellocate" warrning

then I used some bootable apps like UBCD , but it took forever, to analyse it, so I restarted it in the middle of it,
and then the noise that it had SOMETIMES, became permanent, now the computer wont identiy the hard disk .


before I try to analyze the hard disk, in partimagic bootable cd, i could read my files and sometimes I got error and it would become readonly. 
now I cant make it work and I keep getting this nasty noise

what to do ?

---

### Post by halitech on 2010-06-14
sorry to be the one to tell you but that "imminent" warning was one of drive failure and once it started making a noise, its toast. basically that noise is coming from the read/write arm hitting the actual platter inside the drive and once that happens, kiss your data goodbye. 

Doubtful that you will ever be able to get the data off the drive but there are commercial companies that may be able to take the drive apart and retrieve the data but they are costly.

---

### Post by warfacegod on 2010-06-14
Try booting into a LiveCD/USB to see if you can get anything from the drive. photorec (think that's the name) *might* help you get your data.

But to be perfectly clear, I agree with halitech's diagnose, your HDD has gone to the Great Cloud Computer in the sky. I recommend a Viking funeral.

---

### Post by KdotJ on 2010-06-14
This is why we back up folks. I know it's unlikely for a hard drive to fail but it's not impossible. Regular interval backups are always a good idea. Just my 2pence...

---

### Post by elliotn on 2010-06-14
Game over, bye bye to your hard disk

---

### Post by Calash on 2010-06-14
Sounds from your drive are a bad bad thing.  Is it a grinding or squeaking or more of a clicking?

If it is a clicking we may be able to get around the issue. Grinding or squeaking usually means damage to the platters or read/write heads.  In that case any attempt would probably cause more problems.

There are data recovery specialists you could send the drive to, depending on the value of the data on them.  Expect $200 diagnostic fee and near $1000 for recovery, probably more.

---

### Post by lukeiamyourfather on 2010-06-14
First, backup stuff you can't afford to lose. Its that simple. At this point you can either pay a data recovery service to repair the drives and retrieve data or attempt to repair the drives yourself to recover the data. Though you'd need another drive ***_exactly_*** the same to get parts from which is what the data recovery service would be doing.

If you don't want to pay the money for the service and don't have the skills to do it yourself then that data is gone. Booting with data recovery tools and scanning the disks will only make things worse, because its hardware failure, not a problem with the software.

EDIT: To clarify, backup stuff you can't afford to lose on a regular basis.

---

### Post by dookiebowser on 2010-06-14
If the data is really important you should stop using the drive ASAP, while it is still somewhat functional.

Do not attempt to repair the disk yourself. Bring it to a data recovery specialist, they will diagnose it. Depending on the diagnosis they may have to repair the disk which includes using a clean room (this is why you cannot do it yourself without risking damaging it further), and then they will be able to backup and recover your data.

If they deem it functional enough to backup and recover without repairing, it will be a lot cheaper. This is why you should stop using it while it is somewhat functional. It is definitely on it's way out though.

---

### Post by Don1500 on 2010-06-14
OP:"I had a 160 GB IDE hard disk."
Yup, You HAD a hard drive, now you have a paperweight. Is your data worth >$500?  No: buy another drive and start over. Yes: Take it to a recovery firm, and buy another drive to start over. Either way this drive is gone. 

Even Jesus saves.

---

### Post by dookiebowser on 2010-06-14
> **Don1500 said:**
> OP:"I had a 160 GB IDE hard disk."
Yup, You HAD a hard drive, now you have a paperweight. Is your data worth >$500?  No: buy another drive and start over. Yes: Take it to a recovery firm, and buy another drive to start over. Either way this drive is gone. 

Even Jesus saves.

It may not cost that much if they give a free evaluation/diagnostic, and if it isn't that complex of a problem. If they don't have to use their expensive clean room to physically repair the disk, it can be very cheap. Even cheaper still is if you bring your own media for them to use to backup to, like a 2nd hard drive or DVDs. Cheaper still is if you drop it off and pick it up rather than have them pick it up and deliver it (if they offer this service).

Just call a few places, bring it in to the ones that will do a free evaluation and give you a quote so you know what you are dealing with. Then weigh out whether the data is worth that much to you.

---

### Post by medya on 2010-06-14
Thanks everyone for replying me , loosing data is not any better than loosing a dear one .

I have had a Virtualmachine VDI (virtual disk file) on that hard disk ,
then i had a snapshop of that VDI , in another hard disk ,

I have important information on the Snapshot of Virtualbox, is there any way to make the snapsho of Machine work without the main VDI ?

the snapshot is pretty big, like 7 GB , can I derviate any data from that snapshot?

and Question Number 2 :

the noise was became constant when I tried to check the hard disk with some utility in Partimagic , is there any chance that I can make it work again by partimagic ? 

thanks everyone I apperciate your help .

---

### Post by Calash on 2010-06-14
> **medya said:**
> Thanks everyone for replying me , loosing data is not any better than loosing a dear one .

I have had a Virtualmachine VDI (virtual disk file) on that hard disk ,
then i had a snapshop of that VDI , in another hard disk ,

I have important information on the Snapshot of Virtualbox, is there any way to make the snapsho of Machine work without the main VDI ?

the snapshot is pretty big, like 7 GB , can I derviate any data from that snapshot?

and Question Number 2 :

the noise was became constant when I tried to check the hard disk with some utility in Partimagic , is there any chance that I can make it work again by partimagic ? 

thanks everyone I apperciate your help .

Can you describe the noise?  It would help to diagnose what is wrong with the drive.

Noise=Hardware failure.  At this point we are looking at how bad of a failure, and based on that we may be able to offer some help.

---

### Post by warfacegod on 2010-06-14
> **Calash said:**
> Can you describe the noise?  It would help to diagnose what is wrong with the drive.

Noise=Hardware failure.  At this point we are looking at how bad of a failure, and based on that we may be able to offer some help.

Agreed.

Clicking noise = backup or clone the drive immediately

Any other noise = give up

---

### Post by medya on 2010-06-14
it used to be Click noise, now it is something like Air Noise

---

### Post by Calash on 2010-06-14
Hmm.  Not sure about that one but I would guess you are on the bad side of things.  At this point I would suggest disconnecting the drive and checking the phone book for data recovery places.

If cost is an issue and/or you have a desire to try more you can but be aware that sounds like that usually indicate a problem with the head hitting the platter.  In these cases it is scraping the magnetic media and ruining any chance you may have of recovering the data.

In short, the more you try on the drive now the less likely it will be for a data recovery place to get your data later.

All that being said, if you want to try something there is always the "Freezer" method.  It has worked for me in the past to get data off a drive.  Remove the drive from the computer and put it into a watertight bag/container.  Put it in the freezer for 1/2 hour.  Reinstall and try your data extraction, LiveCD in this case.  

The cold air causes the metal to constrict and may bring things back to a somewhat usable position long enough for you to get what you need off the drive.

Some point:
DO NOT GET THE DRIVE WET
DO NOT TRY THIS UNLESS YOU HAVE NO OTHER CHOICE
DO NOT TRY THIS IF YOU HAVE WARRANTY COVERAGE


Good luck..

---

### Post by medya on 2010-06-14
thanks , I will try the freezing method, I have no warranty . has any other person tried freezing method ?

---

### Post by QIII on 2010-06-14
The one and only time I tried it, it worked.  But your failure may be entirely different.

However, as stated above, if you have physically damaged the platters you are likely out of luck.

---

### Post by warfacegod on 2010-06-14
I haven't tried it personally (no need) but I have heard of it. It is by no means a "recommended" method but unofficially, it's legit. Look at it this way, you really have nothing to lose. At this point, it can't make things worse. The only way for things to get worse would be a comet falling from the sky and turning your HDD into a plasma cloud of radioactive particles.

---

### Post by halitech on 2010-06-14
I've used it on a few drives with about 80% success rate. I usually go for a few hours instead of 30 minutes and wait about 10 minutes before hooking it up. it might work better if you have an external USB adapter that will allow you to hook the drive up without powering everything down.

---

### Post by cascade9 on 2010-06-15
> **medya said:**
> thanks , I will try the freezing method, I have no warranty . has any other person tried freezing method ?
 
 Yes, a few times. Its worked as much as its failed for me (I wish I had an 80% success rate). 

I've also done the platter swap a few times (what the professional data recovery companies do). Its not impossible to do at home, you dont need a clean room, but its a real pain. You have to be very careful, and have very good fine motor skills. Not something that I'd suggest most people try. 

> **halitech said:**
> I've used it on a few drives with about 80% success rate. I usually go for a few hours instead of 30 minutes and wait about 10 minutes before hooking it up. it might work better if you have an external USB adapter that will allow you to hook the drive up without powering everything down.

I've sat the box on top of the freezer and ran a IDE + molex cable into the freezer once. Mainly because I could get the drive going, but it would stop working as soon as the drive got warm...which happened before I could copy the files off the drive. :|

> **warfacegod said:**
> I haven't tried it personally (no need) but I have heard of it. It is by no means a "recommended" method but unofficially, it's legit. Look at it this way, you really have nothing to lose. At this point, it can't make things worse. The only way for things to get worse would be a comet falling from the sky and turning your HDD into a plasma cloud of radioactive particles.

+1. 

Well, things could get worse in other ways, eg- alien invasion, but thats not going to make your data come back, or disappear. Hmm, unless they use huge EMP bombs.....

---

### Post by medya on 2010-06-15
guys I put in in freezer , anod now the Click Noise is back, I Guess that is a Sucess ?
but still I cant get to make it known to pc

---

### Post by halitech on 2010-06-15
> **cascade9 said:**
> 

I've sat the box on top of the freezer and ran a IDE + molex cable into the freezer once. Mainly because I could get the drive going, but it would stop working as soon as the drive got warm...which happened before I could copy the files off the drive. :|


That is what happens to me most of the time as well and it took a few times for 1 drive to get all the data off the drive. Never thought of keeping it in the freezer and running cables inside.


> **medya said:**
> guys I put in in freezer , anod now the Click Noise is back, I Guess that is a Sucess ?
but still I cant get to make it known to pc

if you are still getting noises and the drive isn't being recognized I would say the drive is beyond the point of you saving the data yourself.

---

### Post by cascade9 on 2010-06-15
> **halitech said:**
> That is what happens to me most of the time as well and it took a few times for 1 drive to get all the data off the drive. Never thought of keeping it in the freezer and running cables inside.

I know somebody else who used a block of dry ice for the same reason. You could possibly even use ice in a sealed bag as well. 

> **halitech said:**
> if you are still getting noises and the drive isn't being recognized I would say the drive is beyond the point of you saving the data yourself.

+1, agreed.

---

### Post by Calash on 2010-06-15
> **halitech said:**
> ..if you are still getting noises and the drive isn't being recognized I would say the drive is beyond the point of you saving the data yourself.

The freezer method is far from perfect but at work I have used it a few times with mixed results.

Unfortunately I have to agree that the drive is a lost cause at this point.  Any further work will require much more advanced technical skills and endanger the possibility of recovering data further.  I would suggest deciding the value of the data on the drive and then shopping around for data recovery places to see if they can help.

My only other suggestion would be to put the drive in another computer on the off chance you are dealing with a power issue.  An external case should work as well.  You could also try moving the drive to a different power plug and unplugging any other drives.  Just power the system up enough to see if you get the clicking...no need for a bootable OS.


> 
know somebody else who used a block of dry ice for the same reason. You could possibly even use ice in a sealed bag as well. 


Unless it was bagged it must have made a horrific noise.  Metal makes a screaching noise when it comes in contact with Dry Ice.  Still, that is a very good idea as you would not have to worry about water vapor from the ice and the gas would help to keep water from gathering.

Now that I think of it...we have Liquid Nitrogen tanks onsite....;)

---

### Post by dookiebowser on 2010-06-15
You were willing to risk damaging the hard drive further before consulting a data recovery solution to get an expert opinion. I do not believe this data is that impr0ntant.

---

### Post by warfacegod on 2010-06-15
> ...we have Liquid Nitrogen tanks onsite...

I would guess that have the platters still able to spin would be preferable to having molecular motion nearly stop.

---

