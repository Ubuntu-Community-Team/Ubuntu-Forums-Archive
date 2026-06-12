---
title: "Just will not load"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Robert1305 on 2010-12-24
Hi All, absolute newbie to Ubuntu.

Have loaded 10.10 into my laptop no problems, works just fine, i really enjoy using it, but .......it just refuses to load into my desktop, when I boot up with the disk it goes straight into loading the OS without giving me any options, then after 30secs it freezes.

Tried 3 different disks all do the same.

Must be something on my PC that gets in the way.

Any help greatly appreciated.:confused:

---

### Post by TeoBigusGeekus on 2010-12-24
Could you give us your desktop specs?

---

### Post by verymadpip on 2010-12-24
Hi Robert 1305.

Are you getting a purple screen with 2 white icons at the bottom at any point before the install begins?  
If so, try hitting the esc key at that screen. That may take you to an options screen.

This got me an options screen.  However, I was being taken into a desktop session, not straight to installation.  I think it's worth a shot though.

---

### Post by Robert1305 on 2010-12-25
Still can not load 10.10.but..............................................can load, Mandriva, Mint, and ubuntu 9.04, but can not upgrade it.

Spcs are.,,,,, M/B Asus500, cpu...AMD 3000, ......mem.....4gb.......HDD......250gb.....Graphics.....ATI 8800gts.

self build all water cooled.

---

### Post by amjjawad on 2010-12-25
> **Robert1305 said:**
> Hi All, absolute newbie to Ubuntu.

Have loaded 10.10 into my laptop no problems, works just fine, i really enjoy using it, but .......it just refuses to load into my desktop, when I boot up with the disk it goes straight into loading the OS without giving me any options, then after 30secs it freezes.

Tried 3 different disks all do the same.

Must be something on my PC that gets in the way.

Any help greatly appreciated.:confused:

When you're booting from the LiveCD of Ubuntu 10.10, what exactly do you see? any message? any screen?

---

### Post by Robert1305 on 2010-12-25
> **amjjawad said:**
> when you're booting from the livecd of ubuntu 10.10, what exactly do you see? Any message? Any screen?

nothing goes straight to the blank desktop and freezes.

---

### Post by amjjawad on 2010-12-25
> **Robert1305 said:**
> nothing goes straight to the blank desktop and freezes.

Have you checked the MD5SUM for your downloaded iso?
Check "Step1" in my signature, there's a HOWTO check MD5SUM.

How did you create the LiveCD? did you follow the instructions here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) - step2 ?

---

### Post by IndyGunFreak on 2010-12-25
> **Robert1305 said:**
> Still can not load 10.10.but..............................................can load, Mandriva, Mint, and ubuntu 9.04, but can not upgrade it.

Spcs are.,,,,, M/B Asus500, cpu...AMD 3000, ......mem.....4gb.......HDD......250gb.....Graphics.....[B]ATI 8800gts.[/B}

self build all water cooled.

ATI 8800 gts?  8800gts sounds like an Nvidia card.  First, double check your graphics card.

If the live CD will not boot, there's the Alternate Install CD for this sort of thing.  It is all text based, but is not difficult if you pay attention to what you're doing.  I had an old PC that had a troublesome ATI card and would always freeze at the desktop.  I used the Alt CD, and it was fine.  I got so used to it, I always use the Alt CD now.

---

### Post by Robert1305 on 2010-12-26
There must be a setting on my PC thats been altered cos all disks that I put into the cd just bypass the intro set up screen and go direct to the install screen and then freeze.

---

### Post by amjjawad on 2010-12-26
> **Robert1305 said:**
> There must be a setting on my PC thats been altered cos all disks that I put into the cd just bypass the intro set up screen and go direct to the install screen and then freeze.

Not sure if I understood your post correctly but I guess you mean you can't choose whether to "TRY" Ubuntu or "Install" it and it just jumps to the installation?

Once you boot from the CD, you'll get a dark purple screen with a small icon for a man with opened armed. Once you see this, press any way. You'll then have to choose your language and choose whether to try or install Ubuntu.


[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]

---

### Post by Ustonkey on 2010-12-26
> **Robert1305 said:**
> There must be a setting on my PC thats been altered cos all disks that I put into the cd just bypass the intro set up screen and go direct to the install screen and then freeze.

HI,
   Sounds as though your Boot Record first Boot is set to your hard disk!  
    With ISO files your Boot Record needs to have your first Boot set to your CD/DVD. I'm sure there are some Guru's about that will tell you how to do that.:
                Ustonkey

---

### Post by IWantFroyo on 2010-12-26
Try checking your cd writer's speed. 
I had a problem like this because I put mine on maximum write. 
It skipped a bunch.
16x is a good bet.

---

### Post by Robert1305 on 2010-12-30
Adding further to this saga........

Nothing has worked, all the Linux disks I have just will not install the set-up screen.

Then I found an old 9.00 disk, so I tried it, it loaded like a dream and worked perfectly.

I used the upgrade manager to upgrade to 10.04, no problems the O/S is absolutely fine, its a joy to use.

I have tried to load 10.10 from a purchased Linux disk, but still no joy.

There is no upgrade to 10.10 showing in my U/M, as yet. :confused:

All the disks I have work OK on my laptop, could this be a bios problem.

---

### Post by amjjawad on 2010-12-30
> **Robert1305 said:**
> Then I found an old 9.00 disk, so I tried it, it loaded like a dream and worked perfectly.

Do you mean Ubuntu 9.10? did you managed to boot from the LiveCD and get to the desktop?


> I used the upgrade manager to upgrade to 10.04, no problems the O/S is absolutely fine, its a joy to use.

Did you upgrade 9.10 to 10.04 now and it's working?

> 
I have tried to load 10.10 from a purchased Linux disk, but still no joy.
There is no upgrade to 10.10 showing in my U/M, as yet. :confused:
All the disks I have work OK on my laptop, could this be a bios problem.
So, are you trying to say that everything can be loaded and worked like a charm except Ubuntu 10.10?

I'm a bit confused. What exactly are you trying to do now? If 10.04 is working fine so there is nothing wrong with BIOS or something.
There might be something in the iso file you downloaded (either the wrong iso or MD5SUM doesn't match Ubuntu 10.10 Hash) or a disc (CD/DVD) problem.

Isn't that your scenario? I hope I understood your post correctly.

---

### Post by Robert1305 on 2010-12-30
Nothing above 9.10 will load into my PC. either 10.04 or 10.10.

Thought it might be a bios prob because I could only get 10.04 to work by upgrading.

The 10.04 disk I use for installation is one I purchased from Linux shop, and it loads perfectly using my laptop.

---

### Post by amjjawad on 2010-12-30
> **Robert1305 said:**
> Nothing above 9.10 will load into my PC. either 10.04 or 10.10.

Thought it might be a bios prob because I could only get 10.04 to work by upgrading.

The 10.04 disk I use for installation is one I purchased from Linux shop, and it loads perfectly using my laptop.

So, bottom line is: The ONLY way to load 10.04 is when you use that disc you bought. Am I right?
Otherwise, no way to load 10.04 or 10.10. Right?

---

### Post by Robert1305 on 2010-12-30
No!....... the only way I can use 10.04 is to load 9.10 and upgrade to 10.04.

9.10 is the only disc that will load into my desktop PC, no others will, inc...mint, mandriva.10.04 or 10.10.

I even tried Win7, that will not load.

At the moment 10.04 is running perfectly, so am a bit loath to try anything new!!!!!!!!!!

---

### Post by amjjawad on 2010-12-30
> **Robert1305 said:**
> No!....... the only way I can use 10.04 is to load 9.10 and upgrade to 10.04.

9.10 is the only disc that will load into my desktop PC, no others will, inc...mint, mandriva.10.04 or 10.10.

I even tried Win7, that will not load.

At the moment 10.04 is running perfectly, so am a bit loath to try anything new!!!!!!!!!!

Either it's my flu (just went to hospital this morning) or something is missing in your post :)

Are we talking here about an installed OS that you're able to login to? or we're talking about Ubuntu 9.10 Disc (CD/DVD) that you can boot your machine with and use it as a LiveCD?

If you already installed 9.10 and you upgraded to 10.04 and it's working perfectly now then:
1- Do not do anything else as of now. Keep it as it's.
2- Try to find out why the other CDs/DVDs are not bootable

It's really weird that no CD/DVD nor USB could boot your machine.

The possible chances are:
1- Your media is damaged (CD/DVD/USB)
or
2- Corrupted download.
or
3- The software that you're using to burn CDs/DVDs or the USB Creator program has an issue.
or ... finally
4- Something wrong in your BIOS Settings. Your machine is booting ONLY from your HDD. In this case, you need to refer to your Motherboard Manual.


I don't think there are another possibilities.

Again, if your machine is working now perfectly, keep it as it's :)

---

### Post by amjjawad on 2010-12-30
I asked you 4 days ago this question:
> **amjjawad said:**
> Have you checked the MD5SUM for your downloaded iso?
Check "Step1" in my signature, there's a HOWTO check MD5SUM.

How did you create the LiveCD? did you follow the instructions here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) - step2 ?

But you did not answer me yet.

Please, do one thing. Read my below post very carefully and try to see what step or what setting you did NOT look into.
I'm sure something is missing as you're not providing us with the full details. No offense and don't worry about it but I really suggest to read the below post and check it step by step until you figure out what's wrong.


> **amjjawad said:**
> Either it's my flu (just went to hospital this morning) or something is missing in your post :)

Are we talking here about an installed OS that you're able to login to? or we're talking about Ubuntu 9.10 Disc (CD/DVD) that you can boot your machine with and use it as a LiveCD?

If you already installed 9.10 and you upgraded to 10.04 and it's working perfectly now then:
1- Do not do anything else as of now. Keep it as it's.
2- Try to find out why the other CDs/DVDs are not bootable

It's really weird that no CD/DVD nor USB could boot your machine.

The possible chances are:
1- Your media is damaged (CD/DVD/USB)
or
2- Corrupted download.
or
3- The software that you're using to burn CDs/DVDs or the USB Creator program has an issue.
or ... finally
4- Something wrong in your BIOS Settings. Your machine is booting ONLY from your HDD. In this case, you need to refer to your Motherboard Manual.


I don't think there are another possibilities.

Again, if your machine is working now perfectly, keep it as it's :)

---

### Post by albert s on 2010-12-30
could it be a dodgy CD reader and perhaps it was just sheer luck that the 9.10 disc booted up OK.....

---

