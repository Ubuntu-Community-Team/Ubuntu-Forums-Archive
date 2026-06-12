---
title: "Problem upgrading from 8.04 LTS to 10.04 LTS"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by clayy93 on 2010-07-14
I'm posting this in Absolute Beginner Talk because I am an absolute beginner so to speak when it comes to really using anything other than Windows and I'm not really too knowledgeable when it comes to Windows either. I've been using my computer with 8.04 LTS for a while now mainly just to use the internet. Last night I tried to upgrade to 10.04 LTS. I followed the directions I was given somewhere on the Ubuntu website about going to the update manager and checking for updates, updating them, then checking again and clicking upgrade. Eventually, after waiting a few hours, it was done and I was asked to restart my computer. When I did, my computer froze on this black screen with a bunch of stuff I didn't understand such as stuff like 

[  6.247554]  [<c01034c8>] work_notifysig+0x13/0x1b

which is the very last line on this big wall of text showing up. there are a few similar looking lines all in a row above this one, with some different stuff at the top. 

After getting similar looking things after restarting a few times, I thought maybe the upgrade didn't work right and I went on my other computer and burned an ISO file with Ubuntu 10.04 LTS using InfraRecorder to a blank DVD-R. I put the disk in the computer and restarted it and while it was starting up I saw a purple screen come up and I hit enter which brought me to the menu I've been expecting all along, which is the one asking if I want to Install Ubuntu, Check Disk for Defects, etc. I selected Install and then chose English for my language. Just a second later the screen went black again and spit up that big wall of text I didn't understand. I left it there for a while hoping it would do something but no luck. I tried this a few more times and still not getting anywhere. 

I already made sure in the BIOS menu thing that it's booting from the CD drive first. If anybody has anything to help me get my computer working again it would be really appreciated. 

My computer is an HP Pavilion a814x

I don't know what other information is needed to help me out here.

---

### Post by NoBugs! on 2010-07-14
Have you tried the 'check disk for defects' option? Maybe the disk is bad? There are other options in that first menu, like safe graphics mode, that may help.

---

### Post by clayy93 on 2010-07-14
After trying to check disk for defects it went to the black screen with the text again. 


And I didn't see any Safe Graphics Mode.
I only see Try Ubuntu without installing, Install ubuntu, Check disc for defects, test memory, and boot from hard disk.

---

### Post by clayy93 on 2010-07-14
I also just notices that my caps lock and scroll lock lights on my keyboard are blinking whenever I get to the  black screen with the text.
The text also changes sometimes too. The last line right now after trying Install Ubuntu again is
[    3.917356]  [<c058b983>] error_code+0x73/0x80

---

### Post by philinux on 2010-07-14
> **clayy93 said:**
> I also just notices that my caps lock and scroll lock lights on my keyboard are blinking whenever I get to the  black screen with the text.
The text also changes sometimes too. The last line right now after trying Install Ubuntu again is
[    3.917356]  [<c058b983>] error_code+0x73/0x80

have you got home on it's own partition and more importantly backups.

---

### Post by clayy93 on 2010-07-14
Back ups of what? And I don't think home is on its own partition.

---

### Post by philinux on 2010-07-14
> **clayy93 said:**
> Back ups of what? And I don't think home is on its own partition.

Backups of important stuff. I've had trouble with upgrades.

---

### Post by clayy93 on 2010-07-14
I don't have much important stuff other than music and a buttload of PDF versions of books, but I copied all of that stuff to an external harddrive.

---

### Post by bodhi.zazen on 2010-07-14
First, that is not how to upgrade, that will re-install Ubuntu.

To upgrade, use update-manager :

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

The second step is to check the integrity of the iso and the burn on of the CD.

Assuming the CD is OK, it sounds as if X (the graphical interface) failed. In that event you may need to install from the alternate CD and we need to know what video card you are using (nvidia ? ATI ? )

---

### Post by clayy93 on 2010-07-14
that's how I tried to upgrade in the first place is through update manager, following the instructions in the link. 
How do I check the integrity of the iso?
and I don't know what my graphics card is.

---

### Post by Zill on 2010-07-14
> **clayy93 said:**
> ...I only see Try Ubuntu without installing, Install ubuntu, Check disc for defects, test memory, and boot from hard disk.
Rather than installing I would first try to run Ubuntu directly from the Live CD.

This means that you boot up with your CD in the drive, then select the "Try Ubuntu without installing" option.  This should then boot Ubuntu as a "live" session.

If this runs correctly you should have an icon on the live desktop allowing you to install the new system if you wish.

The advantage of this method is that it proves your CD is OK, as well as giving you an opportunity to have a look around the new version before you actually install it.  It also demonstrates that your hardware is basically compatible, although you *may* need to install additional graphics/wireless drivers etc following installation to get the best results.

---

### Post by bodhi.zazen on 2010-07-14
> **clayy93 said:**
> that's how I tried to upgrade in the first place is through update manager, following the instructions in the link. 
How do I check the integrity of the iso?
and I don't know what my graphics card is.

These links review the process :

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)


> **Zill said:**
> Rather than installing I would first try to run Ubuntu directly from the Live CD.

This means that you boot up with your CD in the drive, then select the "Try Ubuntu without installing" option.  This should then boot Ubuntu as a "live" session.

If this runs correctly you should have an icon on the live desktop allowing you to install the new system if you wish.

The advantage of this method is that it proves your CD is OK, as well as giving you an opportunity to have a look around the new version before you actually install it.  It also demonstrates that your hardware is basically compatible, although you *may* need to install additional graphics/wireless drivers etc following installation to get the best results.

If you read up, his live CD fails.

---

### Post by Zill on 2010-07-15
> **bodhi.zazen said:**
> ...If you read up, his live CD fails.
The OP originally said "...I selected Install and then chose English for my language. Just a second later the screen went black again and spit up that big wall of text I didn't understand..." so I take this to mean that the CD was *not* run as a live session.

However, I agree that the CD is suspect and so should be thoroughly verified before use.  My suggestion of running the live CD was to give additional confidence in the CD *before* starting installation.

---

### Post by gj_clt on 2010-07-15
My solution to a similar upgrade problem was to use Gparted, reformat disk and start again with a freshly downloaded and checked CD.

---

### Post by bodhi.zazen on 2010-07-15
> **Zill said:**
> The OP originally said "...I selected Install and then chose English for my language. Just a second later the screen went black again and spit up that big wall of text I didn't understand..." so I take this to mean that the CD was *not* run as a live session.


LOL , I think most people expect the Desktop CD to boot to a graphical desktop. IMO failure to start a graphical session / black screen with wall of text == failure. The OP clearly booted the CD, and not the hard drive, and was clearly met with failure, again IMO.

The question is is this a bad burn or is this a hardware / videocard issue.

---

### Post by clayy93 on 2010-07-15
I think it might be something wrong with the hardware because I tried to burn the iso to three different disks. 
Unless maybe there was something wrong with the original download, I guess it is probably a hardware problem.

---

### Post by bodhi.zazen on 2010-07-15
> **clayy93 said:**
> I think it might be something wrong with the hardware because I tried to burn the iso to three different disks. 
Unless maybe there was something wrong with the original download, I guess it is probably a hardware problem.

Well, do an md5sum on the downloaded iso.

It it is OK, try a different CD burning program (k3b) and/or burn at the lowest possible speed (1x rather then 4-24x).

---

### Post by clayy93 on 2010-07-16
I did the md5sum thing and the iso is alright.
I burned using a new program, ImgBurn at 1x speed.
Still nothing.
I don't even care about upgrading anymore, I just need my computer to work again.

---

### Post by Zill on 2010-07-16
> **clayy93 said:**
> ...Still nothing...
"nothing" is not very descriptive!  Please advise *exactly* what you see after booting up with the CD in the drive and selecting the "Try Ubuntu without installing" option.

---

### Post by clayy93 on 2010-07-16
with the Try Ubuntu without installing, I get the black screen with text again 2 sec. later.
the following is EVERYTHING on my screen after I start up my computer and try to Try Ubuntu without installing.


[   3.922549] Kernel panic - not syncing: Attempted to kill init!
[   3.922614] Pid : 1, comm: init Tainted: G         D      2.6.32-21-generic #32-Ubuntu
[.  3.922694] Call Trace:
[.  3.922760]  [<c0588f42>] ? printk+0x1d/0x23
[.  3.922821]  [<c0588e7a>] panic+0x48/0xf3
[.  3.922883]  [<c014ec0d>] forget_original_parent+0x2bd/0x2c0
[.  3.922946]  [<c014ec23>] exit_notify+0x13/0xf3
[.  3.923007]  [<c0150531>] do_exit+0x13/0x170
[.  3.923068]  [<c058c4b5>] oops_end+0x95/0xd0
[.  3.923129]  [<c012b41c>] no_context+0xbc/0xe0
[.  3.923191]  [<c012b47c>] __bad_area_nosemaphore+0x3c/0x160
[.  3.923255]  [<c01cef67>] ? get_page_from_freelist+0x147/0x360
[.  3.923319]  [<c012b5b7>] bad_area_nosemaphore+0x17/0x20
[.  3.923381]  [<c058dc76>] do_page_fault+0x2f6/0x3a0
[.  3.923443]  [<c058d980>] ? do_page_fault+0x0/0x20
[.  3.923505]  [<c059b983>] error_code+0x73/0x80
[.  3.923566]  [<c01e5695>] ? do_wp_page+0x1f5/0x820
[.  3.923628]  [<c01304cc>]  ? kmap_atomic_prot+0x4c/0xf0
[.  3.923690]  [<c01e641c>] handle_mm_fault+0x2fc/0x390
[.  3.923758]  [<c058da8d>] do_page_fault+0x10d/0x3a0
[.  3.923820]  [<c058d980>] ? do_page_fault+0x0/0x3a0
[.  3.923882]  [<c058b983>] error_code+0x73/0x80

---

### Post by Zill on 2010-07-16
clayy93:  Thanks for the info.  In order to establish if your 10.04 CD/DVD is good it would be helpful to try it in a different PC.  Just make sure the BIOS is set to boot the PC from the CD first and then select "Try Ubuntu without installing" as previously - it should not change anything on the HDD.

One more question: please advise if you needed any special parameters to previously install Ubuntu 8.04 or was this a standard "default" install.

If you still have your 8.04 disk then you should be able to boot this as a Live CD - if this still works then (hopefully!) your hardware is OK.  If you no longer have the disk then you could, of course, [download 8.04 again]("http://releases.ubuntu.com/8.04/").

---

### Post by clayy93 on 2010-07-16
I don't think there were any special parameters when I downloaded 8.04. I ordered the disk from the website and just followed the on-screen instructions when I put the disk in. 
I still have the disk for it.
It looks like the 10.04 disk is working in my other computer. 
The 8.04 disk works!!! At least it seems that way so far!!
Thanks for the help.
But I'm still curious as to what the problem could have been as to why I couldn't get 10.04.

---

### Post by clayy93 on 2010-07-16
Nevermind. At about 46 percent through installing 8.04, an error came up.

Failed to copy files; faulty CD/DVD or hard disk?


The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

I cleaned the cd, and I have kept a fan near my computer to make sure it's cool.  
 I don't think the disk drive is faulty because I have two trays to put the disk on and switching to the other one didn't change the results here. 
So it seems like I either need a new hard disk or a lens cleaner. Right? 

Where do I get a hard disk, what kind and for how much?

---

### Post by Zill on 2010-07-16
clayy93:  I am not convinced that your HDD is at fault in this case as, when you are running the Live CD rather than installing the OS, the HDD is not needed.  As your 10.04 disk runs on one PC but does not on the other, it looks to me like the DVD drive, rather than the HDD, is on the way out.  However, it is puzzling that you are getting the same problem with two DVD drives on one PC. :confused:

All I can suggest is that you do extensive testing with both the 8.04 and 10.04 live CDs to try to establish if a DVD drive fails.  I do not believe it is worth trying to install either OS until the CD/DVDs can be read reliably.

If you do need new hardware then a quick Google comes up with [this info]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00375932") for the HP Pavilion a814x.  It seems that the standard HDD is 160 GB SATA - 7200 rpm but I suggest you could upgrade the spec if you like.  Just take a look online and buy a drive from the supplier of your choice!

Just a final thought... You could try burning a CD, rather than a DVD, with the 10.04 ISO.  If the DVD drive *is* struggling then it may be easier for it to read CDs. ;-)

---

### Post by clayy93 on 2010-07-17
Isn't it possible to burn it onto a flash drive? If so my friend has one I could borrow.
I figure if I do that I can know really what the problem is. If it works then my disk drive I know is the problem, otherwise it really is the hard disk.

---

### Post by waynefoutz on 2010-07-17
> **clayy93 said:**
> Isn't it possible to burn it onto a flash drive? If so my friend has one I could borrow.
I figure if I do that I can know really what the problem is. If it works then my disk drive I know is the problem, otherwise it really is the hard disk.

yes it is, Unetbootin is an easy way to put a live cd on a USB stick or flash drive. I prefer installing this way, it's a LOT faster. 

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by Puzzled Guy on 2010-07-17
I don't know about you, but some people prefer to do a fresh install.

I can't say much else since this is just my second install of Ubuntu
Jaunty -> Lucid

---

### Post by Zill on 2010-07-17
> **Puzzled Guy said:**
> I don't know about you, but some people prefer to do a fresh install...
If you read the thread from the beginning you will see that this is basically what we are trying to achieve now.  The problem is getting the PC to read and/or install the new OS from the DVD.

---

### Post by clayy93 on 2010-07-18
I tried to boot from the USB after burning 10.04 to it.
My computer started up and then took me to a menu I haven't seen yet, just a variation of what should come up if I were using a CD. It had most of the same options, Try Ubuntu from this USB, Install Ubunutu, and things like that. Well anyways this list only popped up for a second and then went to a black screen that said it was loading something with a dotted line getting longer until it reached the end of the screen then started loading something else on the second, then the third, etc. for a few more lines, then it went to a bunch of really fast scrolling text ending up at the same exact thing I got before with the error codes and the thing about init kernels or whatever at the top. 

Does this mean I need a new hard disk?

If I do need a new one, would this one work: 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075)

or is there a better one I should get for around the same price (or cheaper)

---

### Post by gj_clt on 2010-07-18
Reading the newegg review about the disk you are looking at the reviewer mentions changing SATA the cables. I had a problem like yours with a dvd drive and that was the answer - change the cable.

---

### Post by Zill on 2010-07-18
> **clayy93 said:**
> ...Does this mean I need a new hard disk?...
If you had chosen the "Try Ubuntu from this USB" option then I still do not believe your hard disk is the problem.  AIUI, this does not access the HDD at all unless you mount it later to have access to your data.  As the OS *appears* to crash before it has fully loaded then I cannot see how the HDD is the cause.

Of course, if you went straight for the "Install Ubuntu" option then yes, you *may* well have a bad HDD.  If this is the case then the unit you suggested looks fine to me.  Others may disagree but to me HDDs are basically interchangeable unless you are really looking to tweak the performance.  If you want to check things just take a peek at your HDD model number then look up the drive spec on Google, making sure the physical size is the same!.  Regarding prices, I live in the UK so the deals I can find will be different to yours.  Just shop around!

Caveat:  I have never done a USB install as CDs *always* work for me. ;-)

---

### Post by clayy93 on 2010-07-20
with the USB attempt, I did try without installing first.

also I've been running 8.04 for the past couple of days off of the disk without installing, since it still won't let me do that. I haven't had any real problems but I just want a working computer again.

If I should change the SATA cable or whatever, what kind should I get?

I need to have this computer working again soon so please somebody just give me a little help here.

---

### Post by Zill on 2010-07-20
clayy93:  Using USB, CD or DVD you *should* be able to run both 8.04 and 10.04 as "live" versions, ie. without installing to the HDD.  If you cannot do this then either your download and/or burn is bad or the PC has a hardware fault.  While there is an outside chance that a failed HDD *may* be able to spike the PC in such way that the live OS will not run properly, IMHO this is very unlikely as the HDD is not really accessed in live CD mode.

I suggest you burn new CDs (not DVDs!) for both 8.04 and 10.04, making sure the MD5 sums and disk burns are verified.  Then do repeated tests running the live CDs (without installing the OS) and see if the CDs perform faultlessly.  If so then you could proceed with installation to the HDD, first of 8.04 and then 10.04, and see how that goes.

If the PC fails the live CD tests then you may have a motherboard or RAM fault.  However, if the live CD tests are OK and only installation to the HDD fails then it looks like HDD failure.  The SATA cables *could* be the problem but it is quite unlikely IMHO as a serial cable is a very simple item.  These cables are standard parts that are cheap and easy to find.

---

