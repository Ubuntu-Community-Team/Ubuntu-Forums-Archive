---
title: "Nero Linux 3.5.2.3"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-02-20
Is anyone using Nero Linux 3.5.2.3 in Ubuntu 8.10?  If so, is it working?  If it is, could someone help me figure out how to burn CD's in it?  I can't seem to figure it out.  Thanks!!!

---

### Post by Rucas on 2009-02-20
Didnt even know they had a Linux version.
You should read the helpfile that must have followed with your Nero, since its a commercial product. But usually its a fairly sytaight affair.
Drag and drop or select the files to burn (ususally in some menu), select burn speed and what ever other options and thats pretty much all there is to it.
Usually at the start up you should get a menu that lets you choose what kind off project you also want to burn, like an ISO file, or data, video, etc...
Hope it helps a little.

---

### Post by kaibob on 2009-02-20
I'm using Nero Linux, and it works fine. 

Burning a CD is pretty straightforward: create a "New" compilation; drag the files from the file browser window to the compilation window; and then burn the CD. 

You can view the user manual--which is very complete and amply illustrated--by entering the following in a terminal window:

```
evince /usr/share/doc/nero/Manual.pdf
```

---

### Post by hifly1231 on 2009-02-20
> **kaibob said:**
> I'm using Nero Linux, and it works fine. 

Burning a CD is pretty straightforward: create a "New" compilation; drag the files from the file browser window to the compilation window; and then burn the CD. 

You can view the user manual--which is very complete and amply illustrated--by entering the following in a terminal window:

```
evince /usr/share/doc/nero/Manual.pdf
```

Thanks!!!  It's working great!!!  Now all I have to do is learn how to burn an .iso file!!! :rolleyes:

---

### Post by konqueror7 on 2009-02-20
i've tried nero linux before on hardy, but if i correctly remembered, its a commercial trial right? i think it got 30 days trial or something...uninstalled in and used brasero/gnomebaker instead...

---

### Post by Ben Page on 2009-02-20
Or if you don't like Brasero, you can use K3b, its a burning app for KDE4, looks nice, and can burn an *.iso file with 2 clicks.

---

### Post by binbash on 2009-02-20
> **hifly1231 said:**
> Thanks!!!  It's working great!!!  Now all I have to do is learn how to burn an .iso file!!! :rolleyes:

Open nero

From Recoder Menu, select burn image and select the image you want to burn

---

### Post by kaibob on 2009-02-20
Deleted by Kaibob

---

### Post by hifly1231 on 2009-02-20
> **pedja_portugalac said:**
> Why would you use nero-linux when you have all you need in Ubuntu (out of the box)? Use Brasero, it's great and free.
PS: Using proprietary software, such as nero, you can harm your dear OS!!!

I've installed Nero Linux 3 because I absolutely **_CAN'T_** get any of the CD burners in my repository to work in Ubuntu 8.10.  Not the built in, not Brasero, not K3b, and not Gnomebaker.  I'm not sure whether it's a bug in Intrepid Ibex or not, but I've read where other people are having this problem as well.  Nero Linux is working great.  I just don't know exactly how to burn an .iso file to disk because I've never done it before.  But I think it would be great to know how.

---

### Post by kaibob on 2009-02-20
> **hifly1231 said:**
> ...Nero Linux is working great.  I just don't know exactly how to burn an .iso file to disk because I've never done it before.  But I think it would be great to know how.

When you say ".iso file" are you referring to an ISO image (i.e. disk image)? If so, as previously mentioned, just select *Recorder > Burn Image* from the top menu in Nero.

---

### Post by hifly1231 on 2009-02-20
> **kaibob said:**
> When you say ".iso file" are you referring to an ISO image (i.e. disk image)? If so, as previously mentioned, just select *Recorder > Burn Image* from the top menu in Nero.

I'm doing that, and it's saying that it's burning the iso image, and says that the burning's completed, but it's not burning it to the disk like it does when I burn a song to disk.  I must be missing something.

---

### Post by kaibob on 2009-02-20
> **hifly1231 said:**
> I'm doing that, and it's saying that it's burning the iso image, and says that the burning's completed, but it's not burning it to the disk like it does when I burn a song to disk.  I must be missing something.

I downloaded gparted ISO as a test and burned it to a CD. I have included a screenshot below. Make sure you have selected CD or DVD in the upper left corner and remove the check mark from simulation. An alternative, as suggested by another forum member, is to double-click on the ISO file in Nautilus and the Nero burn dialog will appear.

Are you certain that the ISO is not corrupted or otherwise damaged? Gparted Live CD is a good test:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by halitech on 2009-02-20
> **hifly1231 said:**
> I'm doing that, and it's saying that it's burning the iso image, and says that the burning's completed, but it's not burning it to the disk like it does when I burn a song to disk.  I must be missing something.

the ISO you are currently trying to burn, is it a dvd iso or a cd iso? (ie. 4.4gig or 700meg)

---

### Post by hifly1231 on 2009-02-20
> **pedja_portugalac said:**
> I disagree with you. When I start to use Ubuntu, Brasero wasn't there out of the box and I didn't want to mix KDE and GNOME applications. So I tried nero, the application I was using when I was on XP (I never pay applications - not even XP OS). What happened was many freezes along with many fu..ed CDs and DVDs and of course security holes it leaved so I reinstalled brand new Ubuntu without it and I used command line utilities for all kind of jobs. But now with Brasero you have authentic nero burning room for linux out of the box. Someone say here, how to burn an .iso image, with Brasero just double click on it (.iso) and Brasero open right project. Nothing more then that. The only thing nero-linux can do Brasero for the moment can't is burning BD discs (blue ray) but then again I think it's very bugy. That said, if you want to f.ck with nero, use stolen serials or drop some money for nothing do it, it's your right...

OK, I'm working with a fresh install of Ubuntu 8.10, and I can't get ANY of the CD burning utilities to work, not even the built-in.  How did you get Brasero to work in Ubuntu 8.10?  I'm also not understanding how Nero Linux 3.5.2.3 debian package is going to leave a security hole in my Ubuntu.(?)  It's awfully funny to me that Nero Linux 3 works, but nothing else does.  I didn't want to install DeepBurner in WINE, because the ONLY thing I use WINE for is my Visual Link Spanish CD's (I have no other choice).  I don't like having any "Windows programs" installed in there.

---

### Post by hifly1231 on 2009-02-20
> **halitech said:**
> the ISO you are currently trying to burn, is it a dvd iso or a cd iso? (ie. 4.4gig or 700meg)

I'm trying to burn an ISO of Windows XP SP3 to put inside my VirtualBox.  I'm using a Memorex CD-R 52X 700MB disc.

---

### Post by hifly1231 on 2009-02-20
> **kaibob said:**
> I downloaded gparted ISO as a test and burned it to a CD. I have included a screenshot below. Make sure you have selected CD or DVD in the upper left corner and remove the check mark from simulation. An alternative, as suggested by another forum member, is to double-click on the ISO file in Nautilus and the Nero burn dialog will appear.

Are you certain that the ISO is not corrupted or otherwise damaged? Gparted Live CD is a good test:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

So are you telling me to try and burn this ISO as a test?

---

### Post by kaibob on 2009-02-20
> **hifly1231 said:**
> So are you telling me to try and burn this ISO as a test?
That's correct--just as a test. You can use any image file; I suggested gparted because it is so widely downloaded that there can be no question that the image itself is OK.

---

### Post by halitech on 2009-02-20
> **hifly1231 said:**
> I'm trying to burn an ISO of Windows XP SP3 to put inside my VirtualBox.  I'm using a Memorex CD-R 52X 700MB disc.

I'm not sure but I thought you could mount an ISO in Virtual box to boot from so you can install instead of having to have it on a disk?

I know this doesn't solve your burning issues but would at least allow you to get XP running in VB

---

### Post by mgmiller on 2009-02-21
The absolute easiest way to burn an .iso to disc is to right click the .iso and then select "Write to Disc".  It's handled natively by gnome.  

When you put a blank disc in the burner, here is what should happen:
You should see a dialog open that says a blank disc has been inserted and asks you what to do.  Just close this dialog.  

Also, there should be an icon on your desktop that represents the blank disc.
Do not click on that.

If the dialog and desktop icon don't appear, then you may have some issues with /etc/fstab and the way your optical drives are mounted there.

So, to recap:
Insert the blank disc, close any dialogs that open, right click the .iso and select "Write to Disc".

---

### Post by kelvin spratt on 2009-02-22
hiffly
You can use a iso direct in virtual box no need to burn.

---

### Post by handy on 2009-02-23
> **alexandari said:**
> Nero linux? are you joking me? there`s nothing better than k3b...

For you, on your hardware perhaps.

For me on my hardware what you say is not true.

When burning lots of disks k3b will crash, NeroLinux under the same circumstances does not.

---

### Post by hifly1231 on 2009-02-24
> **mgmiller said:**
> The absolute easiest way to burn an .iso to disc is to right click the .iso and then select "Write to Disc".  It's handled natively by gnome.  

When you put a blank disc in the burner, here is what should happen:
You should see a dialog open that says a blank disc has been inserted and asks you what to do.  Just close this dialog.  

Also, there should be an icon on your desktop that represents the blank disc.
Do not click on that.

If the dialog and desktop icon don't appear, then you may have some issues with /etc/fstab and the way your optical drives are mounted there.

So, to recap:
Insert the blank disc, close any dialogs that open, right click the .iso and select "Write to Disc".

I would LOVE to be able to do this, but as I stated before, I am working with a fresh install of Ubuntu 8.10, and I suspect (from my own experience, and also what I've been reading on the Internet) that there's a CD burning issue with Intrepid Ibex.  Right clicking and selecting "Write To Disk" would be awesome.  Same with burning songs to CD.  It's just not working in my Intrepid Ibex.  I actually even reinstalled a few days ago to make sure that something didn't go wrong with my last install, and still the same thing.

---

### Post by MasterNetra on 2009-02-25
Are you trying to burn the iso to a 100% BLANK disc? And try not to format the discs either...(erase CD-RWs don't format though)

---

### Post by stchman on 2009-02-25
> **hifly1231 said:**
> Is anyone using Nero Linux 3.5.2.3 in Ubuntu 8.10?  If so, is it working?  If it is, could someone help me figure out how to burn CD's in it?  I can't seem to figure it out.  Thanks!!!

Was Nero Linux free?  

Ubuntu has Brasero OOB and K3b just an install away.

---

### Post by mgmiller on 2009-02-25
I believe this problem can be addressed in 2 parts.  

The first is the immediate problem of getting burning to function at all.  You have installed Nero and hopefully can get some help from the person who offered to assist you outside of the forum.  

That being done, the other part is why can't 8.10 burn using any of the built in repo accessible apps?  I have about 6 Ubuntu boxes running at the moment, but only 1 of them has a burner and it has been upgraded many times since it's original install with 5.04.  I have also recently upgraded my burner from an older TS-H552 PATA burner to a brand new Sony SATA lightscribe burner.  Both worked without a hickup, even the lightscribe part.  

So my questions are:
What burner are you using?
What interface (PATA or SATA)?
If it's PATA are the jumpers set correctly on the drive? If it's the only drive on the PATA cable, it should be set to master, not "cable select".
What firmware is in the burner and can it be upgraded?

Your entry in /etc/fstab may need to be tweaked.

Have you googled your model burner for Linux (or Windows for that matter) problems?  I have run accross burners in other peoples machines that are nothing but trouble.  Replace them with a known good brand and model and all the problems disapear.  Sometimes all it takes is a firmware update.

---

### Post by hifly1231 on 2009-02-25
> **TransitMan said:**
> You know how to get ahold of me if you don't want to do the thread, for sake of others flaming or not reading correctly.

I'm sending you a message.

---

### Post by halovivek on 2009-02-26
i use Brasero. it is really good and it saved me lot in pain with paid one softwares.

---

### Post by hifly1231 on 2009-02-27
Question answered thanks to TransitMan.

---

### Post by blueridgedog on 2009-02-27
> **hifly1231 said:**
> Question answered thanks to TransitMan.

Congrats Mark.  I hope Nero works for you.  I think the Linux version is a sign of the growing market share of Linux and I am pleased to see it.  There are those who use Linux from a "free as in speech" perspective and they have philosophical issues using software that is not open source (it is not the fact that the software costs). 

I hope you take some time to trouble shoot your hardware as the tools built into Ubuntu now are great!  I can double click an ISO file and burn it, or right click it and open it in VLC or any number of other options. 

I just bought a cheap $25 lite on burner to add to my new rig and it meets my needs.

---

### Post by bodhi.zazen on 2009-03-02
I closed this thread as the OP question has long since been answered. 

Moving the discussion of nero 4 linux to recurring discussions.

Please keep threads on topic and the conversation civil ;)

---

