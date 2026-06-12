---
title: "Former Linux (Xandros) user looking to move back to Ubuntu"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by RVA Dennis on 2009-02-12
In 2002 I purchased and used Xandros on my then desktop, dual booting Windows and Xandros. When that machine died and after having fits trying to get wireless access, photo downloads, printer isuues, etc. I abandoned the dual boot and went back to Windows XP. I run a three year old Toshiba Satellite A105 with 1GB ram and an 80GB HD. Nothing special at all.

I have the Canonical provided installation disk for 8.10 and before I either run it in a partition I will use WUBI to install to run it in Windows XP at the outset.

I intend to keep XP because of two "Need To" isuues: 1). we use Quicken 2003 for all our financial finagling and 2). I have been programming my own forex trading software for 20+ years using Basic and now QB45. Since this is our source of income (trading), I can not give up these progrms and since I will be 68 on 8 March, I am not interested in learning a new Linux compatible language to re-write these essential analysis programs.

In Full Circle I saw mention by another "old timer" like myself of running Professional Basic in DOSbox and wonder if any has tried this with QB45? The Quicken issue is not as great a problem as my wife is treasurer and keep things going in that department and if I recall correctly GNU Cash is quite similar in many repects.

Anyone have other input/suggestions on running a DOS based program and especially compiled .exe files in Ubuntu? 

TIA

Dennis

---

### Post by DGortze380 on 2009-02-12
> **RVA Dennis said:**
> In 2002 I purchased and used Xandros on my then desktop, dual booting Windows and Xandros. When that machine died and after having fits trying to get wireless access, photo downloads, printer isuues, etc. I abandoned the dual boot and went back to Windows XP. I run a three year old Toshiba Satellite A105 with 1GB ram and an 80GB HD. Nothing special at all.

I have the Canonical provided installation disk for 8.10 and before I either run it in a partition I will use WUBI to install to run it in Windows XP at the outset.

I intend to keep XP because of two "Need To" isuues: 1). we use Quicken 2003 for all our financial finagling and 2). I have been programming my own forex trading software for 20+ years using Basic and now QB45. Since this is our source of income (trading), I can not give up these progrms and since I will be 68 on 8 March, I am not interested in learning a new Linux compatible language to re-write these essential analysis programs.

In Full Circle I saw mention by another "old timer" like myself of running Professional Basic in DOSbox and wonder if any has tried this with QB45? The Quicken issue is not as great a problem as my wife is treasurer and keep things going in that department and if I recall correctly GNU Cash is quite similar in many repects.

Anyone have an input on running a DOS based program and especially compiled .exe files in Ubuntu?

TIA

Dennis

If they are simple programs, all at the command line, you will likely be able to run them using wine ... although because you wrote it yourself, there are no guarantees, you'll have to try it to see.

---

### Post by LowSky on 2009-02-12
From what I have seen there are too many isses with WUBI, at least that has been what I've noticed. A Dualboot setup is best in my honest opinion.

Many people seem the to not like Gnucash when coming from the quicken world, but Good news there as Intuit seems to be releasing a web based version that will work on any system (got to love Cloud computing).

Your using really simple languages for coding, and wrinting with them will still be possible.

As for any of your other issues, like printing (Lexmarks are know to not work, HP works probably the best), Wifi is something that should just work, but in most cases if it doesnt their is a quick fix or simple driver to enable. Photo downloading is  rather simple now.


anything else your worried about feel free to ask.

---

### Post by Temposs on 2009-02-12
I think DOSbox is a pretty nice program and I've run one of the most advanced games made for DOS on it(Alone in the Dark 2), so it stacks up pretty well, I think.

You can also try running your QB program under Wine, and that will allow you even more flexibility if it works. (EDIT: that is, you will be able to start it up just like any other program, with a double-click on a shortcut)

I use GnuCash personally and find it acceptable for my needs. It's not the prettiest, but it works.

EDIT: You can also import your Quicken data into GnuCash.

---

### Post by RVA Dennis on 2009-02-12
> **LowSky said:**
> From what I have seen there are too many isses with WUBI, at least that has been what I've noticed. A Dualboot setup is best in my honest opinion.

Many people seem the to not like Gnucash when coming from the quicken world, but Good news there as Intuit seems to be releasing a web based version that will work on any system (got to love Cloud computing).

Your using really simple languages for coding, and wrinting with them will still be possible.

As for any of your other issues, like printing (Lexmarks are know to not work, HP works probably the best), Wifi is something that should just work, but in most cases if it doesnt their is a quick fix or simple driver to enable. Photo downloading is  rather simple now.


anything else your worried about feel free to ask.

Actually I have run Ubuntu from the CD and also from a partition but ran into an XP problem and did a clean reinstall of XP. In my experimentation I had no trouble with wireless access or my Canon printer, USB devices, etc. so the issue is my QB45 stuff.

I'll forge ahead with the WUBI for the moment and then do a dual boot install later. Need to take the time to do it right this time though :redface:.

I'll report back soon.

---

### Post by Hospadar on 2009-02-12
I would just go right into a dual boot, it's pretty low risk if you defrag windows first, back up anything extremely critical, then just resize the windows partition.

As for running windows and dos programs, dosbox works great for dos, and wine might work for windows, but virtualbox will almost definately work unless you are doing some kind of crazy network wierd setup (in which case it would still work, it would just take longer to set up).

I have really come to prefer virtualbox for most things windows because (as it runs a complete virtual copy of windows) every windows program I might need works perfectly without any monkeying around, although because it is a virtual machine, you need a decent (>=pentium 4 probably) machine with a more than puny (probably 512 or more) amount of ram to run it at a comfortable speed.  The old dell p4 gx270 in my office runs office in a vm great.

---

### Post by RVA Dennis on 2009-02-12
Thanks for the steer to Virtual Box, Hospadar.

I can see from the responses here and the postings and support offered in other threads Ubuntu is a far cry from my experience with Xandros 1.0 and 2.0. 

Appreciate all the help and suggestions made! I'll play with the Live CD mode for a bit and do the dual boot installation this weekend when I havemore time and fewer distractions - like my trading.

---

### Post by RVA Dennis on 2009-02-13
Aginst the advice to go straight to a dual boot partition I did an "install in Windows" last night and while most everything seems fine, I am unable to run my trading platforms which require Java and JavaWS. 

I installed openJavaJDK but can't get anything to load.

Any hints or suggestions what I have done wrong or haven't done?

---

### Post by jchiar on 2009-02-13
> **RVA Dennis said:**
> Aginst the advice to go straight to a dual boot partition I did an "install in Windows" last night and while most everything seems fine, I am unable to run my trading platforms which require Java and JavaWS. 

I installed openJavaJDK but can't get anything to load.

Any hints or suggestions what I have done wrong or haven't done?

Use this page as a start:
[https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu)
Then this one:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
Then, of course, this one:
[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)
and for any thing that is ever needed, 
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
Those are the Man pages for every release.

---

### Post by RVA Dennis on 2009-02-13
Thanks jchiar, followed the sdvice and now cab  run the JNLP app in Ubuntu. Resolution is crummy but I work on that. 

75% of the way there in about 18 hours so I am pleased thus far.

Once again thanks to all.

---

### Post by RVA Dennis on 2009-02-14
Did a refresh full install to dual boot with XP and so far it is going well. I have my quotes and trading platform working, page rendering et al are fine. Now on to getting my QB45 programs to run.

Tried installing Virtual Box but got an error message at the end of installing indicating corrupted files.

Hopefully can resolve that or try DOS box instead.

Again thanks for all the help and comments.

---

### Post by RVA Dennis on 2009-02-15
Have now gotten dos emulator running and my programs do boot up - now to sort out the linkage to my data files associated with each program.

Only real issue ATM is that associated with running an external monitor. If I enable the ProView LCD monitor it appears the desktop is simply strectched across the two screens in an "exploded" view. All the graphics, icons etc. are hugely magnified. Any thoughts on resloving that?

Otherwise quite pleased and impressed by the speed and ease of a full installation dual booting WinXP which I shall continue to use as primary OS while I familarize myself with Intrepid and get all the features in need and use daily operating. As I noted earlier I trade foreign currency online and my days are fairly long so it will be evenings and weekends for a while.

Thanks again for all the help and encouragement.

---

### Post by RVA Dennis on 2009-02-17
"Only real issue ATM is that associated with running an external monitor. If I enable the ProView LCD monitor it appears the desktop is simply strectched across the two screens in an "exploded" view. All the graphics, icons etc. are hugely magnified. Any thoughts on resloving that?"

Resolved that issue after downlading and installing an ATI driver. Perfect resolution and great font rendering after installing msttcorefonts package.

Now what I need to learn to do is how to get the two monitors "unsynchronized"; that is to be able to run a web browser on the primary monitor and Open Office or my rading platform or whatever else on the secondary monitor.

Suggestions?

---

