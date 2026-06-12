---
title: "Total beginner questions"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-03-28
First, absolute beginner is a good title.
Have a Toshiba L305-S5933Intel Pentium Dual T3400 @ 2.16GHz, 3 GB Ram, 32 bit OpSys, 224 GB HDD w/156 GB free, BIOS Version 2.10. (Fortunately found that info w/o too much effort.)

Very interested in 9.10 and have tried to do the MB5 thing but get nowhere with that. Have checked out the download instructions, followed to the letter, but cannot figure out what I need to do to check the 9.10 download and CD for accuracy. Don't see the MB5 anywhere.

Any instructions available for someone that had to take a class on how to turn a computer on? (Not really that bad but find lots of instructions that need to be written like the "For Dummies" books for those of us that don't "specialize" in 'puter talk.)

Thanks in advance for the patience and assists.

---

### Post by r-senior on 2010-03-28
Ah, you confused me there. I think you want to check the MD5 sum of your download?

Simplest way is from the terminal:

$ md5sum <your-downloaded-file>.iso

For example:

$ md5sum ubuntu-9.10-desktop-i386.iso

Then you can compare by eye, or copy and paste your resulting MD5 sum into a search on this page. 

[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

If it matches the ISO you downloaded, you are set.

---

### Post by flyfishingphil on 2010-03-28
Sorry about that. You are right on the md5sum but the main question is how do I get to that action you list above "$ md5sum ubuntu-9.10-desktop-i386.iso"? After downloading the md5sum package I don't find it listed anywhere so "where/how" do I check for integrity? Is that by clicking on the downloaded file and typing that in a box that appears? Directions on how/where to do that are greatly needed.
Thanks again.

---

### Post by tom.swartz07 on 2010-03-28
> **flyfishingphil said:**
> Sorry about that. You are right on the md5sum but the main question is how do I get to that action you list above "$ md5sum ubuntu-9.10-desktop-i386.iso"? After downloading the md5sum package I don't find it listed anywhere so "where/how" do I check for integrity? Is that by clicking on the downloaded file and typing that in a box that appears? Directions on how/where to do that are greatly needed.
Thanks again.

Im assuming that youre still running windows? 

This page will tell you how to get the MD5SUM for windows, if youre on something else, just scroll up on the page. [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Windows

---

### Post by r-senior on 2010-03-28
> **tom.swartz07 said:**
> Im assuming that youre still running windows?
Good point! :lol:

---

### Post by cloyd on 2010-03-28
Ok, for once, another beginner can help. MD5 . . . checks the integrity of the iso or image file you download.  I'm assuming you're running some version of windows. I didn't use it. I burned lots of CD's that wouldn't boot. A program that can check MD5 is available for windows. It can be downloaded from the net. Get it. it will save you time. Use Google. I did manage to get a good download and make a bootable flashdrive. I used unetbootin to convert my iso to a bootable drive.  It too is available to run in Windows from the net, It is free.  

"Idiots books" They can be helpful, and they are available for linux . . . The most recent edition of the _Idiot's Guide to Linux_ comes with a cd with more than one ISO linux distro on it.  Or, if you happen to have access to a Barnes and Noble or some other good bookstore, you might get "The Official Ubuntu Book."  It comes with a couple live DVD's that will boot if you modify your BIOS to boot from the cd drive. They are a bit pricey ($25-$45) depending of which on and where you get it. They are worth it, even if you can download the ISO's for free. There is lots of good information in the books, and the cd's have workable files on them.

Oh yes, the Official Ubuntu Book is available in a 9.04 and a 9.10 edition. I had the 9.04 edition. If you go this route, get the edition you want. I can't remember for sure . . . was the Idiot's Guide for 9.4 or 9.10? I'm not sure. Be aware if you buy.


Lots of times, as I started, I felt like there was a catch 22. A lot of the instruction I read assumed I already had Linux before I could download Ubuntu. Not true. You can start from windows, and get what you need. You will have to search a bit, but even a 60 year old non-techie like me can do it . . . I''m sure you can too.

---

### Post by flyfishingphil on 2010-03-28
Printing out pages suggested so I will have them to follow. Will download the md5sum as soon as fresh copy of 9.10 finishes downloading. Question: In reading thru some of the stuff it refers to using *infra recorder[I]and also refers to *iso reader[/I] either prefered? Also, prefered site for getting the md5sum and the iso "translator"?

---

### Post by flyfishingphil on 2010-03-28
Got you by a couple of years longer Cloyd! 

Found what I needed and did the ISO burn using the Infra Recorder. Checked download with MD5sum and everything matched. Now, how do I do the CD Integrity Check that is refered to in "BurningISOHowTo"? Where is this "page" it refers to? Can I check the CD using the md5sum, or is done another way. (Tried to use md5sum but can't figure out how.)

---

### Post by PocketDog on 2010-03-28
I wouldn't bother with all that MD5 checksum hassle. Just get Ubuntu via the torrent download: It puts less strain on Ubuntu servers, and torrents have their own hash check built-in anyway. If you have 100% of the download, you can be sure it really is 100%

---

### Post by tpjk on 2010-03-28
if you want to make sure your cd burned correctly you can also just choose 'check cd for defects' from the menu that comes up shortly after you boot from it.

[this is what the menu looks like](http://www.howtogeek.com/wp-content/uploads/2008/09/image42.png)

---

### Post by flyfishingphil on 2010-03-28
pocketdog. Thanks, already downloaded and sent to cd, so I'll just try it "Live" and see if everything appears proper.

tpjk, your link opens a "403 Forbidden" blank page. If I use it as "live CD" can I check it for integrity there?

Cloyd, went searching and found what appears to be a great beginners guide to Karmic at this location: [http://manuals.makeuseof.com.s3.amazonaws.com/MakeUseOf.com_-_Ubuntu_Karmic_Koala.pdf]("http://manuals.makeuseof.com.s3.amazonaws.com/MakeUseOf.com_-_Ubuntu_Karmic_Koala.pdf") Check it out and see what you think. In the meantime I'll take the authors advice, have a cup of tea and read the guide about a dozen times so it becomes comprehensible! (Old head injury makes it hard to remember what I just read unless I read it repeatedly. Honest!)

---

### Post by anewguy on 2010-03-28
You should probably down load the Linux guide mentioned in the sticky notes as well - it's free and quite comprehensive.

Dave ;)

---

### Post by cloyd on 2010-03-28
I've been off line for a few hours. The online guide looks good at first glance. I downloaded it. And, it  looks like there might be some other good things at that website. Thanks.  

I think some of the others here are giving pretty good advice.  I believe most of these folks have delved deeper into all this than I have.  As someone said, you can check the integrity of the burn after you burn the disk. Blank disks are cheap.

There is a load of good stuff on line.  I still recommend the other books. Though it looks like you are not going to need the cd's in the books.

---

### Post by tom.swartz07 on 2010-03-28
> **anewguy said:**
> You should probably down load the Linux guide mentioned in the sticky notes as well - it's free and quite comprehensive.

Dave ;)

This might be a long shot, dave, but are you related to THE gary larsen, are you?

---

### Post by cloyd on 2010-03-28
Just noticed . . . you've burned your cd with infrecorder  . . . you most likely have your bootable cd already . . . if it boots (or booted. . . . its been a couple of hours now) you should be home free.  You next big task should be do make a few decisions.  If the live cd works well, are you going to completely replace windows, or dual boot, or use wubi?  If you go the dual boot route (that was mine) try to really understand what you are doing before you start partitioning your drive.  Then as you install, watch what you are doing as you install so that you do not install Ubuntu on your windows partition. Prepare before you do this. It is worth the effort.

I just took a minute and looked closer at the Ubuntu Karmic Koala Bible.  I liked the detail it went into on the installation process.  I'd like to add a detail that may help . . . or may not. If you have Vista, you have a utility that will shrink your windows partition. It is possible to shrink a windows partition, and then have the installation program install Ubuntu on the largest free space . . . which will be that empty space you create with Vista.   The empty space won't exactly be a partition after you create it . . . it only becomes a partition when you format it with gparted or the installation program.  I do remember that this option (use larges free space) made a lot of decisions for me. It determinedd the size of my swap drive, for instance.

Shrinking the drive with Vista may not shrink the drive as much as you'd like it too.  I only took forty gig when I could have taken more. But, Ubuntu is not the hog that Vista is, and I've found that I can do an awful lot with forty gig.

---

### Post by anewguy on 2010-03-28
> **tom.swartz07 said:**
> This might be a long shot, dave, but are you related to THE gary larsen, are you?

No, but he warped my mind all the same!  It seems I can't hardly look at ANYTHING in the world now without either some Farside cartoon coming to mind or at least a "strange" thought a la The Farside.  Can't imagine life without that unique view! 

Dave :)

---

### Post by tom.swartz07 on 2010-03-28
> **anewguy said:**
> No, but he warped my mind all the same!  It seems I can't hardly look at ANYTHING in the world now without either some Farside cartoon coming to mind or at least a "strange" thought a la The Farside.  Can't imagine life without that unique view! 

Dave :)

AH! Nice. Love his comics. Im def the same way- haha.

Sorry for the distraction, continue with the thread
[/distraction]
[serious]

---

### Post by flyfishingphil on 2010-03-28
OK, I got to the Live CD side, after I figured out to change the boot sequence in Vista so it reads the cd first. I played with Karmic for a couple of days putting it into an older PC for my Grandson, and did a dual there. Haven't decided yet on whether to do a solo or a dual for the Ubuntu.

did find some interesting things though. Can't connect with my printer. I don't know if Ubuntu doesn't find it because it operates on WiFi, or it's just one that Linux doesn't recognize/work with. The printer is a Canon MP560 and didn't find it listed at the Linux org site or in the Ubuntu printer listings. Any suggestions there?

Did the test sequence and everything seemed to work fine. Recognized usb 4 plug in and the Logitech headset with mic. Worked fine. As did video.

Tried to do a Disk Integrity test but couldn't get that to work either. Was wondering if that was because it was in the Live CD mode and not installed.

Another question. I have a Maxtor One Touch 4 mini, 160GB capacity, and was wondering if I could install Ubuntu to that, as drive E, bring it up to full operation, try it out for a while from there then, if everything works properly install it alone on C and wipe out Windogs Viscious in the process.

Anybody? I'll check back tomorrow and see if there is hope for us totally lost in the land of "confusers".

Additional info: Did some searching thru the forums and found a reference to printer problems. If you are having trouble setting up your printer, it's not Linux recognized, go to [www.turboprint.info]("http://www.turboprint.info") and check the listings on all of the printers they have Linux drivers for. Found my M560 in that listing so will probably spend the $40 (+/-) and order the disc.(For Canon users go to [Canon Asia]("http://support-asia.canon-asia.com/")and you'll find the Linux drivers there.)

---

