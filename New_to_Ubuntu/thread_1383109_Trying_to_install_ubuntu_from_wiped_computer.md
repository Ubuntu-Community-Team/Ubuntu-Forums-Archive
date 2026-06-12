---
title: "Trying to install ubuntu from wiped computer"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by crazymf on 2010-01-16
I own an old Sony Vaio desktop that was running XP. It was running really slow, so I figured I'd install Ubuntu on it and see how it does. I wiped my hard drive by using DBAN, and that worked fine. I downloaded Ubuntu and burned it to a disk using Infrarecorder. I tried putting it into the computer and it told me NTLDR missing, please restart. I opened by BIOS and it said the CD drive was the primary place to boot from so I have no idea what is going on. Thank you to anyone who can help.

---

### Post by AlexDBall on 2010-01-16
Try re-burning a CD.. 
If it fails, try UNetBootin to create a bootable USB memory stick and select the USB drive as the first boot option from the bios (or boot menu).

---

### Post by baddog144 on 2010-01-16
You need to tell your computer to boot from the CD drive. When your computer starts up, look for a message saying "Press DEL to enter BIOS menu", or something similar. The exact key may be different. Press this key, and look for an option to change the boot sequence. Move "CD drive" to the top, and reboot

---

### Post by crazymf on 2010-01-16
I tried re-burning it still with no luck. I just tried your suggestion and it won't even let me choose to boot using a USB drive. I can only use a CD/DVD, floppy, or HD

---

### Post by baddog144 on 2010-01-16
So when you choose CD/DVD, with the disc in there, does it still give you the NTDLR message? :/

---

### Post by crazymf on 2010-01-16
exactly. I don't understand why the computer would need it because xp isn't there anymore and ubuntu doesnt need it to install right?

---

### Post by baddog144 on 2010-01-16
EDIT: Sorry, didn't read your OP well enough. 
Are you sure Infrarecorder didn't have a particular option to make a bootable disc?

---

### Post by crazymf on 2010-01-16
I used Infra recorder the first time and when that didnt work, i tried the burner that came with windows 7 on a different computer

---

### Post by baddog144 on 2010-01-16
Hmm, that should've worked. I'm out of ideas, sorry :(

---

### Post by crazymf on 2010-01-16
Well thanks anyway

---

### Post by warfacegod on 2010-01-16
> **crazymf said:**
> I used Infra recorder the first time and when that didnt work, i tried the burner that came with windows 7 on a different computer

In Windows you can't simply burn your ubuntu file onto disc and have it work. It needs to be done as an ISO. If you right click your ubuntu file their should be an iso option of some kind.

---

### Post by warfacegod on 2010-01-16
This what I used when I still used Windows. It never failed me.

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

---

### Post by crazymf on 2010-01-16
Yea thats the one I did. Anyway, the Infra recorder should have worked too right?

---

### Post by warfacegod on 2010-01-16
> **crazymf said:**
> Yea thats the one I did. Anyway, the Infra recorder should have worked too right?

Never used it but it ought to have if you followed the instructions on the Ubuntu download page.

---

### Post by crazymf on 2010-01-16
well Ill try isorecorder and see if that works

---

### Post by qamelian on 2010-01-16
> **warfacegod said:**
> In Windows you can't simply burn your ubuntu file onto disc and have it work. It needs to be done as an ISO. If you right click your ubuntu file their should be an iso option of some kind.
That isn't true with Windows 7. In 7, you can write click on an ISO file and write it to disc the same way you would in Ubuntu..

---

### Post by warfacegod on 2010-01-16
> **qamelian said:**
> That isn't true with Windows 7. In 7, you can write click on an ISO file and write it to disc the same way you would in Ubuntu..

Yes, but that creates it as an ISO file which is what the disc needs to be. Out of the box XP and Vista can't do that.

---

### Post by ssulaco on 2010-01-16
crazymf,do you have another computer you can try the image in?
Ive had real good luck with Imgburn,........burn it at the slowest possible speed.

Did you make sure your bios is set to boot from the rom drive like baddog144 suggested?

---

### Post by crazymf on 2010-01-16
Yea, I tried it on a windows 7 comp and it worked just fine. 
So far I've tried Infrarecorder, isorecorder, and the default win 7 iso burner and all three worked in this computer, but on the other one, the wiped sony, nothing works. I keep getting "NTLDLR not found, restart"
I tried loading from the HD and it took very like 2 sec for the restart screen to pop up, but when I load from the CD it takes 2-3 minutes. maybe that means something?

---

### Post by Miljet on 2010-01-16
> NTLDLR not found, restart

All the advice about which program to use to burn the disk is useless! From the above quote, it is obvious that his computer is trying to boot from the hard drive and not the CD drive. The old boot information is still on the Master Boot Record of the drive and is pointing to the NYLDR file, which isn't there anymore.

@crazymf, you still don't have your BIOS set to boot from the CD/DVD drive first. You have to move the CD drive listed in the BIOS so that it is above the hard disk drive.

---

### Post by Sef on 2010-01-16
Make sure that you set the bios to boot from the cd first as miljet said.   If it is set to boot from the cd first,  and it is not, then I would try the cd in another computer and see what happens.

---

### Post by crazymf on 2010-01-16
Yes it is. In my bios menu, under boot, I have an option for boot device priority. I go into that and i have 3 priorities. the first one is my cd/dvd drive, the second is a floppy, and the third is the HD. 
When I start it up with the cd in it, the drive makes whirring noises like its reading the cd. then it gives me the restart message


@Sef   the disk works in my other computer

---

### Post by houseworkshy on 2010-01-16
This one is way beyond me, however, I did a search for your error and found a solitary ( but mentioned twice ) solved thread for something which sounds very similar.
  
[http://forums.bit-tech.net/showthread.php?t=55167](http://forums.bit-tech.net/showthread.php?t=55167)

Because I am so far out of my depth and don't know the site, for all I know it could be malicious, please wait for an expert to ok the advice in it.  If he or she does say it is ok and it works.  Then, as you have run dban, don't forget to set the "bootable" flag after formating.

Good luck.

---

### Post by trikster_x on 2010-01-17
N/m

---

### Post by JKyleOKC on 2010-01-17
> **houseworkshy said:**
> Because I am so far out of my depth and don't know the site, for all I know it could be malicious, please wait for an expert to ok the advice in it.I don't claim to be an expert but I've been dealing with similar problems for nearly 30 years now. The actions described in that thread were all directed at solving a different problem: the machine was just beeping and not completing the POST (Power On Self Test) that's built into most BIOSes. When he replaced the graphics card, that solved the POST problem but had no effect on the NTLDR message.

He then said he reformatted the drive, and that got rid of the NTLDR message. That wouldn't be an option in this case since Windows isn't there any more.

The BIOS code is apparently trying to boot from the hard disk, which should be totally empty since you ran DBAN to wipe it -- but it seems as if the original boot code in the MBR is still there and looking for the NTLDR file.

So your current problem boils down to finding out why it's refusing to boot from the CD. When you said the CD works in another machine, did you mean that it actually booted into Ubuntu there, or simply that it was readable? If the CD fails to boot, the BIOS will try for the floppy next, and if that fails or has no disk, it will finally go for the HD -- and you would get the error message.

If it was just readable, that sounds like you may have burned a copy of the ISO file to the CD, rather than burning the actual image that the ISO file contains. On my ancient Win systems I used the Nero burning program, and it had separate menu items for the two modes of burning. Someone else will have to give you details of more modern burner programs, if this hint isn't enough for you to work it out on your own...

Hope this helps!

---

### Post by warfacegod on 2010-01-17
I just reread your first post (after having read houseworkshy's link) and I think wiping your drive is what did this. I don't know dban at all but I'm betting it left the Master Boot Record on the drive when you wiped it. If it's possible take the drive out and put it in another computer and reformat it. Doesn't really matter what filesystem you use, probably NTFS would be best. Make sure you do a full format with the long tedious wait not a quick format. Then put the drive back in the your Vaio and try your disc again.

---

### Post by baddog144 on 2010-01-17
> **Miljet said:**
> All the advice about which program to use to burn the disk is useless! From the above quote, it is obvious that his computer is trying to boot from the hard drive and not the CD drive. The old boot information is still on the Master Boot Record of the drive and is pointing to the NYLDR file, which isn't there anymore.

@crazymf, you still don't have your BIOS set to boot from the CD/DVD drive first. You have to move the CD drive listed in the BIOS so that it is above the hard disk drive.

It is possible that it's not being burnt correctly, so the BIOS doesn't recognize it as a bootable disc. But yeah, my first thoughts were definitely boot order.

---

### Post by admiralspark on 2010-01-17
In some (most?) bios's, you can hit (for ex) the Esc key and it will show a screen presenting you the different boot options. This is NOT for changing the order--it allows you to choose to boot from any connected media, regardless of what order it's in. If you have that option, try selecting CD drive from there. If you don't (or that still doesn't work), the slow, heavy reformatting is probably the way to go.

---

### Post by PRC09 on 2010-01-17
A couple of things here,the NTDLR missing means that the hard drive wasnt wiped properly.I use dban all the time and have never seen this message.When the drive is wiped properly and you try to boot from it the error is  "Error loading operating system" (looking at it right now).The other issue with the cd not booting could be it is CD-RW media.Have seen this a couple of times now especially on older drives.Works fine from cd-r but wont see a bootable iso on a cd-rw.....Hope this helps.

---

### Post by crazymf on 2010-01-17
well, I've been using a CD-RW so maybe thats the problem? 
I know for a fact that it is trying to boot from the CD first, so that isnt the problem. The CD works in my newer computer, so there isn't an error in burning it. So ill try using a CD-R.

---

### Post by audiomick on 2010-01-17
> **crazymf said:**
> well, I've been using a CD-RW so maybe thats the problem? 
I know for a fact that it is trying to boot from the CD first, so that isnt the problem. The CD works in my newer computer, so there isn't an error in burning it. So ill try using a CD-R.

Hi. Haven't run up against it myself, but I have seen _lots_ of posts saying definitely do not use a CD-RW. Also, you should burn at the slowest  possible speed.

Do a MD5sum check on the iso image before you start.

---

### Post by warfacegod on 2010-01-17
> **crazymf said:**
> well, I've been using a CD-RW so maybe thats the problem? 
I know for a fact that it is trying to boot from the CD first, so that isnt the problem. The CD works in my newer computer, so there isn't an error in burning it. So ill try using a CD-R.

Most likely your CD-ROM can't even read a CD-RW. You said it was old (relative term) and allot of old ones can't. If using a CD-R works, then you should use the entire hard drive to install. That way you are assured of eliminating dban's bad wiping job.

Frankly I'm astonished you were able to get ubuntu's iso onto an RW, they're only 650 MB.

---

### Post by Defiant Rat on 2010-01-17
> **warfacegod said:**
> Most likely your CD-ROM can't even read a CD-RW. You said it was old (relative term) and allot of old ones can't. If using a CD-R works, then you should use the entire hard drive to install. That way you are assured of eliminating dban's bad wiping job.

Frankly I'm astonished you were able to get ubuntu's iso onto an RW, they're only 650 MB.

I've used RW's to install before without a problem. If your computer cant read the cd maybe put the HDD into one that can, install ubuntu to it, then put it back in the Vaio.

---

### Post by halitech on 2010-01-17
> **warfacegod said:**
> Frankly I'm astonished you were able to get ubuntu's iso onto an RW, they're only 650 MB.

I used to think the same thing but there are 700meg rewritable cds out there

[http://www.amazon.com/Verbatim-CD-RW-Ultra-Speed-16X-24X/dp/B000B06PNK](http://www.amazon.com/Verbatim-CD-RW-Ultra-Speed-16X-24X/dp/B000B06PNK)

---

### Post by warfacegod on 2010-01-17
> **halitech said:**
> I used to think the same thing but there are 700meg rewritable cds out there

[http://www.amazon.com/Verbatim-CD-RW-Ultra-Speed-16X-24X/dp/B000B06PNK](http://www.amazon.com/Verbatim-CD-RW-Ultra-Speed-16X-24X/dp/B000B06PNK)

I haven't used RW's in years so, I guess I stand (sitting actually) corrected. But I won't take this laying down.

---

### Post by halitech on 2010-01-17
I haven't either and the only ones I have are 650 but I find with the price of cd-r its just easier to burn it to a cd-r then worry about finding a 700meg cd-rw

---

### Post by baltadt on 2010-01-17
I have had the same problem here is how to fix it. First look for a program called "killdisk". It is what the D.O.D. uses to wipe their computers. Second you have two choices. Either buy a newer cd-rom or dvd-rom for like $20 used at a computer repair store or buy a stack of cd-r disks. That should fix all your problems. Hope I helped you.

---

### Post by warfacegod on 2010-01-17
> **Defiant Rat said:**
> I've used RW's to install before without a problem. If your computer cant read the cd maybe put the HDD into one that can, install ubuntu to it, then put it back in the Vaio.

That is a possible fall back solution. A variation on my suggestion of formatting the drive in another machine. Installing in another machine might work but the install process would use drivers for the machine the drive is in not the one it will be in. That would almost certainly cause problems once it's switched back to the old machine. It's a last resort and may or may not work. In essence, it's a crap shoot.

---

### Post by freak42 on 2010-01-17
Why do people always recommend a slow burn speed? This sounds like a total myth to me?

---

### Post by warfacegod on 2010-01-17
> **freak42 said:**
> Why do people always recommend a slow burn speed? This sounds like a total myth to me?

Slower speeds drastically reduce the risk of a write error in the burn process.

---

### Post by cowboy7305 on 2010-01-17
can the disk be read by any other computer if  not its a disk problem if it can be read its a DVD problem with the machine you are trying to use

---

### Post by crazymf on 2010-01-17
PROBLEM SOLVED!

I used a CD-R burned at the slowest possible speed and that worked. I'm guessing that worked because my computer couldn't read CD-RW, so yea.

Thanks to everybody who helped me.

---

### Post by warfacegod on 2010-01-17
Glad to help. If you haven't done the install yet then I'll reiterate my post about using the entire drive to install ubuntu into. Please mark as solved.

---

