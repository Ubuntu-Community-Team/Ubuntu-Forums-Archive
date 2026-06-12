---
title: "PIO v. DMA"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Steveplanetary on 2010-10-28
I've long been interested in general, and I'm interested in particular about the BOINC apps I run: Is there any way, other than reading the code (which I couldn't do anyway), of knowing whether a running app is using programmed IO or direct memory access to read from/write to the hard drive?  TIA

---

### Post by amauk on 2010-10-28
It's the operating system that determines which mode is used for accessing hard disks, rather than applications

With any PATA disk from the last 10 years, you're almost certainly using UDMA 5 or 6 (100 /133 mbps)

---

### Post by Steveplanetary on 2010-10-31
Thanks for the reply, amauk, but that prompts other questions.  The interface, by the way is ATA-100, so I assume the drive is capable of UDMA 5.  But doesn't the OS use PIO sometimes, and DMA at other times?  If the answer is yes, how does the OS decide which to use and when to use it?  And, not being a programmer, it would seem to me that PIO *implies* that the transfer method is carved into stone by the app.  I obviously don't know much about this.  Would you elaborate, please?  Thanks.

---

### Post by anewguy on 2010-10-31
If the OS is set for DMA access, it should use just that.  When an IDE interface contains more than 1 device, such as a hard disk and a CD-ROM, the interface will only run as fast as the slowest device.  In that case, I imagine (thought I've never really checked) if the CD-ROM drive was PIO (and it would need to be old for that) then it may be possible the hard disk might also only be accessed at PIO speeds - whether that means actual PIO or not I don't know.

Most "modern" hard disks and CD/DVD etc. drives will be DMA.  I know that sometimes in Windows you had to tell it to use DMA on a device, but I don't know if that's even true now.  Whether Ubuntu or other Linux's automatically use DMA if the device supports it I don't know.

I'll be following this to see how things turn out, though I am curious - are you having a performance problem or why are you concerned about this?  The normal user wouldn't be.

Dave ;)

---

### Post by cascade9 on 2010-10-31
> **amauk said:**
> With any PATA disk from the last 10 years, you're almost certainly using UDMA 5 or 6 (100 /133 mbps)

I've seen more than a few machines less than 10 years old that only had UDMA 33/66 drives (mainly 'corporate' machines)  

> **anewguy said:**
> If the OS is set for DMA access, it should use just that.  When an IDE interface contains more than 1 device, such as a hard disk and a CD-ROM, the interface will only run as fast as the slowest device.  In that case, I imagine (thought I've never really checked) if the CD-ROM drive was PIO (and it would need to be old for that) then it may be possible the hard disk might also only be accessed at PIO speeds - whether that means actual PIO or not I don't know.

That was true on very old systems, but anything even gettigng close to the ubuntu mimimum requirements will have independent device timing. 

> **Two devices on one cable — speed impact**

 There are many debates about how much a slow device can impact the performance of a faster device on the same cable. There is an effect, but the debate is confused by the blurring of two quite different causes, called here "Lowest speed" and "One operation at a time".
 **"Lowest speed"**

 It is a common misconception that, if two devices of different speed capabilities are on the same cable, both devices' data transfers will be constrained to the speed of the slower device.
 For all modern ATA host adapters this is not true, as modern ATA host adapters support *independent device timing*. This allows each device on the cable to transfer data at its own best speed. Even with older adapters without independent timing, this effect only applies to the data transfer phase of a read or write operation. This is usually the shortest part of a complete read or write operation.[[17]]("http://en.wikipedia.org/wiki/Parallel_ATA#cite_note-16")
 **"One operation at a time"**

 This is caused by the omission of both overlapped and queued feature sets from most parallel ATA products. Only one device on a cable can perform a read or write operation at one time, therefore a fast device on the same cable as a slow device **under heavy use** will find it has to wait for the slow device to complete its task first.
 However, most modern devices will report write operations as complete once the data is stored in its onboard cache memory, before the data is written to the (slow) magnetic storage. This allows commands to be sent to the other device on the cable, reducing the impact of the "one operation at a time" limit.
 The impact of this on a system's performance depends on the application. For example, when copying data from an optical drive to a hard drive (such as during software installation), this effect probably doesn't matter: Such jobs are necessarily limited by the speed of the optical drive no matter where it is. But if the hard drive in question is also expected to provide good throughput for other tasks at the same time, it probably should not be on the same cable as the optical drive.
[http://en.wikipedia.org/wiki/Parallel_ATA#Two_devices_on_one_cable.C2.A0.E2.80.94_speed_impact](http://en.wikipedia.org/wiki/Parallel_ATA#Two_devices_on_one_cable.C2.A0.E2.80.94_speed_impact)

---

### Post by anewguy on 2010-10-31
It's interesting, as I have read this many times I have to believe the people who wrote the articles must know what they are talking about.  However, in my experience, this has not stayed true.  I have a MSI Neo motherboard running an AMD64 3200+, nothing modern, but also nothing old either.  I have 2 IDE 80 gig drives - 1 from Maxstor, 1 from Seagate.  One supports ATA100, the other only up to ATA66.  When both of these drives are on the same IDE interface, there is a marked reduction in performance even though I'm not accessing the slower drive at all.  Windows and Ubuntu are both on the faster drive, and they both have an apparent reduction in performance when both devices are on the same IDE interface.  Split them across different IDE controllers and everything is back to normal.

So, coming from the old, old, old school (you don't even want to know how long ago!) I remember quite well how things used to be, how things have changed over the years, and the thing is that at least for my machine it still holds true.  I'm also quite familiar with such things as only 1 device at a time can be doing a transfer on an IDE interface - I wrote drivers for these things years and years ago when you had to build your own hard disk interface and provide all of the programming to access it.

Where I have really fallen short is on SATA.  I haven't had a SATA device that I've kept because my motherboard won't boot from the SATA interface(s).  So, i've just never bothered with it.  Not to mention that after years of very technical work starting with what are now extremely large boat anchors down to minis and down to what we now call a "PC", I got tired of "wanting to know" and started being the old fart I am and going with "as long as it works....".  This has made me lazy, made me forget a TON of stuff, and remember some incorrectly.

As I said, I've read many such articles, but just in my experience on my not *that* old motherboard, it doesn't hold true in my case.  Possibly this affects others as well.

I guess it's all rather moot - I'm more interested in why the OP is even concerned with it, as perhaps they are having another problem and someone has directed them to this as being the problem.  It might be something we can help with, or it might be something we can say "don't worry about it" to, but I'm curious to know.  As you know, the average user is not concerned with these things.  More than half the people who buy PC's have no idea what such things are, let alone care about them.

Dave ;)

---

### Post by P4man on 2010-10-31
If it takes less than an hour to boot your OS, then its using DMA.
OK, thats a slight exaggeration perhaps, but not even all that much; PIO is in-cre-di-bly slow. So slow there can be no confusion. Floppy drives use PIO. Stone age era CD roms used PIO. You know the ones that ran at double at quad speed. Wopping 150-300Kb/s.

---

### Post by anewguy on 2010-10-31
> **P4man said:**
> If it takes less than an hour to boot your OS, then its using DMA.
OK, thats a slight exaggeration perhaps, but not even all that much; PIO is in-cre-di-bly slow. So slow there can be no confusion. Floppy drives use PIO. Stone age era CD roms used PIO. You know the ones that ran at double at quad speed. Wopping 150-300Kb/s.

And.....rememer when that seemed incredibly fast?  ;)

Dave ;)

---

### Post by P4man on 2010-10-31
I never thought that was really fast, but boy, 650 MB was outrageous. Today we store images of your cd and dvd drives on our harddisk, back then a single CD could hold multiple images from my hd :)

---

### Post by anewguy on 2010-10-31
> **P4man said:**
> I never thought that was really fast, but boy, 650 MB was outrageous. Today we store images of your cd and dvd drives on our harddisk, back then a single CD could hold multiple images from my hd :)

Yeah - back in the day I was the first to get a hard disk in our group.  5 megabytes, and that was HUGE.  Sounded like a jet airplane engine running most of the time.

Dave ;)

---

### Post by cascade9 on 2010-11-01
5MB...I cant remember how big the 'winchester' HDD in my dads computer in the mid/late 80s was, but I *think* it was 10MB. 

> **anewguy said:**
> It's interesting, as I have read this many times I have to believe the people who wrote the articles must know what they are talking about.  However, in my experience, this has not stayed true.  I have a MSI Neo motherboard running an AMD64 3200+, nothing modern, but also nothing old either.  I have 2 IDE 80 gig drives - 1 from Maxstor, 1 from Seagate.  One supports ATA100, the other only up to ATA66.  When both of these drives are on the same IDE interface, there is a marked reduction in performance even though I'm not accessing the slower drive at all.  Windows and Ubuntu are both on the faster drive, and they both have an apparent reduction in performance when both devices are on the same IDE interface.  Split them across different IDE controllers and everything is back to normal.

As I said, I've read many such articles, but just in my experience on my not *that* old motherboard, it doesn't hold true in my case. Possibly this affects others as well.

Sorry if my post came across as 'its always like this'. I've heard of the exactly issue you have with IDE drives sharing a channel, I've just never run across it myself with newer motherboards. 

BTW, if you know, can you tell me the exaclt model motherboard, or even just the chipset? Thats the sort of info I try to store for later use. 

> **anewguy said:**
> Where I have really fallen short is on SATA.  I haven't had a SATA device that I've kept because my motherboard won't boot from the SATA interface(s).  So, i've just never bothered with it.  Not to mention that after years of very technical work starting with what are now extremely large boat anchors down to minis and down to what we now call a "PC", I got tired of "wanting to know" and started being the old fart I am and going with "as long as it works....".  This has made me lazy, made me forget a TON of stuff, and remember some incorrectly.

You could still use a SATA drive as an OS drive, just load GRUB to the IDE drive (or use any of the other ways avaible). But you aready knew that, right? ;)

---

### Post by Steveplanetary on 2010-11-01
I never imagined that my question would spark so many responses, but I'm glad it did. I learned a lot, and your replies are now carved in stone for others to learn from. I'm not having any performance problems, I just suffer from terminal curiosity. And that curiosity isn't limited to all things computer, although in the '90s I built my own computer.  The only computer I ever bought is the laptop I saved from The Fire Of 2005.
 
Being an old fart myself, and a disabled one without a car, my list of activities is rather short. Daytime TV (and much of it at night) is boring, and my bass guitar playing sucks, and always will, so I spend most of my time learning things on the Internet. And that's a good thing. There seems to be no end to the things I want to learn, and the Internet is a bottomless gorge of information.
 
Thank you all for your replies. You have done your good deeds for the week.
 
Cheers,
 
Steve

---

### Post by anewguy on 2010-11-01
> **Steveplanetary said:**
> I never imagined that my question would spark so many responses, but I'm glad it did. I learned a lot, and your replies are now carved in stone for others to learn from. I'm not having any performance problems, I just suffer from terminal curiosity. And that curiosity isn't limited to all things computer, although in the '90s I built my own computer.  The only computer I ever bought is the laptop I saved from The Fire Of 2005.
 
Being an old fart myself, and a disabled one without a car, my list of activities is rather short. Daytime TV (and much of it at night) is boring, and my bass guitar playing sucks, and always will, so I spend most of my time learning things on the Internet. And that's a good thing. There seems to be no end to the things I want to learn, and the Internet is a bottomless gorge of information.
 
Thank you all for your replies. You have done your good deeds for the week.
 
Cheers,
 
Steve

Hey, glad you at least aren't having any problems!  I'm on Social Security Disability myself, so I understand the TV idea, I can't play guitar, so I'm like you - I spend a lot of time online.  The difference?  You're at least still curious about things, whereas my mind just reached an "I'm full" (or as my friends would tell you, the "he's full of it") stage and I just don't seem to be able to find a way to be interested in much new anymore.  I do get curious sometimes when something comes up in the way of old-time hacking - you know, messing with the hardware and with programs to control it (not to be confused with the evil that hacking seems to be now).  I do start digging more then.

Hope you have a good day!

Dave ;)

---

### Post by anewguy on 2010-11-02
> **cascade9 said:**
> 5MB...I cant remember how big the 'winchester' HDD in my dads computer in the mid/late 80s was, but I *think* it was 10MB. 



Sorry if my post came across as 'its always like this'. I've heard of the exactly issue you have with IDE drives sharing a channel, I've just never run across it myself with newer motherboards. 

BTW, if you know, can you tell me the exaclt model motherboard, or even just the chipset? Thats the sort of info I try to store for later use. 



You could still use a SATA drive as an OS drive, just load GRUB to the IDE drive (or use any of the other ways avaible). But you aready knew that, right? ;)

Yeah, the biggest problem with trying use grub on an IDE drive is that I must have an IDE DVD drive also or I can't boot the various LiveCD's, Windows install CD's, etc..  I had gotten a nice SATA DVD drive and a large SATA hard drive to upgrade my PC, but when I got into still needing an IDE drive and not being able to boot from a SATA DVD drive, I just gave up for now.  Someday if I have some money I'll actually build something again that is at least current until I get the parts to the parking lot! ;)

Also, no offense taken at all on your post - I didn't read it as an all or nothing, but rather as showing how things are supposed to work but with exceptions.  The motherboard is an MSI K8T Meo-FIS2R.  It's got both VIA SATA and Promise SATA controllers, but just can't boot from any of them for what ever reason.  I thought I had gone through the BIOS, enabled the SATA and added the SATA device(s) to the boot list, but could never get it to boot SATA.  I think the IDE is also all VIA considering the motherboard and the K8 family chipset.

Again - no offense at all, and I hope I didn't come across that way either - didn't mean to!

Have a good one!

Dave ;)

---

