---
title: "Synchronizing cache - Imgburn - Ubuntu Image"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by avnd on 2011-06-28
Hello there! 

I have downloaded an .iso of Ubuntu from the official website. The download went fine.  I, then, tried burning the image file to a blank CD. The process went fine till it got stuck at the 'Synchronizing cache' step. It was hanging for over half an hour. I thought a disk was wasted. 

So I forced shut Imgburn and then thought I might as well give that disc a try. (I thought I'd proceed because I have been stuck at that step before, though I don't really remember what I burned or what the consequence was). 

So, I booted from that disc and the Live version was running fine. 

So, my question is that "What can I expect from that disc? Is 'synchronizing cache' an important step really? Because if it is an absolutely necessary step, I might have to try it again. Otherwise, I could proceed with that install because the Live version was running fine".

 Any help is greatly appreciated. Thank you.

Aravind.

P.S. I totally forgot that the Imgburn log would be important and forgot to save that. Although my primary question right now is "What does synchronizing cache mean (in newbie language)? Is it absolutely important for an OS image?" rather than "What cause my system to hang at that step"?

---

### Post by FormatSeize on 2011-06-28
> **avnd said:**
> 
So, my question is that "What can I expect from that disc? Is 'synchronizing cache' an important step really? Because if it is an absolutely necessary step, I might have to try it again. Otherwise, I could proceed with that install because the Live version was running fine".
Synchronizing cache is the final step in finishing the copying process of a new CD. So what you have is a disc that has all the data of the original, but not quite as complete as the original. The synchronizing cache step is not critical to getting a copy of what you want, of course, that's barring trying to do odd-ball things with your new disc.
 
I wouldn't know what I would think of a disc that wasn't quite the original if this happened to me, though. If your disc works fine, then go with it. It should do what you want it to do without any problems, and I don't believe that future problems will pop up because you happened to use a disc that wasn't in sync with the original. 
 
If, in the future, you don't want to use discs that did not complete the sync process, try burning at a lower speed. With some drive/software combinations, it is best to go at the speed that the disc is rated as opposed to the highest one that you can push. It makes for a better burning process and may alleviate this "problem".

---

### Post by dFlyer on 2011-06-28
My advice is to download md5sum.exe and check the checksum of your iso before reburning the cd, than if the md5sum matches burn a new cd. Don't trust a cd that never completed successfully. It may seem to work and cause major headaches later.

---

### Post by avnd on 2011-06-28
Thanks for the replies, FormatSeize and dFlyer.

@FormatSeize: I actually tried burning the .iso on both Windows7 and another Ubuntu. With ImgBurn in Windows 7, I got a hang at the 'Synchronising cache' thingy. With Brasero in Ubuntu, I got a hang at something like 'Finalising' (I don't exactly remember the exact command when it stuck. 
As far as slowing the speed, I was actually advised to burn at the slowest possible speed when it comes to OS disks. I tried that(~2x). But ImgBurn said it wasn't compatible and automatically switched to a higher speed(~10x). I don't know why. 

@dFlyer:I have no idea what md5sum.exe is right now, mate. I'll give it a shot and let you know what happens. Thanks for the warning though. :)

---

