---
title: "Is Brassero fixed yet?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-08-29
Could anyone please tell me when Brassero will be able to convert avi files into DVDs for the DVD player again?
It was working fine on my Pc until I clicked yes on the update manager! after that it stopped working!  it would be great to know what the update manager changed for it to stop working, and possibly an easy solution as I am a total novice?? please help

---

### Post by HotShotDJ on 2010-08-29
Bottom line... No.  Brasero is not fixed yet. I've tried to use it in the past for all sorts of burning, and have NEVER gotten it to work. I've removed it from my system and replaced it with K3B. I honestly don't know why it is included in Ubuntu.

---

### Post by redbook4574 on 2010-08-29
> **HotShotDJ said:**
> Bottom line... No.  Brasero is not fixed yet. I've tried to use it in the past for all sorts of burning, and have NEVER gotten it to work. I've removed it from my system and replaced it with K3B. I honestly don't know why it is included in Ubuntu.

Agreed stick with K3B

---

### Post by 1991sudarshan on 2010-08-29
Brassero is not upto the mark!! better use K3B it has many features!! the problem with brassero is it doesn't support multi-session properly!!

---

### Post by khelben1979 on 2010-08-29
Well... no matter which one is the best, he wanted to use Brasero. You can get the source [directly from their webpage]("http://projects.gnome.org/brasero/") if you're interested.

Edit: sorry if this is not a newbie advice b.t.w. but it's quite easy compiling the source, just have a look in the included README files and go slowly from there.

---

### Post by Herman on 2010-08-30
:D Hi everyone,
I'm having some trouble with brasero too.

I'm teaching my mother how to use brasero to copy one DVD to another DVD.

So, first we put in the DVD we want to make a copy of.
Next, a helpful dialog box pops up and offers us a drop-down list for what we want to do, open folder and view files or some other option, one option being to open brasero.
All is fine so far, so we choose 'open brasero', that's great!
Brasero opens and we want to copy the disc to the default, which is 'New Disc in the burner holding the source disc'.
A progress bar shows up and we wait for several minutes, and when it is finished our CD drawer opens and we remove the copied DVD.
Brasero reports "Success, 100% done!"
Please replace the disc with a writable CD or DVD.
An image of the disc has been created on your hard drive.
Burning will begin as soon as a writable disc has been inserted.

Now there are two or three things that go wrong at this point.
First, we insert a blank DVD and wait .... nothing happens.
So, we wait and wait and wait.
There is no 'OK' button, so the only option other than to wait, is to click 'Cancel', which seems to abort the operation, so we have to do it all over again.
We get up to the stage where we insert a blank writable DVD, and this time we waited a really, really long time and still nothing.

After several more tries at this, I'm wondering where in the hard drive, exactly, is brasero storing all these .iso files?
I tried a search but it does not reveal any new files with the .iso extension.

Now, I'm not exactly a newbie around here, and I'm perfectly capable of making my own copy of a CD or DVD with a dd command.
I guess that's what I'll do now, but I have to say I'm quite disappointed with brasero.

Questions:
What am I doing wrong?
Is it only me, or are other people experiencing the same problem(s)?
Is there something wrong with the brand of blank DVDs we're trying to use?
Shouldn't brasero have an 'OK' button beside the 'Cancel' button so user can tell it when we have inserted a writable disc and want to prompt it to continue, or if not at least give us an informative error message?
Does the user need to be informed where brasero is putting all these files it's copying so we can go and delete them if the process fails?
Should I be filing a bug report?

Regards, Herman :confused:

---

### Post by bodhi.zazen on 2010-08-31
> **HotShotDJ said:**
> Bottom line... No.  Brasero is not fixed yet. I've tried to use it in the past for all sorts of burning, and have NEVER gotten it to work. I've removed it from my system and replaced it with K3B. I honestly don't know why it is included in Ubuntu.

It works "OK" but I agree k3b is IMHO a better application.

If you want a lighter weight alternate, try xfburn.

---

### Post by candtalan on 2010-08-31
> **Herman said:**
> :D Hi everyone,
I'm having some trouble with brasero too.

[...]

An image of the disc has been created on your hard drive.
Burning will begin as soon as a writable disc has been inserted.

Now there are two or three things that go wrong at this point.
First, we insert a blank DVD and wait .... nothing happens.
[...]
Questions:
What am I doing wrong?
Is it only me
[...]
Regards, Herman :confused:
No it is not only you. I stopped using brassero at Ubuntu 10.04 when I started to get problems and Brassero simply did not do what it promised.
It made me sad that 10.04 was flakey like this and would cause problems particularly for newcomers.

The very easy option is to use the excellent k3b
Ubuntu Software Centre>k3b
hth

---

### Post by kelvin spratt on 2010-08-31
I don't think its all to do with Brassero  as I don't use Ubuntu and Brassero seems to work Ok. The only thing I don't use it for is to compile movies. I use Devede for that its far more superior than any other Linux app runs on windows as well,

---

### Post by JBAlaska on 2010-08-31
+1 on DeVeDe for transcoding avi's
+1 for k3b or xfburn for burning.

---

### Post by Herman on 2010-08-31
It could be some kind of hardware/driver problem in this case, I'm not sure. It could read the CD to copy from okay, but it couldn't seem to recognize the blank disc to copy to at all.
We tried both DVD -R and DVD +R discs.
Neither Brasero nor K3b could burn a disc in this computer.
Even selecting the .iso and clicking 'burn to disc' wouldn't work, at least there was an error message, 'Please replace the disc with a supported CD or DVD'.
I eventually got a copy of the same .iso I copied with the dd command burnt to disc in a different computer. 

I still think it would be nice if there could be some way provided for the user to get some kind of feedback or error message from the program when a blank DVD is inserted but isn't recognized. Otherwise, the user is just left waiting and scratching their head. 

I'll experiment with brasero and k3b some more in a couple of days when I get back home. 
Thanks for all your help and advice everyone. :D

---

### Post by Herman on 2010-09-03
:-k Okay, I'm home I'm still curious about why Brasero could burn a DVD in one of Mum's computers but not in the other.

Actually, I wasn't really interested in Brasero and DVD burning to start off with, I would prefer to continue learning and practicing how to use kdenlive for editing home videos. The DVD burning issue is a side issue for me. Before I got sidetracked too much I wanted to spend a little more time on my main project, but as often happens to me, I find an answer to a question I have while doing something different, when I'm not even looking for it. To learn more about video formats I was reading about [AVCHD]("http://en.wikipedia.org/wiki/AVCHD") in the wikipedia and by coincidence I saw a link about DVD rot and clikcked on it.
I'll include a link to it here because I think this page is an interesting one, ["DVD Rot" /  DVD Longevity and Reliability  (9/2003)]("http://www.manifest-tech.com/media_dvd/dvd_compatibility.htm"), it explains a lot of other issues with the use of DVDs besides just DVD rot. It's worth a few minutes to read right through the article, it's only one page, but for those who may be in a hurry, 

[LIST=1]
[*]there are good quality DVDs for sale and poor quality DVDs.
[*]the DVD media needs to be compatible with the DVD drive we want to use
[*]some DVD drives can tolerate poor quality media better than others
[/LIST]

---

### Post by Herman on 2010-09-03
I decided to try a few simple experiments while doing something useful and backup up some old files at the same time.

I inserted a blank DVD into the optical drive of my main computer, it's one I assembled myself and it has a SONY DVD RW drive and the operating system I'm using is Ubuntu Lucid Lynx.
```
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-710A '
Revision       : 'BY02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED
```I must mention now that I have used this same DVD drive in a different computer and had no problems with it, but since I started using it in my newer computer with the ASUS P5QL PRO I have noticed it seems to have become fussy about what CDs and DVDs it will work with and I have not yet been able to determine any rhym or reason.
```
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P5QL PRO
    Version: Rev 1.xx
    Serial Number: MS1C88B21200276
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0
```In my first experiment, and attempt at burning a data backup DVD failed after "Creating checksum for image files, Getting size, Starting to record, Ejecting medium."
I was given a pop-up message, "Unknown error burning", and it gave me the opportunity to save the error log, which I happily did.
The log file has a line near the bottom, "media is not formatted or unsupported".

SO, for my second experimnent I transfered the same files to an older computer I have, my Acer T-310, which also runs Ubuntu Lucid Lynx.
```
herman@T-310-II:~$ sudo dmidecode -t baseboard
[sudo] password for herman: 
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Acer
    Product Name: E61ML 
    Version: (null) 
    Serial Number: 987654321

herman@T-310-II:~$ cdrecord -checkdrive dev=/dev/scd0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-4082B'
Revision       : 'A201'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
```
I tried again using the same blank DVD that my newer computer was not able to burn to.
I was given an error message, " Unable to mount data disc, Error mounting: mount: block device /dev/sr0 is write protected, mounting read-only."
In spite of the apparent error message though, the data was successfully recorded to the DVD using this computer.

Meanwhile, back in my newer machine, I tried using CD/DVD creator to see if it would be any better than Brasero. Probably they're both front-ends for the same program that does the actual work, but nevertheless I thought it might be interesting to try it anyway.
The result was another pop-up window to tell me,"ejected medium", and another log file with the error message: "media is not formatted or unsupported".

Looking around the room I found a different spool of blank DVDs, and this one contained blank DVDs with a nice shiney gold colour on top, with the brand name "SONY".
Bearing in mind that it's my SONY CD/DVD drive that I seem to be having problems with, I decided to try the SONY brand DVDs. The SONY brand DVD drive should be expected to be compatable with SONY brand DVDs one would expect.
I recieved another error message, this time it is 'You do not have permission to write to this drive", and saved yet another log file.
Again though, in spite of the apparent error message, the data was successfully burnt to the DVD.

Conclusions: It's too early to draw any conclusions from only the small number of experiments I have tried, but it look like the link I provided in the above post is right, it's important to select a good (quality) brand of CDs or DVDs to write to, and when we find a brand of DVDs that work with our particular DVD drive, stick with the same brand.

The song I'm listening to now: "Don't Cuss the Fiddle", by Waylon Jennings and Wille Nelson, and the moral of the story is to take the time to try a few experiments first instead of just complaining and blaming the operating system, program, programmers or developers. (Meaning that's what _I_ should have done first). :)

---

### Post by Randicus on 2010-09-11
If anyone is still looking at this thread; don't worry, you are not alone. I see many theories, including hard-ware problems. My opinion is that the problem is 10.04. I never had any problems burning c.d.s with any programme. Brasero and K3b both worked perfectly. However, since up-grading to 10.04 I have not been able to burn c.d.s with any programme. I can only hope the bug is worked out for the next edition and I do not lose anything important before then.

---

### Post by jtarin on 2010-09-11
Using 10.04 I have gone Brasero, K3B...now Gnome Baker which seems to burn and copy to suit me....with the exception of no multi-session. Promised for near future release.

---

