---
title: "64bit hell"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by savafan on 2010-03-01
I've had my share of issues with a new 64bit system & getting things to work correctly. I continue to run into problems when it comes to the 64 version of Ubuntu.

My question is; Can I just install the 32bit version on a system that is designed to carry the 64bit version? I have the 32 installed on an older computer & it works wonderfully. I hope to be able to get things running as smoothly on the new system.

---

### Post by philinux on 2010-03-01
> **savafan said:**
> 

My question is; Can I just install the 32bit version on a system that is designed to carry the 64bit version? I have the 32 installed on an older computer & it works wonderfully. I hope to be able to get things running as smoothly on the new system.

Yes.

What problems, got no issues here.

---

### Post by achase79 on 2010-03-01
I recently got a 64 bit system and am running 9.10 without any problems after having multiple 32 bit systems

---

### Post by skymera on 2010-03-01
> **savafan said:**
> I've had my share of issues with a new 64bit system & getting things to work correctly. I continue to run into problems when it comes to the 64 version of Ubuntu.

My question is; Can I just install the 32bit version on a system that is designed to carry the 64bit version? I have the 32 installed on an older computer & it works wonderfully. I hope to be able to get things running as smoothly on the new system.

What problems exactly?

---

### Post by qyot27 on 2010-03-01
64-bit (AMD64 or EM64T) acts as an extension of 32-bit (x86), so if you install a 32-bit OS on the system it will only use the 32-bit portions of the standard, and will have all the regular limitations of a 32-bit system (RAM limits and all).  If the '64-bit' you're referring to is IA64 (i.e., the Itanium family of processors) and not AMD64, then there's a problem, as the two are not compatible.

That said, 64-bit versions of Ubuntu ship as multilib (right?), so you would be perfectly able to install 32-bit applications on the 64-bit version and not have problems.  I'm not sure how to explicitly specify that when working from the repositories, however.

---

### Post by savafan on 2010-03-01
I've had Flash issues & driver issues for running two screens. It seemed that the entire install did not go as smoothly as it did on the older system & ultimately have now gotten the dreaded "black screen"...I have no idea how to recover my graphics. The system is there, I just can't see it.

---

### Post by uRock on 2010-03-01
I have been running the 64bit of Hardy, Jaunty, Karmic, and Lucid with no problems. You can run the 32bit on a 64bit machine with no problems. It may even run better that way. Let us know if you prefer to fix the 64bit problems.

---

### Post by skymera on 2010-03-01
> **qyot27 said:**
> That said, 64-bit versions of Ubuntu ship as multilib (right?), so you would be perfectly able to install 32-bit applications on the 64-bit version and not have problems.  I'm not sure how to explicitly specify that when working from the repositories, however.

Correct.
ia-32libs can be installed so 32bit programs can run.

---

### Post by savafan on 2010-03-01
AMD 64 is what I have

---

### Post by uRock on 2010-03-01
> **qyot27 said:**
> That said, 64-bit versions of Ubuntu ship as multilib (right?), so you would be perfectly able to install 32-bit applications on the 64-bit version and not have problems.  I'm not sure how to explicitly specify that when working from the repositories, however.

I have tried to install 32bit programs on my 64bit OS and each time it failed. May not be the case for all though.

---

### Post by savafan on 2010-03-01
I would very much like to fix what I have but cannot access the system to do so. I've tried the recover mode & still have a black screen

---

### Post by oldos2er on 2010-03-01
OP: Are you using 64-bit flash? I've found it to be more stable than 32-bit flash on a 64-bit system.

---

### Post by philinux on 2010-03-01
> **savafan said:**
> I would very much like to fix what I have but cannot access the system to do so. I've tried the recover mode & still have a black screen

Can you get to a command prompt in recovery mode. If so you could put xorg.conf aside and then try rebooting. This has the effect of making the system use the vesa driver.

at the command prompt

```
cd /etc/X11

then

mv xorg.conf xorg.conf.back
```

You can reverse this if situation remains unchanged.

---

### Post by savafan on 2010-03-01
> **philinux said:**
> Can you get to a command prompt in recovery mode. If so you could put xorg.conf aside and then try rebooting. This has the effect of making the system use the vesa driver.

at the command prompt

```
cd /etc/X11

then

mv xorg.conf xorg.conf.back
```You can reverse this if situation remains unchanged.

I can get to a command prompt in recovery & tried both of those commands.

"No such file or directory" on either of them

---

### Post by philinux on 2010-03-01
Thats a capital X it is case sensitive.

---

### Post by savafan on 2010-03-01
"cannot move xorg.conf to xorg.conf.back" Permission denied

---

### Post by undecim on 2010-03-01
> **savafan said:**
> "cannot move xorg.conf to xorg.conf.back" Permission denied

put "sudo" in front of the command.
```
sudo mv xorg.conf xorg.conf.back
```

---

### Post by theozzlives on 2010-03-01
... and nobody bothers to ask what kind of video card the OP has?

---

### Post by philinux on 2010-03-01
> **theozzlives said:**
> ... and nobody bothers to ask what kind of video card the OP has?

We can sort the other bits out when he can login to a desktop instead of getting a black screen.

---

### Post by cariboo on 2010-03-01
And the other question should be, how did you install flash and the video drivers?

---

### Post by oldos2er on 2010-03-01
> **iRock said:**
> I have tried to install 32bit programs on my 64bit OS and each time it failed. May not be the case for all though.

Make sure you have ia32-libs installed. You can try getlibs ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)) also.

I use **sudo dpkg -i --force-architecture package.deb** which has worked in every case but one, on the very rare occasion when I need 32-bit software.

---

### Post by theozzlives on 2010-03-01
> **philinux said:**
> We can sort the other bits out when he can login to a desktop instead of getting a black screen.

If it's nVIDIA, he might be able to download the drivers and install them via CLI. That would get him back to the desktop. I know on my onboard nVIDIA I had to do that until I installed the server software.

---

### Post by savafan on 2010-03-01
> **undecim said:**
> put "sudo" in front of the command.
```
sudo mv xorg.conf xorg.conf.back
```

Same result..."No such File or Directory"

BTW..Video card is Nvidia. { NVIDIA GeForce 9500 GT} I'll provide more info there once I can get back to the OS

---

### Post by QIII on 2010-03-01
Which version of Ubuntu have you installed?
 
 xorg.conf does not exist any longer by default.  Xorg is generally smart enough to probe your system and detect components in a simple configuration.  So if you are trying to move or copy xorg.conf and it does not exist, you will get the messages you are getting.
 
 It will use the file if it exists, however.  So drivers and setup utilities are still able to make custom entries (and you can still do it yourself by creating an xorg.conf).

That said, it is difficult to make a diagnosis when the best we have is "ultimately this or that happened."

Could you reconstruct the steps that lead to the failure for us?

Was it running (good or bad) well enough for you to see your desktop at some point?

What did you do thereafter?

---

### Post by savafan on 2010-03-01
See this post first & it may help explain. I have version 9.10 installed
[http://ubuntuforums.org/showthread.php?t=1417921](http://ubuntuforums.org/showthread.php?t=1417921)

I was in the process of updating my Nvidia driver when this happened. As far as how the system was performing, there seemed to be some bugs that I was working on fixing at the time but I could see the desktop.

---

### Post by QIII on 2010-03-01
Do you remember what sort of errors you were getting during the installation?

PS --  I graduated from MSU - Billings a long, long time ago when it was still called Eastern Montana College...

---

### Post by savafan on 2010-03-01
I'm afraid I do not. They did seem minor according to the person walking me through the first steps, but I do not recall seeing anything like that when I installed the 32bit version on my old system.

The install was less than 48 hours old & I have nothing to lose by trying a re-install if necessary.

---

### Post by QIII on 2010-03-02
If you use the LiveCD ("Try Ubuntu without changes to your computer") option, how does it behave?

---

### Post by savafan on 2010-03-02
I did try that option. My machine would not reboot as it should & upon trying a manual reboot, it simply goes to my option screen on to choose which OS I want to use.

I decided to try a complete re-install & have had no luck with that either....The OS is still there, & I still cannot see it..

Please keep in mind that I am a complete idiot when it comes to this very new system. I do not yet understand any of the language or commands beyond the general set up.. Some of that was confusing to me also.

I'm willing to bet that it is something simple that pertains to my video card drivers. I just haven't found the answer yet.

---

### Post by uRock on 2010-03-02
If the LiveCD won't boot, then that version will not work. I'd recommend installing the 32bit version. The only pro to using 64bit is being able to utilize more than 4 gigs of RAM. I have ran both on my 64 bit system and 32bit was just as fast as 64bit.

---

### Post by Enigmapond on 2010-03-02
Please can someone walk this gentleman through a proper re-installation over XP 64bit?. I have helped all I can...he is a dear friend of mine..:) Your help would be most appreciated.

Cheers! :p

---

### Post by RMZindorf on 2010-03-02
I had issues running Ubuntu Server Edition on my 64bit Desktop. However, when I tried again about a week later it worked. I didn't change anything on my PC or the way I set up Ubuntu, so I couldn't tell you what issues I had fixed. What are you running into? No screen display? Mouse/Keyboard issues?

---

### Post by savafan on 2010-03-02
no screen display. All was fine till I updated my video driver...That is when I lost my display upon reboot

---

### Post by uRock on 2010-03-02
What graphics card do you have? This may help decide if a different version will be better.

---

### Post by savafan on 2010-03-02
NVIDIA GeForce 9500 GT. 

I'm using two screens & was trying to configure them correctly when this problem occured

---

### Post by uRock on 2010-03-02
That is odd that the nvidia driver isn't working right. Did you do all of the updates first? Doing the updates first may help with kernel changes that would effect the driver.

---

### Post by Enigmapond on 2010-03-02
If he can't get past GRUB, is there a way to bypass GRUB to get in and try to fix things? is there a command he can give in the recovery terminal that will rollback any changes made??

---

### Post by savafan on 2010-03-02
I'd be more than happy to just wipe the entire thing & start over if I knew how. I think I've tried every way possible to re-install this with no luck. I thought that would be my best option considering I cannot seem to get my drivers re-installed properly on the video card, but it seems it wont let me do a re-install either.

I'm not giving up. If I don't have this figured out by tomorrow evening, I'll call my Tech & see if he can get it figured out. He doesn't know a lot about Ubuntu, but he can get into the Bios screen & see if things are properly set there. I'll have him wipe the entire HD if I have to.

---

### Post by uRock on 2010-03-02
> **Enigmapond said:**
> If he can't get past GRUB, is there a way to bypass GRUB to get in and try to fix things? is there a command he can give in the recovery terminal that will rollback any changes made??

That is beyond my skill level.

  I would suggest making a new thread and titling it with the GPU in the title. Then give as much detail as possible as to what happened and how it happened along with which version of Ubuntu (ie Hardy, Jaunty, or Karmic) and a list of hardware the machine has, so that some of the more knowledgeable people may notice it and be able to help.

I apologize for not being of much help on this.

---

### Post by QIII on 2010-03-02
OK.  Let's get back to the LiveCD not running.

If you put the LiveCD in the tray, close it, turn off the machine and then restart it, it won't run in LiveCD mode?

(Sorry.  I don't mean to be condescending.  I hope you realize that!)

Essentially, it doesn't seem to detect that there is a CD in the tray?

---

### Post by QIII on 2010-03-02
> **iRock said:**
> If the LiveCD won't boot, then that version will not work.

Not necessarily true, and a terrible conclusion to jump to without diagnosis.  He apparently had it running at one time, albeit with errors.

"It doesn't work so it won't work" is a non sequitur.

---

### Post by Enigmapond on 2010-03-02
> **QIII said:**
> OK.  Let's get back to the LiveCD not running.

If you put the LiveCD in the tray, close it, turn off the machine and then restart it, it won't run in LiveCD mode?

(Sorry.  I don't mean to be condescending.  I hope you realize that!)

Essentially, it doesn't seem to detect that there is a CD in the tray?

No that's not the issue, sorry to interject but I've been working with him on this for days via YM...:)

What he did, and savafan, correct me if I'm wrong, was to insert the cd whilst the computer was running Windows XP. He then chose the try option at which point it restarted but didn't go to the live cd options but to his regular booting options and yes..as far as I know the computer bios is set to boot from CD first...

Now if I've totally thrown this into orbit..let me know, I'll shut up...LOL

Cheers!:P

---

### Post by steveneddy on 2010-03-02
> **savafan said:**
> I've had my share of issues with a new 64bit system & getting things to work correctly. I continue to run into problems when it comes to the 64 version of Ubuntu.

My question is; Can I just install the 32bit version on a system that is designed to carry the 64bit version? I have the 32 installed on an older computer & it works wonderfully. I hope to be able to get things running as smoothly on the new system.

Although I didn't read the thread, only the opening post, I would say that:

1. yes - you can run 32 bit OS on 64 bit hardware

2. I've been on 64 bit since Edgy and have had no issues. 

3. I suppose I should now read the rest of the thread.

---

### Post by steveneddy on 2010-03-02
My suggestion now that I HAVE read the thread is to totally reinstall.

Put the CD in the drive and reboot the PC.

You did partition the drive and you now are dual booting, correct?

Or did you use Wubi? 

Advice: Don't use Wubi - download VirtualBox for Windows and install Ubuntu on VirtualBox if you can't or don't want to dual boot.

OK - there's my .02

---

### Post by savafan on 2010-03-02
OK...I have tried to do a complete re-install. I put the cd in the tray & restart...Nothing happens...My regular boot menu comes up & it's like the cd is not even there as QIII pointed out. I've also tried this by using the option to boot directly from the cd..This does not work either.

---

### Post by steveneddy on 2010-03-02
> **savafan said:**
> OK...I have tried to do a complete re-install. I put the cd in the tray & restart...Nothing happens...My regular boot menu comes up & it's like the cd is not even there as QIII pointed out. I've also tried this by using the option to boot directly from the cd..This does not work either.

Was it a dual boot or wubi install the first time?

---

### Post by savafan on 2010-03-02
I didn't set it up, so I'm not entirely sure, but I know nothing about wubi. It is pretty much a dual boot. I have the option to run Ubuntu or XP 64 when I start the machine. The drive is partitioned for Ubuntu to have 400GB, & windows has 100gb. First option & default is Ubuntu.

---

### Post by sandyd on 2010-03-02
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
you were missing the "/etc/X11/" in front when you ran the command.

---

### Post by Enigmapond on 2010-03-02
Ooh..where I thought the above comment was random..LOL I see where it was posted and yes you should try this in the recovery terminal...

---

### Post by savafan on 2010-03-02
"no such file or directory"

---

### Post by uRock on 2010-03-02
> **QIII said:**
> Not necessarily true, and a terrible conclusion to jump to without diagnosis.  He apparently had it running at one time, albeit with errors.

"It doesn't work so it won't work" is a non sequitur.
If a LiveCD doesn't work I my system, I move on to the one that does.

---

### Post by sandyd on 2010-03-02
wha?
theirs no xorg.conf and the xserver is STILL showing a blank screen?
thats a new one.....

---

### Post by QIII on 2010-03-02
OK.  CD not detected at startup.

Three possibilities come directly to mind:

1.  BIOS setup.  But you say you've already checked that.

2.  Hardware problem with drive.

3.  Bad burn of ISO.

Since you can make as many perfect copies as you want of Ubuntu and it will not work if the drive is defective, let's eliminate hardware first.

What happens if you put an XP installation disk (or any bootable media) into the drive and start the machine?  (Be sure NOT to click anything that says "install".  That is not the point right now.  We are checking to see that bootable media will boot.)

---

### Post by QIII on 2010-03-02
> **iRock said:**
> Thanks for the attack. If a LiveCD doesn't work I my system, I move on to the one that does.

No attack.  Observation only.

---

### Post by uRock on 2010-03-02
> **carlee said:**
> wha?
theirs no xorg.conf and the xserver is STILL showing a blank screen?
thats a new one.....

That is odd. Is their any way to use a LiveCD and add that file, once he can get a live image to boot?

---

### Post by sandyd on 2010-03-02
> **iRock said:**
> That is odd. Is their any way to use a LiveCD and add that file, once he can get a live image to boot?
ubuntu 9.10 does not need a xorg.conf.

in fact, by default, it doesnt have one.
which is why im thinking something that either
1. something in xorg/xserver is broken.
2. hardware faliure (very unlikely though, but thats the only thing i can come up with at this time)

---

### Post by QIII on 2010-03-02
Carlee --

(Nice tutorial on Flash, by the way).

I agree with your possibilities, but think that hardware failure may not be too far off the mark.

If we can get him running again, it would probably be good to take a look at the performance (or non-performance!) of the GPU.

---

### Post by savafan on 2010-03-02
I got my system to accept the live CD. I had to change the priority in my bios.

UPON RE-INSTALL....All seemed fine to begin with....Then I saw some errors happen quickly...I/O...Logical error....353688...353689??? Too fast to read...

Then the black screen of death...All I could choose is the language, no time zone, no option on partitions....Nothing but black

---

### Post by sandyd on 2010-03-02
> **savafan said:**
> I got my system to accept the live CD. I had to change the priority in my bios.

UPON RE-INSTALL....All seemed fine to begin with....Then I saw some errors happen quickly...I/O...Logical error....353688...353689??? Too fast to read...

Then the black screen of death...All I could choose is the language, no time zone, no option on partitions....Nothing but black
If I were you, I would replace that hard disk.
IO errors indicate that the hard disk has read/write errors, which are a symptom of a failing/damaged disk

---

### Post by QIII on 2010-03-02
> **carlee said:**
> If I were you, I would replace that hard disk.
IO errors indicate that the hard disk has read/write errors, which are a symptom of a failing/damaged disk

Spot on.


Edit:  Unless....  Hmmm.  Bad ISO image?

---

### Post by savafan on 2010-03-02
I just happen to have a second disc here. In trying the second one I did not see the I/O errors after the series of checks....It just went directly to the blank screen once again.

Leave it to me to come up with the unusual....LOL...Story of my life

---

### Post by audiomick on 2010-03-02
maybe try to run smartmontools
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
from the live cd. That will give you an idea about the state of the drive, I think.

edit: but a bad ISO / burn might be a possibility....

---

### Post by teh603 on 2010-03-02
> **savafan said:**
> I didn't set it up, so I'm not entirely sure, but I know nothing about wubi. It is pretty much a dual boot. I have the option to run Ubuntu or XP 64 when I start the machine. The drive is partitioned for Ubuntu to have 400GB, & windows has 100gb. First option & default is Ubuntu.Ok, here's what's coming to mind. Admittedly, I haven't read the entire thread so I don't know all of what's going on, but these work for me.

When I want to boot off a LiveCD, I put it in the drive and hit either Esc or f12 at the splash screen, depending upon the BIOS you have. I don't try to boot off the HD, because the LiveCD/DVD won't be in the GRUB menu.lst (or whatever its called). When GRUB makes its menu, you can only select items listed in menu.lst, and your CD won't be in there.

Second, does your computer have an Intel i3 Processor and/or the Intel Arrandale chipset? If so, then you can't boot to any version of Karmic without some massive workarounds. If'n you want to try something risky, burn yourself a copy of Lucid Alpha 3 and join in the testing. It seems to work "out of the box," despite being "highly unstable."

---

### Post by QIII on 2010-03-02
savafan --

Perform the checks audiomick suggests and let us know what you find.

Carlee is probably correct, but I'd hate to send you to Office Depot to spend your money without knowing.

---

### Post by QIII on 2010-03-02
teh603 --

savafan says he had it working (poorly) at one point.  But working poorly certainly could be a possibility for what you have indicated.

(But my money is on Carlee's suggestion...)

---

### Post by savafan on 2010-03-02
This was a situation I had to begin with & a friend of mine helped me to be able to "see" it.

At this point, I'll have him stop by tomorrow evening & we'll see what we can do from there. I greatly appreciate all of your help here & I will let you know what happens...We will refer to this thread once I come to some conclusions.

Thank you all for now.

P.S....I would consider looking at Lucid if & when I can get this straitened out.

---

### Post by sandyd on 2010-03-02
> **QIII said:**
> teh603 --

savafan says he had it working (poorly) at one point.  But working poorly certainly could be a possibility for what you have indicated.

**(But my money is on Carlee's suggestion...)**
dont bet on me being right, sometimes im wayyy off.... ;)

---

### Post by QIII on 2010-03-02
> **carlee said:**
> dont bet on me being right, sometimes im wayyy off.... ;)

I've been a computer geek for 35 years or so.  Sometimes I think I am only getting more stupid - but I tell everyone that it's all a matter of the bifocals making it hard to see the keyboard, so I sometimes type stupid stuff.

Sometimes I have to call my Dad for help.  He's been a geek since the 40's.

---

### Post by savafan on 2010-03-02
I've only been a Geek in training for about 2 years & most of it has been within the last few months....Thanks QIII & carlee....I'll let you know.

---

### Post by savafan on 2010-03-04
I've re-installed, have my partitions set correctly, no errors detected & starting over. I'm not sure all of what has been done so I'm not going to mark this thread as "solved", but a friend of mine was on a mission to make this work for me & I saw many parts of this system that I never thought existed. All I can say is that I had to go into "Safe graphics mode"...(F4 options)  to be able to "see" the OS. The Black Screen of Death is still a mystery as to how it happened & why.

The re-install was not a problem & since it was only a few days old, I had literally nothing to lose. The challenge was getting the nvidia card & two screens to work properly & have the configurations saved as they are. I (he) has this forum to thank for that. The answers were here, it just took a while to find them. I wish I could say where & who to thank, but I really have no idea.

Thank you all for the help & I hope to see you in the next sections...

---

