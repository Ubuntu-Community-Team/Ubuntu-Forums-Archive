---
title: "My HUGE ISSUE (it is pretty big)"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by aperture123 on 2010-04-29
Hello, take on my issue (if you dare).
My issue involved Ubuntu 10.04. I noticed it was coming out about 4 days before, and had this briliant idea to triple boot max os x snow leopard, windows 7, and Ubuntu 10.04 to commemorate this event. Anyways, this was all going on to my acer aspire one netbook.

Suffice to say, mac came first and wouldn't install, but I did manage to format my harddrive to this mac crap stuff. So I stopped that (didn't really like macs) and went for the Windows 7 next. Put it on usb (NTFS formatted) and lo and behold, no go. Darn. So, I said forget it and went straight for UNR 10.04 (whoo!).

First time didn't even run. Then I realized maybe formatting to FAT32 might work...and it did. Yay. Then tried to install the program through and I'm right here. This issue.

I partitioned my harddrive (easily) and attempted to install ubuntu netbook remix. In then stated about 35% (?) of the way through that it couldn't install, corrupt cd/dvd/harddrive (one guess on the corrupt one). 

HOW CAN I FIX SUCH A THING!? (sorry for screaming)

The touchpad isn't working either and the update hasn't fixed. Should I wait a little longer?

Also, everything else works (somewhat) ok. Chat works, internet works (being used right now).

SO MAIN PROBLEMS:

#1. When I disconnect my power cable, my cpu basically shuts down in ubuntu. ??? even though fully charged, why is it doing this?

#2. Mac and Windows 7 are pretty much out, so ubuntu can take all the space. Why isn't it working correctly? It partitioned everything right, just says corrupt harddrive. Does this mean I need to do something else, am I missing some important thing?

#3. How can I fix touchpad? i'd like to use it SOME time...

also, on bios should i change the HCSC or something to IDE??? 

Thanks!

---

### Post by ndstate on 2010-04-29
You cant install MAC OS on just any computer.  If you want Windows and Ubuntu install windows first.  I would completely erase your computer and start over... see what happens.

---

### Post by aperture123 on 2010-04-29
> **pmp6nl said:**
> You cant install MAC OS on just any computer.  If you want Windows and Ubuntu install windows first.  I would completely erase your computer and start over... see what happens.

I tried that, so I used Gpart to do so, but JUST install Ubuntu. It wouldn't install though. Why?

---

### Post by conradin on 2010-04-29
Yep, The reason mac excels at what it does is that it doesn't have to worry about all sorts of random hardware. They Control the hardware and software development for most of their systems. While the Intel macs do support intel CPUs there is much more PC hardware they dont support. 

ANYWAyz, the linux media you downloaded probably had a check sum MD5 or something like that in which you could use to verify the media was not corrupted. 

Im guessing, this is a number of issues, and that your hardware isnt brand new. You may have a hard drive with many bad sectors its hard to tell at this point. you're telling us your installation of linux corrupted part way through, but continues to run?

In any case, I would re-download the linux media and verify that its a functional copy. Then I would boot the live option and test my hardware. Then I would write back here, and tell us all about the experiences, and figure out what to do next.

---

### Post by aperture123 on 2010-04-30
Ok, here was the issue.

When I booted to Live mode (to test out UNR 10.04), I tried to install. I just told it linux could take up all of the installer. It then came up with this error that my cd/dvd/harddrives may need to be cleaned/checked out. Since this is a netbook, there is no cd/dvd drive.

Live works fine (other than the touchepad). I need to get it intalled,  but there seems to be some hardware errors concerned. I'm using the acer aspire one.

---

### Post by P4man on 2010-04-30
Sounds like its telling you the usb stick has gone bad. do you have another stick to try?

---

### Post by aperture123 on 2010-04-30
Yes, I have another usb stick I can try, I'll try that one too, and post back regarding results.

However, my ground prong on my charger cable broke so....hopefully I can either repair it (wedge in there kinda) or replace it (1.99 I think, rewire some stuff), it may be awhile.

---

### Post by aperture123 on 2010-04-30
erm, apparently my ground prong isn't 'required', so I seem to be fine without it. Just don't expect me to go in the rain anytime soon.

Anyways, here is the specific error (got a new usb for it)

"The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."

Perhaps it is because on the bios I changed some stuff????
what else could it be? (stopped at 40%)
oh, by the way, that touchpad thing was an error I caused on accident the first time. never happened again :P


EDIT: Changed my bios SATA from ADHI (i think?) to IDE (sorry if I made these spelled incorrectly). However, this seemed to have nothing to do with it as when I tried installing again there was still an error, at 40% again. I saw something about keeping it cool, so I assume that is the main harddrive or usb? I got a tiny fan to see if I can cool the acer down a little bit, but how do I fix this issue?

Thanks.

---

### Post by P4man on 2010-05-01
to quote myself > **P4man said:**
> Sounds like its telling you the usb stick has gone bad. do you have another stick to try?

---

### Post by aperture123 on 2010-05-01
P4Man,
         
          I've tried a different usb stick, but the issue is it just isn't working. Both sticks were in FAT32 when written over. Is it maybe where I put the usb on the computer that might be affecting the computer? Or perhaps that I need to format them to a different type?

Or am I going to have to buy a third usb stick?

---

### Post by P4man on 2010-05-01
First make sure your downloaded iso is not corrupted:
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Then what do you use to make the USB stick? I would recommend:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Lastly, when you boot from the usb stick, you should get a purple screen with a keyboard icon before getting to the language screen. press escape or space when see that icon. You will get a screen with options. Run the "cd/dvd" verification (not sure how its called). That will ensure your usb stick has no errors on it.

---

### Post by mechro on 2010-05-01
Probably a dumb question, but how did you put Ubuntu on the USB stick? Perhaps it was from a bad burn LiveCd?

---

### Post by aperture123 on 2010-05-01
*sigh*

I used UnetBootin to write it to cd.
Ran the Md5checksum.
looks like I'm redownloading ubuntu 10.04 netbook remix....

---

### Post by aperture123 on 2010-05-02
Welp, downloaded the UNR again (this time from America since the servers allowed me to) and it installed perfectly. I've had no problems thus far with it, and my friend is now getting it too:P!

Anyways, thank you everyone for all your help. You're awesome!

---

### Post by sadaruwan12 on 2010-05-02
Mention not we're here to help, And Bro welcome to the change.

Also like give some advice to you when you down load a ISO file it may be Ubuntu or something else do a verification using MD5 code it'll save you from lot of trouble. I think you've learned it the hard way 'cos normally Ubuntu LTS's give very little trouble.

And please mark this thread as solved you can do that through the post setting when you go to edit it.

Also Bro it seems like you're new to all this Ubuntu thing so now you're using the all new 10.04 could you give us small feed back how pleasant or worse is your experience is through that we could improve more.

Thank you and welcome again to the change. ;-)

---

### Post by conradin on 2010-05-03
I hate to suggest some thing like this, Its what I would do but not neccisarly the best idea for everyone. 

I would remove the netbook hard drive and install via a live cd in another computer. Im suspicious of your usb bus and or other hardware. 
If you do it this way you can avoid whatever unknown possibly hardware issue you are currently having execept for the event your hard drive is faulty somehow.

Again, if youre netbook is under warenty, or you dont feel comfortable taking your computer appart, this advice is not for you.

---

### Post by P4man on 2010-05-03
> **conradin said:**
> I hate to suggest some thing like this, Its what I would do but not neccisarly the best idea for everyone. .

Maybe next time you can read more than just the first post before replying, as the issue was solved by downloading a non corrupted iso ;)

---

### Post by Bjalf on 2010-05-03
> **sadaruwan12 said:**
> Also like give some advice to you when you down load a ISO file it may be Ubuntu or something else do a verification using MD5 code it'll save you from lot of trouble. I think you've learned it the hard way 'cos normally Ubuntu LTS's give very little trouble.

It is in cases like this that bittorrent shines. It automatically checksums the file, and if you already have a questionable image, bittorrent can check it and re-download just the corrupt bits.

And it eases the strain on the servers.



> **conradin said:**
> I would remove the netbook hard drive and install via a live cd in another computer.

But the installation would then detect the wrong hardware.

---

