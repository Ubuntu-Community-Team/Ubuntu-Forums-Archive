---
title: "copying dvd to computer then burning"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-23
I have my Ubuntu box set up to read dvd movies.

I have a personal movie, that has no copyright codex on it, that I simply want to copy to the computers HD and then burn as many copies of the movie as I please.

I do have an external dvd-r drive that I could put a disk in the laptop and then burn right over to the dvd-r drive if that can be done without copying the dvd to hd.

However, I'd still like to know how to do it by copying it to hd [also would like to know if it could be done with dvd in laptop and external dvd-r drive without copying to hd]

---

### Post by lidex on 2009-10-24
You can create an image of the disk in .iso format on your hard drive using Brasero. That should be available on standard install. With disk in drive open Brasero and click the "Disc Copy" button. In the dialog that appears, click on the drop-down list under "select a disk to write to" and choose the "image file" option. It will choose a location for you or you can select the "properties" button for more options.

---

### Post by mjp29 on 2009-10-25
> **lidex said:**
> You can create an image of the disk in .iso format on your hard drive using Brasero. That should be available on standard install. With disk in drive open Brasero and click the "Disc Copy" button. In the dialog that appears, click on the drop-down list under "select a disk to write to" and choose the "image file" option. It will choose a location for you or you can select the "properties" button for more options.

So far I'm with you and I did burn a .iso file which saved itself in the home folder.

Now, when I take out the disk that was copied from to make a .iso file and then inserting a new dvd-r to make a copy (burn to), do I select "disc copy" or "burn image" to make the actual backup copy.

I must have done something wrong because my first attempt, because my backup copy would come up on any dvd player but only come up to the first screen [which is a screen where the first seen on the movie is a still rame picture to select to push play] where one normally pushes play on the remote control.  When I play, it just sat there and didn't play.

---

### Post by lidex on 2009-10-25
> **mjp29 said:**
> 
Now, when I take out the disk that was copied from to make a .iso file and then inserting a new dvd-r to make a copy (burn to), do I select "disc copy" or "burn image" to make the actual backup copy.


Burn image

---

### Post by kixome on 2009-10-25
if you want to transcode from dvd9 8.xgig to dvd5 4.3 gig then 
#sudo apt-get install  k9copy and make sure you have libdvdcss2.deb installed if not search and install for new dvds, then use the k9copy assistant! make a donation, cuz those guys rock!

---

### Post by mjp29 on 2009-10-25
> **lidex said:**
> Burn image


I burned image also.

What is confusing me about Brasero are 2 things

Brasero tells me that the copy will be done one one drive; however, the ISO disk image it makes of a DVD movie is only around 31 MB in size.

When one ejects the actual DVD after the image is made, it doesn't surprise me that the burn that it makes to the dvd-r that I insert into the drive isn't complete 

because Brasero never asks for the original disk to be inserted during the burn and I just can't logically believe that Brasero is making a burned copy of an original dvd movie from a 31 mb size (even though Brasero does the burn and indicates that the burn/copy is complete).

---

### Post by mjp29 on 2009-10-25
> **kixome said:**
> if you want to transcode from dvd9 8.xgig to dvd5 4.3 gig then 
#sudo apt-get install  k9copy and make sure you have libdvdcss2.deb installed if not search and install for new dvds, then use the k9copy assistant! make a donation, cuz those guys rock!


Actually, that is good information for the future.  However, the disk I'm copying was recorded in a DVD player/recorder bought at Walmart.  So, I'm sure it isn't an 8 gig movie (like a store bought dvd movie from a major movie studio).

In fact, I just checked the dvd's size, and it is 4.3 GB.

However, perhaps k9copy will allow me to make a copy of it, because Brasero seems to be helping me only make a bunch of cup coasters.

---

### Post by SuperSonic4 on 2009-10-25
Yes k9copy will let you, just be sure to make your output *ISO Image* instead of *MPEG-4 Encoding*

---

### Post by halitech on 2009-10-25
if its a normal 4.3gig dvd, I would suggest using K3B to make a copy of it. Is the dvd in a format that will play in a normal dvd player? if it is, then yes just make a copy. If its not, you will need to convert it to something like avi and then convert it to dvd format.

---

### Post by mjp29 on 2009-10-25
> **SuperSonic4 said:**
> Yes k9copy will let you, just be sure to make your output *ISO Image* instead of *MPEG-4 Encoding*


ok thanks

this disk is not copyrighted; however, in the future if i choose to back up one of my store purchased movies, will k9 allow one to do that or would one need to use a few programs in combination.  For example, in Mac osx one first uses mac the ripper then has to use another program later to do the burning

---

### Post by mjp29 on 2009-10-25
> **SuperSonic4 said:**
> Yes k9copy will let you, just be sure to make your output *ISO Image* instead of *MPEG-4 Encoding*


ok thanks

this disk is not copyrighted; however, in the future if i choose to back up one of my store purchased movies, will k9 allow one to do that or would one need to use a few programs in combination.  For example, in Mac osx one first uses mac the ripper then has to use another program later to do the burning

---

### Post by mjp29 on 2009-10-25
> **kixome said:**
> if you want to transcode from dvd9 8.xgig to dvd5 4.3 gig then 
#sudo apt-get install  k9copy and make sure you have libdvdcss2.deb installed if not search and install for new dvds, then use the k9copy assistant! make a donation, cuz those guys rock!

I looked with Syanptic package installer and searched and couldn't find "libdvdcss2.deb".  How can I install that please.

Question:  What does k9copy assistant do?  Does one need to use k9copy and then use k9copy assistant to get the job done?

---

### Post by halitech on 2009-10-25
> **mjp29 said:**
> ok thanks

this disk is not copyrighted; however, in the future if i choose to back up one of my store purchased movies, will k9 allow one to do that or would one need to use a few programs in combination.  For example, in Mac osx one first uses mac the ripper then has to use another program later to do the burning

not that I advocate doing anything illegal, but I've only run across a few dvds that K9copy refused to copy and a few may have been due to me doing a fresh install and forgetting to install all my codecs and extras I needed :oops:

---

### Post by halitech on 2009-10-25
> **mjp29 said:**
> I looked with Syanptic package installer and searched and couldn't find "libdvdcss2.deb".  How can I install that please.

Question:  What does k9copy assistant do?  Does one need to use k9copy and then use k9copy assistant to get the job done?

I think you need to have the medibuntu repo added to your list and then look for libdvdcss2. You don't need to include the .deb as that is understood that it will be downloaded in a deb format

not sure what k9copy assisant is for, I've never used it.

---

### Post by lidex on 2009-10-25
Documentation for k9copy can be found here:
[https://help.ubuntu.com/community/K9Copy]("https://help.ubuntu.com/community/K9Copy")
Be aware as a KDE app it requires kde dependencies to run.

---

### Post by lidex on 2009-10-25
mjp29:

You may have used incorrect settings for the initial disc copy operation in Brasero. I just created an iso from dvd with no problem. Screenies below.

---

### Post by mjp29 on 2009-10-28
did you mean to say "refused to copy" when you typed "refreshed to copy" 

?

---

### Post by halitech on 2009-10-28
yes, that was a typo on my part, was thinking of other things at the time I was typing.

---

### Post by mjp29 on 2009-10-29
> **lidex said:**
> Documentation for k9copy can be found here:
[https://help.ubuntu.com/community/K9Copy]("https://help.ubuntu.com/community/K9Copy")
Be aware as a KDE app it requires kde dependencies to run.

I read the documentation and so did my wife.  I guess we are both just clueless.  

Please, someone give it to me in baby steps.  I put the dvd in and open k9copy and don't know what to click to tell it to make an image (or iso image) to the computer.  In fact, my wife got frustrated because 2 dvd movies showed up in k9copy, each being identical and identical in size, yet there is only one movie on this dvd.  I can't even figure out what to click to tell it to make an image - there are so many options in k9copy.

Yikes- someone just slap me.  Doh!

---

### Post by halitech on 2009-10-29
what version of K9copy do you have installed? I have 2.3.3 and I can post a screen shot but I don't want to confuse you if its a different version then I have.

---

### Post by mjp29 on 2009-10-29
> **halitech said:**
> what version of K9copy do you have installed? I have 2.3.3 and I can post a screen shot but I don't want to confuse you if its a different version then I have.

I installed k9copy in the past week.  I opened it and tried to figure out which version it was in preferences or about k9copy but couldn't find any option to check the version.  Tell me how to check the version and i'll do that.

thanks so much for your reply!

---

### Post by halitech on 2009-10-30
In mine its under Help - About K9copy

---

### Post by mjp29 on 2009-10-30
> **halitech said:**
> In mine its under Help - About K9copy

2.3.0 is my version

---

### Post by halitech on 2009-10-30
ok, hopefully they are close to the same

if you look in the upper left, you should see an input and an output. Select the dvd drive as the input and for the output, select iso file. you will then get an option of where to save it, put it where ever you want. Then click on copy. It should automatically select the proper compression to have it fit on a normal dvd.

---

