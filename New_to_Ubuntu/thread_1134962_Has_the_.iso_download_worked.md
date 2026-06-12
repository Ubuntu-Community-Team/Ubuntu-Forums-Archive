---
title: "Has the .iso download worked?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by random turnip on 2009-04-24
Last night i left Ubuntu 9.04 downloading while i went to sleep (my internet is slow and it was getting late).  When i woke up this morning it said on Firefox something like "could not connect to your download" which worried me, and i had a look at the .iso file and it was 698MB instead of 699MB which it said it was going to be before i downloaded.

Am i going to have to re-start the download or is the 1MB just the computer and Firefox rounding the numbers up in different ways?

Basically, shall i use this ISO or download again?

The screenshot shows the file in the Firefox downloads bar and what Vista actually says about the file now that i've downloaded it.
[IMG]http://i247.photobucket.com/albums/gg128/random_turnip/ubuntu904download.jpg[/IMG]

Also, i later burned the ISO to CD just to see if it would, and it appears to have worked, but i haven't actually restarted with the CD in yet, is there much of a chance of it doing any damage if there is a MB missing somewhere?

---

### Post by Sarai the Geek on 2009-04-24
I had some trouble with downloading the .iso too, finally got it to work.

Try running an MD5SUM on the file to see if it's valid.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
You also have the option, when booting into the liveCD, to check disk integrity. If the MD5SUM comes back okay, be sure to do that as well.

---

### Post by lisati on 2009-04-24
Simple reply, YES, it probably has. Now to get it to do something. Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Elfy on 2009-04-24
Check the md5sum - that will tell you if it is ok.

Information for checking the sum - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The md5sums for Jaunty are here - [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by random turnip on 2009-04-24
It says
> MD5 sums are the same
So i assume that means i'm ready to instal, thanks guys.

One other small questions, on 8.10 my wireless card was simply incompatable (HP Pavillion dv9000, Broadcom wireless card), i heard that this was one of the main issues fixed in 9.04, so is there a decent chance it will work out of the box?

---

### Post by pbpersson on 2009-04-24
> **random turnip said:**
> i heard that this was one of the main issues fixed in 9.04, so is there a decent chance it will work out of the box?

It sure sounds like it to me :)

---

### Post by Sarai the Geek on 2009-04-24
> **random turnip said:**
> It says

So i assume that means i'm ready to instal, thanks guys.

One other small questions, on 8.10 my wireless card was simply incompatable (HP Pavillion dv9000, Broadcom wireless card), i heard that this was one of the main issues fixed in 9.04, so is there a decent chance it will work out of the box?

Doubt it. You'll probably need to install a proprietary driver, so have your ethernet cable on hand. However, with any luck it won't be entirely incompatible. :)
I have an HP Pavillion laptop too, getting wireless to work was a pain in the you know where. I haven't upgraded to Jaunty yet (tomorrow, hopefully!) but it sure would be great to see better support for broadcom cards, although broadcom certainly hasn't made it easy...

---

### Post by random turnip on 2009-04-24
Cool, well i'll try it out when i'm home and tell you how it goes, if it does work out of the box (my freind seems to think it will) i will litterally wee a little bit due to excitement.

---

### Post by potatan on 2009-04-24
I also have an HP Pavilion - a bit older than yours, it's a DV5000 - and the wireless does work, but I'd advise installing with an ethernet cable plugged in, in order to get the updates.  

Then once it's all up to date you should be given a popup message about proprietary drivers being available, including the Broadcom wireless controller (I also had an Nvidia one).  

Enable that, and the wireless should work just fine.

Good luck

---

### Post by jimv on 2009-04-24
Boot up from the CD and find out if it works.  Usually the easiest way to do it.

---

### Post by Sarai the Geek on 2009-04-24
> **random turnip said:**
> Cool, well i'll try it out when i'm home and tell you how it goes, if it does work out of the box (my freind seems to think it will) i will litterally wee a little bit due to excitement.

Too much information...

---

