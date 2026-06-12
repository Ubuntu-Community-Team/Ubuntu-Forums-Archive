---
title: "[grandpa thread #2] emachines e525 - Ubuntu install disk not making progress"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Datum47 on 2011-07-04
Hi,
I'm installing 11.04 on my grandfather's computer (see my earlier thread). I have set it to boot from the disk drive in order to install Ubuntu. When I boot it, the disk starts fine (shows that little Ubuntu icon of the figure in the circle). This goes away a few seconds later and the disk sounds as if it is being read in the drive. However, this takes forever, and then............. it all goes quiet............ too quiet............... and the screen goes black. Still running, but no ' Install  /  try Ubuntu ' screen. What is the best course of action to get the install to work?
 
:)

---

### Post by dFlyer on 2011-07-04
Do a Try ubuntu before install to make sure all your hardware is supported. If the live desktop works enter the following command in a terminal:

/usr/lib/nux/unity_support_test -p

This will let you know if your hardware supports Unity.

---

### Post by Rex Bouwense on 2011-07-04
Have you used this CD before to install on any other computer because I suspect a bad burn.  If you have used it to install then perhaps your grandpa's computer doesn't have the guts to run Natty.  What are the computer specs?

---

### Post by apollothethird on 2011-07-04
> **Datum47 said:**
> Hi,
I'm installing 11.04 on my grandfather's computer (see my earlier thread). I have set it to boot from the disk drive in order to install Ubuntu. When I boot it, the disk starts fine (shows that little Ubuntu icon of the figure in the circle). This goes away a few seconds later and the disk sounds as if it is being read in the drive. However, this takes forever, and then............. it all goes quiet............ too quiet............... and the screen goes black. Still running, but no ' Install  /  try Ubuntu ' screen. What is the best course of action to get the install to work?
 
:)

Try creating a Live USB install.  See if that will boot.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Datum47 on 2011-07-04
> **dFlyer said:**
> Do a Try ubuntu before install to make sure all your hardware is supported. 

> **Datum47 said:**
> no ' Install  /  try Ubuntu ' screen.

I can't even get to that stage at the moment.





> **Rex Bouwense said:**
> Have you used this CD before to install on any other computer because I suspect a bad burn.  If you have used it to install then perhaps your grandpa's computer doesn't have the guts to run Natty.  What are the computer specs?

I haven't used it before. I will try it out on my own machine (already Ubuntu) quickly and see if I can get to the install/try stage.

To answer the second part of your question:

900 CPU - Intel Celeron

2 GB DDR2 memory

160 GB HDD




> **apollothethird said:**
> Try creating a Live USB install.  See if that will boot.



Not sure I have access to a USB stick atm - on a farm in the countryside of South Wales - but I will check.

---

### Post by Rex Bouwense on 2011-07-04
If you have a good burn the computer should boot from the CD.

---

### Post by verymadpip on 2011-07-04
Sorry, I've deleted my utter hogwash.

---

### Post by Datum47 on 2011-07-04
OK tried ubuntu on MY laptop, brings up the try/install screen more or less fine. will try getting that options list up like suggested, and if that does not work for some reason i will burn a new disk and try that. yes i will keep everyone posted. thanks for all the help. -d47

---

### Post by apollothethird on 2011-07-04
> **Datum47 said:**
> I can't even get to that stage at the moment.







I haven't used it before. I will try it out on my own machine (already Ubuntu) quickly and see if I can get to the install/try stage.

To answer the second part of your question:

900 CPU - Intel Celeron

2 GB DDR2 memory

160 GB HDD






Not sure I have access to a USB stick atm - on a farm in the countryside of South Wales - but I will check.

You might also try creating one of the minimum installation cd's:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Datum47 on 2011-07-04
Okay, I am still having the same problem so I am off to try burning a new disk. I will keep everyone posted

---

### Post by Rex Bouwense on 2011-07-04
Wait.  Before you burn a new disk, check the md5sum of the download:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
It is probably OK since you can boot on another computer.  You may need to do an alternate install.

---

### Post by apollothethird on 2011-07-04
> **Datum47 said:**
> Okay, I am still having the same problem so I am off to try burning a new disk. I will keep everyone posted

You definitely have the specs available for ubuntu 11.04.  I've seen problems where the LiveCD wouldn't boot on some machines.  But that never stopped it from actually working when using an alternate method of installation.

Grab one of the minicd from the link I gave you.  The mini OS is around 20 megs and might take you only two minutes do download.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Datum47 on 2011-07-04
> **apollothethird said:**
> Grab one of the minicd from the link I gave you. 

I have another engagement right now which I have to attend (specifically: dinner!) which should take 1 to 1.5 hours. I will try burning a MiniCD after that, and post the results. Thanks!

---

### Post by Rex Bouwense on 2011-07-04
I had to look up that mini-CD thing.  Wow!!  I never heard of it.  What a great idea.  I had to bookmark that site.  Excellent.:popcorn:

---

### Post by verymadpip on 2011-07-04
Hello Datum47 & everyone.
What about the possibility of trying the alternate (text based) installer before trying the mini?

It's less resource hungry, pretty simple & installs everything for you.

Sorry, I deleted the options I suggested as I thought the earlier posts were better ideas.
Just to riterate: F6 & try them all :)
ACPI=off worked for me when I had, what seems like, a similar problem.  Of course you have no battery charge indicator, which isn't great on a laptop.

---

### Post by apollothethird on 2011-07-04
> **verymadpip said:**
> Hello Datum47 & everyone.
What about the possibility of trying the alternate (text based) installer before trying the mini?

It's less resource hungry, pretty simple & installs everything for you.

Sorry, I deleted the options I suggested as I thought the earlier posts were better ideas.
Just to riterate: F6 & try them all :)
ACPI=off worked for me when I had, what seems like, a similar problem.  Of course you have no battery charge indicator, which isn't great on a laptop.

Hi, Verymadpip.  Can you tell me how to get to the text based install?  I would like to have had that option with some of my problem machines.

Thank!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by verymadpip on 2011-07-04
Hi apollothethird,
I'm not with it today, I meant to include a link,  Thanks for spotting that for me :)

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Hit 'the location near you' link in the first paragraph & you should be away.

I recommend using a wired connection with the alternate installer as it will save all the hassle of dealing with the network connection afterwards.  For me it meant that my wireless worked right out of the box when the install was finished, but it couldn't detect the wireless stuff properly during the install.  It seems like it does all that configuration for you if you are wired up.  Sorry I can't be more specific & technical, I'm a bit of a newb.

---

### Post by apollothethird on 2011-07-04
> **verymadpip said:**
> Hi apollothethird,
I'm not with it today, I meant to include a link,  Thanks for spotting that for me :)

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Hit 'the location near you' link in the first paragraph & you should be away.

I recommend using a wired connection with the alternate installer as it will save all the hassle of dealing with the network connection afterwards.  For me it meant that my wireless worked right out of the box when the install was finished, but it couldn't detect the wireless stuff properly during the install.  It seems like it does all that configuration for you if you are wired up.  Sorry I can't be more specific & technical, I'm a bit of a newb.

I believe the link that you gave is one of the steps to get to the link that I gave.  By the time the user finish navigating he'll end up on the minicd page.  The minicd is necessary for the boot to start the actual installation.

There are other options on the page you linked to which includes the wubi installed.  I'm sure he wouldn't have any problems performing that install, but that's not a direction I'd recommend.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by verymadpip on 2011-07-04
H'mmm, is this any better?  It offers desktop, server or alternate.

[http://mirror01.th.ifl.net/releases//natty/](http://mirror01.th.ifl.net/releases//natty/)

There are links in the text as well as in the huuuge list.

I see what you mean about the link I gave, not very clear or helpful.
Also sorry to have duplicated.

I don't know much about wubi.  It doesn't sound like something I'm comfortable with TBH. Dunno why not, but there you go.  I've always had an installation in its own partition or on its own HDD, more by accident than judgement.

I don't want the OP to waste his time or resources, so whatever will get the job done most efficiently.  As I say I'm a newb myself really so my advice probably isn't the best.

---

### Post by DawieS on 2011-07-04
> **Datum47 said:**
> However, this takes forever, and then............. it all goes quiet............ too quiet............... and the screen goes black.
I once had exactly the same behaviour when installing 10.04 from a Live CD. It turned out that the PC did NOT have a Floppy Disk Drive, which was NOT disabled in the BIOS. This caused the installer to endlessly search for hardware that did not exist!

Sometimes the simplest of things are easily overlooked, and are the most time-consuming to find...
:confused::shock::oops:

---

### Post by verymadpip on 2011-07-04
> **DawieS said:**
> I once had exactly the same behaviour when installing 10.04 from a Live CD. It turned out that the PC did NOT have a Floppy Disk Drive, which was NOT disabled in the BIOS. This caused the installer to endlessly search for hardware that did not exist!

Sometimes the simplest of things are easily overlooked, and are the most time-consuming to find...
:confused::shock::oops:

Ha. Windows 7 did that to me.  Disabled didn't work, but set to 'none' did.

---

### Post by mastablasta on 2011-07-05
> **apollothethird said:**
> I believe the link that you gave is one of the steps to get to the link that I gave. By the time the user finish navigating he'll end up on the minicd page. The minicd is necessary for the boot to start the actual installation.

 
minimal ISO CD is barebones Ubuntu.
 
Alternate CD is normal ubuntu with text based installer.: [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
 
Also it would be good to remove your e-mail address from your signature unless you have desire for spam to clutter your email.

---

### Post by apollothethird on 2011-07-05
> **mastablasta said:**
> minimal ISO CD is barebones Ubuntu.

Alternate CD is normal ubuntu with text based installer.: [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

Also it would be good to remove your e-mail address from your signature unless you have desire for spam to clutter your email.

Hi, Mastablasta.  I don't know specifically what you're referring to as far as a minimal ISO CD, per barebones Ubuntu.  I don't recommend a barebones installation.  I don't even know, per se, what a barebones Ubuntu is.  I thought there was an Ubuntu Desktop and an Ubuntu Server.  My recommendation is the Ubuntu Desktop of which the link I gave him will give him a very small 22 mg disc image of which he can probably download in seconds, easily boot to, and install the full Ubuntu 11.04.  Not a barebones Linux.  ...and again, I haven't heard of a barebones Ubuntu.  I know there are various installations with different names such as Wubi, Xubunto, Kubunto, etc.  But I'm speaking specifically Ubuntu... and even more specifically, Ubuntu 11.04 Desktop, which will default to Unity if he has the hardware to run and fall back to Ubuntu classic if he doesn't.

He has already downloaded the regular image file.  If you review the messages you'll see that, the image you linked to will not boot on his machine.  Even if the image did boot on his machine, I don't see an option on that disk to go into a text based installer.  Also, if it did boot, I can't really see the need or desire for wanting to use a text base installation when you could have the full gui installation.

It's possible, however, that one might navigate the link you gave and find the small text base installation that I gave a direct link to which is the miniCD (the small 22 meg iso file) which will almost certainly work in this case.

I'm hoping that I'm clarifying your confusion and making it easy for the OP to go directly to what he's looking for.  A quick and easy full Ubuntu 11.04 installation resource.

At first I had the same confusion with the CD install that you appear to have with this miniCD install.  When I first moved to Ubuntu I looked high and low for the DVD iso because all the other distros I had used had either a bunch of CD's for the install or a DVD for the install.  It took me a while to realize that the Live CD provided the full install.  I even downloaded the DVD to install on one of my machines.  The resulting OS setup and configuration was exactly the way the LiveCD installed.  They both performed updates over the Internet during the install.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by no2498 on 2011-07-06
on my dell computer i had to turn off every thing but the cd/dvd
yes every thing no hard drive or anything

---

### Post by cheesennacho on 2011-09-16
i know this is an old thread but what was the final outcome?

---

### Post by Rex Bouwense on 2011-09-16
Don't know.  We are still waiting.

---

