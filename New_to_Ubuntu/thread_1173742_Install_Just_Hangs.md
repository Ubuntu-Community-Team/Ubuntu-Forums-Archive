---
title: "Install Just Hangs"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Chris Green on 2009-05-30
Arghh, stuck at 1st base! I am trying to install 9.0.4 in a jaunty jackalopian kinda way, on a Dell desktop that meets the specifications laid down on the download page. Burning the image CD from iso file went well, and indeed the disk does boot, once I'd altered the BIOS to boot from CD first. 

I get past the 'choose a language screen' and the main menu, but then everything just hangs and I get two of the keyboard's lock lights flashing.

Annoyingly I read somewhere yesterday (and now can't remember where!), that there's a way past this, by altering the way the CD runs. I tried the Safe Graphics option nestled behind one of the F keys, but that gets me a little further, to a plain pinkish desktop looking like a silk curtain and a working mouse cursor, but that's as far as it goes. 

The process then hangs again.

No doubt there's an option for my problem but I didn't know what all the others were.

Any ideas?

---

### Post by kpkeerthi on 2009-05-30
Did you check the Md5 sum of the iso? How fast did you burn the ISO? Burn it at not higher than 4x. You may also want to run the Verify CD wizard from the Live CD boot menu. Another option is to try with the Alternate CD ISO.

---

### Post by Chris Green on 2009-05-30
> **kpkeerthi said:**
> Did you check the Md5 sum of the iso? How fast did you burn the ISO? Burn it at not higher than 4x. You may also want to run the Verify CD wizard from the Live CD boot menu. Another option is to try with the Alternate CD ISO.

Many thanks - I'm on the case right now. Will get back to let you know how I get on.

UPDATE: Yes, iso file passes md5 test. To be sure I wrote a new image disk running the burner really slowly, but to no avail. It still hangs with the keyboard lights flashing. When you say "run the Verify CD wizard from the Live CD boot menu" I take it you mean from the 1st menu option worded something like 'Try Ubuntu without making changes to your machine'? This also waits a while and hangs. 

I tried to download the alternative version, but being new to BitTorrent, I seem to be getting myself tied in knots with a BitTorrent telling me I've downloaded all 697mb but only showing as a 28k file at my end. I'm beginning to ask myself how badly I want Ubuntu at this stage

Do you think I might have some hardware problem? The machine is not exactly new (2ghz P4 with 384mb, running a built in Intel 82B456 graphics) but I've loaded older version of Ubuntu (Edgy Eft I think) on even older machines with no problem.

---

### Post by blueridgedog on 2009-05-30
If you are certain you have made a good disk (perhaps testing it on another system), they perhaps you can try a USB flash drive install.  The program unetbootin will let you put the ISO on a flash disk.  Can your dell boot from a flash drive?

---

### Post by NHArticleTen on 2009-05-30
two things:

first, from the beginning menu, run VERIFY CD

second, from the beginning menu, run MEMORY TEST

and for others who may be experiencing similar problems:

when you post on the forum we ASSUME you have ALREADY...

downloaded the ISO and checked it to verify the MD5 checksum...

burnt the ISO to CD on the slowest burn speed your machine offers...

and you burnt a second CD if you had ANY problems with the first...

changed your BIOS to boot from optical drive first...

you are able to get to the beginning screen...

you have VERIFIED CD...

you have MEMORY TESTED your ram...

and now that you've done all that and maybe a little web surfing for others who have already blogged/posted your problem and perhaps even solutions to it...

PLEASE, PLEASE...provide your hardware and currently-installed operating system(s) and other software...IN YOUR ORIGINAL POSTING.

Everyone thanks you in advance for your kind cooperation!

---

### Post by Chris Green on 2009-05-30
Sorry to have been so have been such a trial for you - it must be nice to know everything. Goodbye and screw Ubuntu. No wonder people PAY for Windows

---

### Post by blueridgedog on 2009-05-30
> **NHArticleTen said:**
> 
PLEASE, PLEASE...provide your hardware and currently-installed operating system(s) and other software...IN YOUR ORIGINAL POSTING.


Not a very Ubuntu post.  Are you trying to help the original poster?

---

### Post by blueridgedog on 2009-05-30
> **Chris Green said:**
> Sorry to have been so have been such a trial for you - it must be nice to know everything. Goodbye and screw Ubuntu. No wonder people PAY for Windows

NHArticleTen is as new as you and means well.  There are thousands of us here that can try and help.  Don't be discouraged because you encounter a rare Ubuntu user who got up on the wrong side of the bed today.

---

### Post by rednano12 on 2009-05-30
I had the same issue. Nothing worked, (mem check, md5 was correct, burned 3 times at 1x speeds...). At that point I downloaded the alternate iso and that worked fine. That is probably the best thing to do. ;) 

--
Ubuntu is like an algebraic function. You get a better output depending on your input.

---

### Post by acura4u on 2009-06-01
I have the same problem.  And just to validate that it's not a CD or corrupt issue, I tried both 8.10 and 9.04.  Both has the same hanging condition.  However, with 9.04, it actually got to the part where it said "Starting up Partitioner".  I think it might be related to the disk controller.  Now I've installed 9.04 on quite a few Dell laptops and desktops already.  What unique about this particular box is that it has an extra SATA controller.  I will try to remove this controller and see if it makes a difference.  My suggestion here is to check to see if you have an extra or legacy controller that it might not light or a BIOS settings that interfere with your IDE/SATA operations.

---

### Post by kpkeerthi on 2009-06-01
> **chris green said:**
> sorry to have been so have been such a trial for you - it must be nice to know everything. Goodbye and screw ubuntu. No wonder people pay for windows
:rolleyes: good bye

---

