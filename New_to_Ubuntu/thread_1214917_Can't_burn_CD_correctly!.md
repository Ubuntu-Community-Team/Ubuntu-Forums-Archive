---
title: "Can't burn CD correctly!"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Ergo0100 on 2009-07-16
Hi!

I have spent more than 10 CD's and downloaded more than 5 different distros but i can't burn correctly the CD!!! Please anybody help!!!I'm using Infrarecorder at the lowest speed!!! and I'm reading the CD's with a Samsung DVD rom reader and another cd reader. Please HELP!!!

It throws me:

end_request: I/O errors
and others many buffers errors

Please help! i have only 3 CD's left!!!!!:(:(:(

---

### Post by Cheesemill on 2009-07-16
Have you checked the MD5SUM of your downloads to make sure that the .iso you are trying to burn has downloaded without any errors?

---

### Post by halitech on 2009-07-16
can you burn anything and have it read in another machine? possiblity that your burner is on the way out to the trash :(

---

### Post by Ra-Hoor-Khuit on 2009-07-16
Download the .iso file via a torrent, if you can.  Torrents auto-verify the file integrity as they download almost guaranteeing you a "good" file to burn from.

Then, assuming you're operating in a Windows environment, try using **Deep Burner** to burn your bootable media:

[http://www.deepburner.com/download/DeepBurner1.exe](http://www.deepburner.com/download/DeepBurner1.exe)

I suggest burning at a *moderate* speed of about 4x or 8x for a CD.

---

### Post by Ergo0100 on 2009-07-16
Yes. i have checked the MD5SUMs
No. I haven't tried the CD in other CD rom lector. 
My CD burner is my laptop integrated cd lector also! I have burned DVD's and CD's without any problems.
I'm going to check if the problem is my PC's CD lector.

EDIT: I made the integrity check 4 times:
In the frist time it found 33 errors
In the second time it found 11 errors
in the third time it found 66 errors
and in the fourth time it found 65 errors.
What the hell is happening?!

---

### Post by philinux on 2009-07-16
Can you give us a link to the iso you downloaded.

---

### Post by 0x29a on 2009-07-16
I'm pretty on board with Halitech on this. It sounds as if there's a problem with the memory builtin to the drive. One thing to also try would be to reseat the drive and at the motherboard. It seems like a simple thing,but I've solved similar problems many times by this.

I've used Infrarecorder on many occassions and it's always worked well for me, so I don't suspect it's the culprit, unless there's some driver or other component that's missing, although I can't think of what off the top of my head. It worked fine under XP on an Inspirion 9200 without any tinkering. I'd used the combination to burn bootable CDs all the time.

Let us know what you discover. I'm curious to know what you find out now. :)

Good luck!

---

### Post by Ergo0100 on 2009-07-16
Ok! now... How can I reset the CD drive? and i have downloaded Xubuntu 8.04.1 Desktop i386 fron xubuntu.org and from the US mirror.

EDIT: The MD5 check is correct!!

---

### Post by LewRockwell on 2009-07-16
I know it's absurd to think you haven't checked...but I have seen filthy optical drives before

blocked or diffused optics may cause problems(and erradic ones at that)

.

---

### Post by Elep.Repu on 2009-07-16
I'm not sure if I'm missing something..

What drive do you have?

> **LewRockwell said:**
> I know it's absurd to think you haven't checked...but I have seen filthy optical drives before

blocked or diffused optics may cause problems(and erradic ones at that)

.

^

---

### Post by 0x29a on 2009-07-16
Depending on what type of laptop you have, it may have a release level to remove it, or a couple of screws. This is to just **reseat** the drive, and not reset the drive. If you get it out, it will also be a good time to pop it open with a paper clip through the hole at the front of the tray, and brush it out with a small paint brush (don't touch the lens with your fingers, of course). I also agree with Ra-Hoor-Khuit about using a moderate burn speed. I typically burn anything important at 8x-16x.

We'll get it figured out. :)

---

### Post by Ergo0100 on 2009-07-16
I have a Toshiba DVD ROM SD-R2512 drive
Unfortunately i cannot reseat it because it's integrated to the laptop.

---

### Post by Elep.Repu on 2009-07-16
Time to get a new one.
Go to Walmart and buy a Sony.

If not, burn it on another computer sir!

---

### Post by Ergo0100 on 2009-07-16
I'm going to burn it on another computer! also i'm going to test the Xubuntu CD in that computer.

---

### Post by 0x29a on 2009-07-16
> **Ergo0100 said:**
> Unfortunately i cannot reseat it because it's integrated to the laptop.

I'm sure it's being held in with small screws on the bottom of the laptop. Sounds like your on the right track to get the CD to burn somewhere at least. Sweet.


In any event, shop locally, and don't shop at Walmart. :p

---

### Post by Elep.Repu on 2009-07-16
> **0x29a said:**
> I'm sure it's being held in with small screws on the bottom of the laptop. Sounds like your on the right track to get the CD to burn somewhere at least. Sweet.


In any event, shop locally, and don't shop at Walmart. :p

Why not shop at walmart?
I paid more when I bought it from the manufacturer. 
Walmart saved me 20 dollars.
Local people cost more. ("But it's wrong") I don't care, it costs less for me, why does it matter.

---

### Post by LewRockwell on 2009-07-16
another issue with using laptops to burn optical media is that you should leave the laptop alone while it's burning

continuing to utilize the laptop while attempting to write to optical media may cause errors in the process due to an excessive amount of vibration/movement

needless to say, if you're whacking away at the keyboard...

well, you know...

.

---

### Post by Ergo0100 on 2009-07-16
i have the error!!!!! the problem are mi old PC's cd drives. I perfecly booted Xubuntu with no errors in the integrity check in other laptop (not this)!!! If the problem was that, i can say: I have 10 different ubuntu's and xubuntu's CD roms for shipping and gifting to my friends... the problem now is to find them... Tanks to all of you!!! you have really helped!! Sorry if i have wasted your time... Next time I'll make the full procedure!! 

Bye all!

Ergo0100

---

### Post by 0x29a on 2009-07-16
> **Ergo0100 said:**
> If the problem was that, i can say: I have 10 different ubuntu's and xubuntu's CD roms for shipping and gifting to my friends... 
Bye all!

Ergo0100

That rocks! Thank you for sharing the outcome to all of this. I personally don't feel it's ever a waste of time.

Good luck!

Andrew

---

