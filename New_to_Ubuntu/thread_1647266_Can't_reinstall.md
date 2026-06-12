---
title: "Can't reinstall"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by helpdrew on 2010-12-17
I cannot reinstall Ubuntu. I had it working once except for a no shutdown problem. I tried fixing that and could no longer get a GUI. I went thru several suggestions but just could not get the graphical desktop back. In order to get to a familar start point I reinstalled Windows XP. That works fine. Now I tried to reinstall ubuntu using the same cd as before and all I get is blank screen once again. Using ctl+alt+F2 I get to a tty screen which says: 
*Linux ubuntu 2.6.35-22-generic #33-Unbunti SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux*
*Ubuntu 10.10*
*Welcom to Ubuntu!*
**Documentation: https.ubuntu.com*
 
*To run a command as administrator (user "root"), see "sudo command)>.*
*See "man sudo_root" for details.*
 
*[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]*
 
I do not know what to  do from this point.

---

### Post by amjjawad on 2010-12-17
> **helpdrew said:**
> I cannot reinstall Ubuntu. I had it working once except for a no shutdown problem. I tried fixing that and could no longer get a GUI. I went thru several suggestions but just could not get the graphical desktop back. In order to get to a familar start point I reinstalled Windows XP. That works fine. Now I tried to reinstall ubuntu using the same cd as before and all I get is blank screen once again. Using ctl+alt+F2 I get to a tty screen which says: 
*Linux ubuntu 2.6.35-22-generic #33-Unbunti SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux*
*Ubuntu 10.10*
*Welcom to Ubuntu!*
**Documentation: https.ubuntu.com*
 
*To run a command as administrator (user "root"), see "sudo command)>.*
*See "man sudo_root" for details.*
 
*ubuntu@ubuntu:~$*
 
I do not know what to  do from this point.

What's your hardware specifications? especially the Graphics Card.

---

### Post by helpdrew on 2010-12-18
This is a Sony Laptop Model PCG 993L. The BIOS says it is a PCG-FX340. It is a Pentium III with 512 mb of RAM and a 10 Gb hard drive.  It has an Intel video chipset on the motherboard 82815. I updated the BIOS and the video driver just recently with files from Sony's web site. This was after I had trouble with the first installation.

---

### Post by amjjawad on 2010-12-18
> **helpdrew said:**
> This is a Sony Laptop Model PCG 993L. The BIOS says it is a PCG-FX340. It is a Pentium III with 512 mb of RAM and a 10 Gb hard drive.  It has an Intel video chipset on the motherboard 82815. I updated the BIOS and the video driver just recently with files from Sony's web site. This was after I had trouble with the first installation.

I installed Ubuntu 10.10 on P4 3.0GHz with 448MB of RAM.

I'll do my best to provide the best advice :)

1) What was the size of SWAP Partition that you set? I strongly recommend to allocate 1GB for Swap.

2) Are you able to boot from USB? if yes, try to create a LiveUSB for Ubuntu 10.10 or 10.04 and see if you could get the desktop (GUI) and keep trying Ubuntu for sometime.

3) If you'll notice that you can't get the GUI or there are some problems like lagging, slowness, etc... then there are many other solutions.

4) I have a list of at least 10 other alternatives to try. Are you interested? some are based on Ubuntu and some other are not. If yes, let me know.

---

### Post by helpdrew on 2010-12-18
> **amjjawad said:**
> I installed Ubuntu 10.10 on P4 3.0GHz with 448MB of RAM.
 
I'll do my best to provide the best advice :)
 
1) What was the size of SWAP Partition that you set? I strongly recommend to allocate 1GB for Swap.
 
2) Are you able to boot from USB? if yes, try to create a LiveUSB for Ubuntu 10.10 or 10.04 and see if you could get the desktop (GUI) and keep trying Ubuntu for sometime.
 
3) If you'll notice that you can't get the GUI or there are some problems like lagging, slowness, etc... then there are many other solutions.
 
4) I have a list of at least 10 other alternatives to try. Are you interested? some are based on Ubuntu and some other are not. If yes, let me know.
I did not set up a swap partition. Did not know one is required. Laptop has XP on it and I chose to Install Ubuntu not do a dual boot. If a swap partition is needed please explain.
This machine will not boot from a USB. BIOS only allows CD, floppy drive, Hard Drive, or network.
Can't get to an ubuntu GUI at all. 
I am open to trying any suggestions you may have

---

### Post by amjjawad on 2010-12-18
> **helpdrew said:**
> I did not set up a swap partition. Did not know one is required. Laptop has XP on it and I chose to Install Ubuntu not do a dual boot. If a swap partition is needed please explain.
This machine will not boot from a USB. BIOS only allows CD, floppy drive, Hard Drive, or network.
Can't get to an ubuntu GUI at all. 
I am open to trying any suggestions you may have

Definitely, you need a **[swap partition]("https://help.ubuntu.com/community/SwapFaq") **but first of all, I need to know whether this is a **[Wubi Installation]("https://help.ubuntu.com/community/Wubi")** or [**Normal Installation**]("https://help.ubuntu.com/community/Installation")?

Are you willing to Install Ubuntu and**[ Dual Boot with XP]("https://help.ubuntu.com/community/WindowsDualBoot")**? or you want Ubuntu to be the only OS you may have on your machine?

---

### Post by helpdrew on 2010-12-18
> **amjjawad said:**
> Definitely, you need a **[swap partition]("https://help.ubuntu.com/community/SwapFaq") **but first of all, I need to know whether this is a **[Wubi Installation]("https://help.ubuntu.com/community/Wubi")** or [**Normal Installation**]("https://help.ubuntu.com/community/Installation")?

Are you willing to Install Ubuntu and**[ Dual Boot with XP]("https://help.ubuntu.com/community/WindowsDualBoot")**? or you want Ubuntu to be the only OS you may have on your machine?
This is a normal installation. I want Ubuntu to be the only OS on this machine.

---

### Post by amjjawad on 2010-12-18
> **helpdrew said:**
> This is a normal installation. I want Ubuntu to be the only OS on this machine.

Great.

Shall we start? :)

1) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
This link will show you how to download Ubuntu and create a LiveCD.
Check [Step1 ]("http://www.facebook.com/note.php?note_id=152426241466147")in my signature. You need to check the MD5SUM for the iso file you'll download. I assume you don't have a LiveCD yet. 

2) I already posted a link of Installation on my previous post.
I suggest to read it.

3) If you want to skip that Installation guide and the other guides which I do not recommend, then you need to do this:

a- Boot your machine from the LiveCD

b- Choose to "TRY" Ubuntu - Do not install

c- Once you get the GUI Desktop, try to explore Ubuntu and see if it works for you. Most likely, it will be painfully slow but the point is, if you can't run the LiveCD and will give you error messages, etc then you may want to try another alternative, Xubuntu, Lubuntu and many other alternatives are also available.

d- If you still want to stick with Ubuntu then you need to create at least 1GB Swap Partition.

e- Follow the guides I already posted and check my signature, there's a guide (facebook page) with tons of useful information. That would make your job easier.

f- The best **[partitions scheme]("https://help.ubuntu.com/community/HowtoPartition")** that you may have is:

HDD is 10GB so
7GB for root partition
2GB for /home partition
1GB for swap partition

OR

You may skip /home partition and give the whole 9GB for root partition.

You could use [GParted ]("https://help.ubuntu.com/community/GParted")(System > Administration > GParted) to do that and you need to choose either Manual Installation or let Ubuntu to install all by itself but I don't recommend that.

I think it's better to try another alternatives but again, I'm not going to suggest more until you try Ubutnu, install it and see how it's going to be.

Please, read the guides/links I'm including as this will help you so much.

;)

---

### Post by helpdrew on 2010-12-18
[amjjawad]("http://ubuntuforums.org/member.php?u=941822") you are awsome thanks for taking me under your wing. I read all the files in your signature. Great stuff, very informative. 
1. So I have a Live CD. I used it once before on this maching and got to the GUI but I had trouble shutting down so I changed something, and I do not know what but I can no longer get a GUI. I made the Live CD with a VISTA Machine I have and the CD worked the first time around. I have done 3a and 3b as outlined in your reply but all I get is a blank screen after the CD drive stops. I can push ctl+alt+f2 and I get the following:
Linux ubuntu 2.6.35-22-generic #33-Unbunti SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
*Ubuntu 10.10*
*Welcom to Ubuntu!*
**Documentation: https.ubuntu.com*

*To run a command as administrator (user "root"), see "sudo command)>.*
*See "man sudo_root" for details.*

*[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]*
I can go no farther than this.

---

### Post by amjjawad on 2010-12-18
> **helpdrew said:**
> [amjjawad]("http://ubuntuforums.org/member.php?u=941822") you are awsome thanks for taking me under your wing. I read all the files in your signature. Great stuff, very informative. 
1. So I have a Live CD. I used it once before on this maching and got to the GUI but I had trouble shutting down so I changed something, and I do not know what but I can no longer get a GUI. I made the Live CD with a VISTA Machine I have and the CD worked the first time around. I have done 3a and 3b as outlined in your reply but all I get is a blank screen after the CD drive stops. I can push ctl+alt+f2 and I get the following:
Linux ubuntu 2.6.35-22-generic #33-Unbunti SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
*Ubuntu 10.10*
*Wel*** to Ubuntu!*
**Documentation: https.ubuntu.****

*To run a ***mand as administrator (user "root"), see "sudo ***mand)>.*
*See "man sudo_root" for details.*

*ubuntu@ubuntu:~$*
I can go no farther than this.

First of all, if you really want to thank me, then do your best to make this machine up and running :)
I'll be with you step by step and hopefully we could make this machine up and running. Nothing is impossible. You're wel***e anytime :)

Okay, so before, you managed to get the GUI desktop from the same CD, right?
What's the version of Ubuntu that you're trying to install? 10.04 or 10.10?

Before, when you got the GUI desktop, was that the same version of Ubuntu that you're trying to install now? I assume the answer is yes for that question. I also assume you had the same RAM as before. Usually, the LiveCD requires 512MB RAM to run but since you've done it before, you should *be able to *do it now.

I have couple of suggestions for you:

1- Try to download a new copy of Ubuntu. I re***mend 10.04.
2- Check the md5sum for it
3- Burn a new CD (create LiveCD)
4- Try it out and let me know what will happen.

Or

1- [http://www.xubuntu.org/get](http://www.xubuntu.org/get)
2- [http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

Or
if you need super fast machine then

1- [antiX]("http://antix.mepis.org/index.php?title=Main_Page")
2- [Slitaz]("http://www.slitaz.org/en/get/")
3- [Linux Mint Fluxbox]("http://www.linuxmint.***/index.php")

There are actually lots more ;)

Problem is, you can't get the Live Session to start. It means you need to start thinking to use some other alternatives. Yes, you can install Ubuntu on that machine but it won't be as fast as installing other alternatives.

I installed Mint Flux on PII with 64MB RAM and 4.5GB HDD. Is it working? oh yes. Is it slow, big time :)
I was testing something and it worked. I'm trying to install something much lighter but I don't have time for that 12 years laptop now.

If I were you, I would go for Xubuntu and/or Lubuntu as these two are based on Ubuntu but use different Desktop Environment.

Let me know if you need more info ;)


P.S.
What's wrong with **w e l c o m e** and **r e c o m m e n d**? some letters are replaced with "*" O.o

---

### Post by helpdrew on 2010-12-19
I really want to use Ubuntu 10.10 on this machine. I already downlaoded a new copy so how do you check the md5sum file if you can't get Ubuntu to work? Can it be checked and verified using VISTA?

---

### Post by amjjawad on 2010-12-19
> **helpdrew said:**
> I really want to use Ubuntu 10.10 on this machine. I already downlaoded a new copy so how do you check the md5sum file if you can't get Ubuntu to work? Can it be checked and verified using VISTA?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/UbuntuHashes#10.10](https://help.ubuntu.com/community/UbuntuHashes#10.10)

---

### Post by helpdrew on 2010-12-21
Ok so I got the MD5SUM checked and verified on a new download of both Ubuntu 10.10 and Xubuntu 10.10 I followed your instructions and got to Part II - "Choose: Try Ubuntu without Installation" The cd drive and the hard disk spin but no GUI. So I'm right back where I started. I just get a blank screen after choosing " Try Ubuntu without Installing" or 'Install Ubuntu" for either Xubuntu or Ubuntu.

---

### Post by Quackers on 2010-12-21
When booting from the live cd/usb press the Esc key and a new screen will appear. Pressing F6 will bring up some options. Choose the nomodeset option and then continue. Hopefully it will boot ok.

---

### Post by helpdrew on 2010-12-22
I pressed f6, got the list, arrowed to nomodeset, pushed 'enter', an x appeared but when I pushed 'enter' again the x disappeared and boot would not continue,  I realize there is something basic I am not doing so please explain.

---

### Post by Quackers on 2010-12-22
Try the other options one at a time to see if any allow booting.

---

### Post by helpdrew on 2010-12-23
OK let me make sure I'm doing this correctly. I get to the screen asks if I want to dual boot. So I try. Blank screen. Then I push f-6 and get a list of options. I highlight each of the options and press enter. Then I hit escape and which gets me back to the selection screen and I hit enter to continue the boot. Is this the correct sequence?

---

### Post by amjjawad on 2010-12-24
> **Quackers said:**
> **When booting from the live cd/usb** press the Esc key and a new screen will appear. Pressing F6 will bring up some options. Choose the nomodeset option and then continue. Hopefully it will boot ok.

To the OP, please read the above post carefully ;)

---

### Post by helpdrew on 2010-12-28
Thank you to everyone on this thread for your help. However, nothing attempted so far works. I can start WinXP just fine. This was when I saw my partitions are FAT-32 not ntfs. Don't know if that makes a difference. Also I am running this laptop on AC power without a battery installed.

---

### Post by amjjawad on 2010-12-28
> **helpdrew said:**
> Thank you to everyone on this thread for your help. However, nothing attempted so far works. I can start WinXP just fine. This was when I saw my partitions are FAT-32 not ntfs. Don't know if that makes a difference. Also I am running this laptop on AC power without a battery installed.

Hello there,

It's been quite some time now since you last posted :)

There are few more questions will help us to understand what is going on.

1) Your RAM is 512MB, correct? how much you share (from RAM) with your Graphics Card? If your Graphics Card is built-in then it will use some of your RAM as a Graphics Memory. Try to reduce that to 32MB for example.

2) What's the name of the iso file you downloaded?

3) What speed you're using to burn the CD? use the minimum.

4) Are you still using 10.10? did you try 10.04?

5) Have you tried other distributions? 

6) Does your CD-Drive works perfectly without problems?

7) Do you have an USB-Port? if yes then try this: [http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)
With Plop, you could boot from USB.

---

### Post by helpdrew on 2010-12-30
Answers to AMJJAWAD's questions:
1. Yes I have 512mb RAM. I do not know how to check to see how much is dedicated to the graphics card. Please advise how. 
2. ISO File Name is xubuntu-10.10-desktop-i386
3. Reduced speed of cd burner to 16x.
4 Have not tried 10.04. I will do that and report back.
5. I tried two distributions within US ut I do not remember which ones.
6. I have had no problems with my cd drive
7. Tried booting from the usb-port with the same results. I go to a blank screen.
 
cnt+alt+f1 brings up a text screen that shows errors. It is talking about some 'buffer lockups' and it cannot unlock them

---

### Post by amjjawad on 2010-12-30
> **helpdrew said:**
> Answers to AMJJAWAD's questions:


> 1. Yes I have 512mb RAM. I do not know how to check to see how much is dedicated to the graphics card. Please advise how. 

This Option should be available in BIOS. Can't remember under what title exactly.

> 2. ISO File Name is xubuntu-10.10-desktop-i386

Okay, so you're trying Xubuntu now. Good.
Did you check MD5SUM?

> 3. Reduced speed of cd burner to 16x.

And still nothing happened? If MD5SUM did not match Xubuntu Hash then you can't burn that iso, you need to download new one.

> 4 Have not tried 10.04. I will do that and report back.

Okay.

> 5. I tried two distributions within US ut I do not remember which ones.

Try antiX and SliTaz. There are a lot more if you want.

> 6. I have had no problems with my cd drive

That's good.

> 7. Tried booting from the usb-port with the same results. I go to a blank screen.
 
But did you get that screen which asks you whether you want to "TRY" or "INSTALL" Ubuntu? the dark purple one?

---

### Post by alexcckll on 2010-12-30
The OP could always try buying an Ubuntu CD from someone like Linux Emporium.. or even buy a preinstalled machine - and take all the pressure off.

That's what I did...

---

### Post by amjjawad on 2010-12-30
> **alexcckll said:**
> The OP could always try buying an Ubuntu CD from someone like Linux Emporium.. or even buy a preinstalled machine - and take all the pressure off.

That's what I did...

That's not a solution, that's called giving up :)

---

### Post by helpdrew on 2010-12-31
Folks, excuse my n[COLOR=black][FONT=Verdana]aiveté but what does 'OP' mean?[/FONT][/COLOR]

---

### Post by helpdrew on 2010-12-31
More answers to AMJJAWAD's questions:
1.Used 'dxdiag' in the Run box under Winxp an found I have 32meg of video memory
2. MD5SUM test came back good.
3. Same as above 
4. Tried 10.04 got the same results. Blank screen. If I ctl+alt+f1 9of f2) I get a text screen that welcomes me to Ubuntu. I booted from USB which works very well.
7. *But did you get that screen which asks you whether you want to "TRY" or "INSTALL" Ubuntu? the dark purple one?*
When I first power up and select a usb boot I get the choices of running from the usb  or Installing plus some other choices. Screen appears to be purple. After I make my selection I see the word 'Unbuntu" with dots blinking under it. When that finishes I get a blank screen.

---

### Post by QLee on 2010-12-31
[QUOTE=helpdrew]Folks, excuse my n[COLOR=black][FONT=Verdana]aiveté but what does 'OP' mean?[/FONT][/COLOR][/QUOTE]

Original Poster or Original Post , depending on context of the statement in which it is used. Just a short way to state the user starting the thread or the first post.

---

### Post by helpdrew on 2010-12-31
Thank you QLee

---

### Post by amjjawad on 2011-01-03
Sorry, I've been very sick and couldn't login. I'm getting better and will be back to action soon.
Is there any update? did you manage to fix it or not yet?

---

### Post by helpdrew on 2011-01-04
AMJJAWAD, sorry to hear you are sick. Please get well. Have not been able to fix this problem. I have downloaded 10.10, 10.04, xubuntu 10.10 put each of them on usb ans cd. Did thr md5sum checks on each and the results are the same.

---

### Post by helpdrew on 2011-01-04
Sorry I need to expand this a little. The md5sum checks all came out good. The problem remains a blank screen after boot sequence. I get the text style choice screen wanting to know if I want to run from the usb (or cd) or if I want to install. It does not matter what I select the results are always the same. After the boot sequence is (and I assume here) complete I get a blank screen. I can do ctl+alt+f1 and get to the ubuntu command prompt but cannot go any where from here in the way of getting a GUI. I do a 'dir' ant I see a directory called 'Desktop' but I cannot do anything with it.

---

### Post by egalvan on 2011-01-04
> **helpdrew said:**
> I cannot reinstall Ubuntu.
I **had it working once **except for a no shutdown problem. 
Now I tried to reinstall ubuntu **using the same cd as before **and all I get is blank screen once again. 


If indeed you are using the **EXACT SAME CD** as before,
and you cannot boot from it,
this points to hardware.

Can you reach the screen that offers several choices?
Look for the following two choices..

first
**Check media for errors**  (or similar language)

make **SURE** you have no errors.
Just checking the downloaded iso for md5sum is not enough...
you have to be sure that the burn was good.

second
**Run Memory Test** (or similar language, it may be called ``memtest``)

run it, and let it run for at least one full cycle...
patience may be needed...
(yes, just passing the first four tests is a good indicator of decent RAM)

Once these two test out OK, then start looking at possible BIOS changes, especially the power settings.
Another place to look is video.

And check the BIOS battery, it´s a cheap 2032 cell.

---

### Post by helpdrew on 2011-01-05
First thought was the cd was bad so I made others. Then I made a bootable USB Stick. did the Memory Test and checked the BIOS battery. All checked good. Upgraded BIOS seversl days ago. I do beleive this is a hardware problem. Again, as stated before, Windows works fine but that is not what I want

---

### Post by amjjawad on 2011-01-06
Hi again,

I just read your whole thread trying to find out what more options we could try and we haven't yet.

There you go:

1) When you get the Command Line Interface (CLI) instead of GUI, what will happen when you type:
```
startx

```
or
```
sudo startx

```


2) I found this in other threads: 

```
sudo service gdm start
``` 

or 

```
sudo service gdm restart
``` 

Try that.

3) Have you tried the Alternate CD?
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

4) You can also try the Server Version and then install GNOME or any other Desktop Manager

Last two remedies:

5) Format the HDD and then start to install

6) Take the HDD outside your laptop, connected to another machine, install from there and put it back in. This is what I have done with a 12 years old laptop with NO CD-Drive, NO LAN, nothing. That was the only way to install Linux and it worked.
Don't try that if you don't know how to do it. I checked the laptop's manual to make sure how to pull the HDD outside.


If NONE of the above worked then ... try something else which is NOT Ubuntu.
I have more than 60 iso files for different distributions on my external HDD. I have tired most of them but did not try with others.
Here's a good site to find more about that: [http://distrowatch.com/](http://distrowatch.com/)

Don't give up hope. There must be a way to do it. Your laptop is still better than the one I'm telling you about. Mine is P2 366MHz with 64MB RAM.

I know using another distribution is NOT a solution to fix Ubuntu but sometimes our hardware is giving us less options to try and more limitations. Note that I'm not saying to give up but I'm just offering more choices :)

Let me know what will happen.

---

### Post by helpdrew on 2011-01-07
Hello AMJJAWAD, glad to see you back - and feeling better I hope. You've gived me a lot of good stuff to do. I'll let you know what happends.

---

### Post by amjjawad on 2011-01-07
> **helpdrew said:**
> Hello AMJJAWAD, glad to see you back - and feeling better I hope. You've gived me a lot of good stuff to do. I'll let you know what happends.

Hello :)
Thanks mate, I feel much better now, thank God.

I'm here as always so let me know what will happen and I'll be very glad to help the best I could :)

---

### Post by helpdrew on 2011-01-08
amjjawad you did it. I tried installing v10.04 per your suggestion and each command you suggested and lo and behold - "sudo service gdm restart" did it. I now have the Ubuntu GUI and am actively using it. Still some lingering issues. The GUI does not fill the entire screen of this laptop and I cannot get Firefox to run (Google Chrome works though) but those will be issues for a different thread. Thank you so much for your [COLOR=black][FONT=Verdana]patience[/FONT][/COLOR] and dedication.

---

### Post by amjjawad on 2011-01-09
> **helpdrew said:**
> amjjawad you did it. I tried installing v10.04 per your suggestion and each command you suggested and lo and behold - **"sudo service gdm restart" did it.** I now have the Ubuntu GUI and am actively using it. Still some lingering issues. The GUI does not fill the entire screen of this laptop and I cannot get Firefox to run (Google Chrome works though) but those will be issues for a different thread. Thank you so much for your [COLOR=black][FONT=Verdana]patience[/FONT][/COLOR] and dedication.


HOOHAA, well done :) I'm really very glad you got the GUI :)
And you're most welcome!

It's okay, I'll try to help you here, no need for another thread.

As for the screen, try from:

System > Preferences > Monitors

Try to adjust it from there. If nothing will happen, sure we'll find another solution :)


As for Firefox, it never let me down and always run like a charm.
Is there any error message? I remember you had 512MB of RAM, right? how big your swap is?
Even with 512MB of RAM and I guess 32MB is reserved for the Graphics Memory, Firefox will work.
So, please let me know what error message if there is any will show up?

Try to run it from Terminal (Applications > Accessories > Terminal)
Just type "firefox" in Terminal. "f" is small one.

Chrome with few tabs could take more RAM Space than Firefox sometimes. Perhaps you need to re-install Firefox but that's a later stage we'll do it in case we have to.

Waiting for your reply :)

P.S.
If you decided to start a new thread, then mark this one as "Solved" from the "Thread Tools". Feel free to send me the link of the new thread in a Private Message. However, I still prefer to finish it here ;)

---

### Post by helpdrew on 2011-01-09
We will keep this thread going right here. 
Downloaded all recommended updates and had a shutdown problem. I had to hold the power button to get it to turn off. When I started up today I did nit have any toolbars, just the blank screen. I restarted two more times and the toolbars reappeared. 
Looked at ths Monitor selection in System > Preferences > Monitors and it says the monitor is unknown and allows 800X600 or 640X480 with a 4:3 Aspect Ratio. for each. 60 or 56 Hz and Normal Rotation. 
With Firefox, I get no error messages. Whenever I select it by icon or through the terminal I get the same results. I get the rotating ball and then nothing.

---

### Post by amjjawad on 2011-01-10
> **helpdrew said:**
> Downloaded all recommended updates and had a shutdown problem. I had to hold the power button to get it to turn off. 

I had that problem for years even before I use Ubuntu. 2 weeks ago (I guess) I wiped my 500GB HDD and install Ubuntu as the only OS on this PC. The shutdown problem was fixed and I just can't believe it :) I didn't bother with that because I never switch my PC OFF. Now, I do because I don't have anything more to download.

There are many threads here about that. This might help:
[http://ubuntuforums.org/showthread.php?t=1466589](http://ubuntuforums.org/showthread.php?t=1466589)


> When I started up today I did nit have any toolbars, just the blank screen. I restarted two more times and the toolbars reappeared.
You mean the Top and bottom panels, right? :)

There are many guides on google for restoring that.
I once removed mine by mistake and I followed this to fix it.

[http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html)


> Looked at ths Monitor selection in System > Preferences > Monitors and it says the monitor is unknown and allows 800X600 or 640X480 with a 4:3 Aspect Ratio. for each. 60 or 56 Hz and Normal Rotation. Did you try to change the resolution? still the desktop does not fill your whole screen?

> 
With Firefox, I get no error messages. Whenever I select it by icon or through the terminal I get the same results. I get the rotating ball and then nothing.Applications > Accessories > Terminal

```
sudo apt-get purge firefox -y

```You need to enter your root password.

Then try this:

```
sudo apt-get update
sudo apt-get install firefox -y

```
Other alternatives:

```
sudo apt-get install chromium-browser -y

``````
sudo apt-get install midori -y

```

---

### Post by zer010 on 2011-01-10
Concerning the screen resolution, I'm not sure about a Sony, but I've seen some laptops that have resolution settings in the BIOS. You might try checking the BIOS and see if there is any options that could help. 
Hope you get everything up and running well!
PS:  If you still have issues shutting down, you can do it from the command line, as I've had to do it a couple times on a friend's laptop. 
You can get all of the options by reading the "man"(manual)page for "shutdown". 
```
man shutdown
```
To reboot:
```
shutdown -r now
```
To shutdown (power off):
```
shutdown -h now
```
You might have to use "sudo" if it complains about permission. 
```
sudo shutdown -h now
```

---

### Post by helpdrew on 2011-01-11
amjjawad I followed the thread you provived to restore the top and bottom panels with great sucess. I have top and bottom panels now. I fear what will hapen when I shut down
I connected an external monitor to the laptop and Ubuntu gave me additional resolutions. 1024X768 (4:3) gives me full screen on both displays. 
As far as Firefox goes I still get nothing after following your suggestions. Google-Chrome works fine

---

### Post by helpdrew on 2011-01-11
Hello zer010. THe commands you suggested work fine. Is there any way to make this happen automatically? Where can I insert the ***shutdown -h now *** command?

---

### Post by amjjawad on 2011-01-11
> **helpdrew said:**
>  amjjawad I followed the thread you provived to  restore the top and bottom panels with great sucess. I have top and  bottom panels now. I fear what will hapen when I shut down


Don't fear anything, my friend :)
Glad it worked for you.

>  I connected an external monitor to the laptop and Ubuntu gave me  additional resolutions. 1024X768 (4:3) gives me full screen on both  displays. 

So, does it mean you get the full screen ONLY when you connect the external monitor?  

>  As far as Firefox goes I still get nothing after following your suggestions. Google-Chrome works fine 

So, it doesn't work even after removing it and re-install it?


As for Shutdown, I'm trying to search and find something for you.
I found these so far (trying to find different scenarios):


[http://www.lockergnome.com/linux/2010/05/18/ubuntu-10-04-shutdown-problem-fix/](http://www.lockergnome.com/linux/2010/05/18/ubuntu-10-04-shutdown-problem-fix/)

[http://sathyasays.com/2010/12/17/how-to-fix-for-ubuntu-unable-to-shutdown-with-acpi-turned-off-due-to-a-problem-with-geforce-fx-5200-and-onboard-intel-chipset/](http://sathyasays.com/2010/12/17/how-to-fix-for-ubuntu-unable-to-shutdown-with-acpi-turned-off-due-to-a-problem-with-geforce-fx-5200-and-onboard-intel-chipset/)

[http://www.ahfx.net/weblog/160](http://www.ahfx.net/weblog/160)

Sorry, can't find more now because I have to watch a football (soccer) match on TV :)

---

### Post by helpdrew on 2011-01-13
Top and bottom panels are working most of the time. The external monitor gives me full screen size but when I disconnect it I get a less than full screen on the laptop monitor. I will estimate about 60% right in the middle.

---

### Post by amjjawad on 2011-01-14
Hi again :)
 
 For the screen resolution, please try this:
 1) [http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)
 
 2) [http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)
 
 3) [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
 
 
 
 What about the other issues? everything is okay?

---

### Post by helpdrew on 2011-01-16
I am learning that Ubuntu is Like a Box of Chocolates, You Never Know What You Will Get. Tonight I started up and I am at full screen 1024X768. Looks great. Great info you gave. I am reading the tutorial of the last link you supplied. SUper stuff.
As for other issues - Firefox still does not work but Google Chrome does. I cannot see any videos or hear music from sites like Flixi or YouTube. Tried downloading Adobe Flash but cannot get it to run. Will continue to try.

---

### Post by amjjawad on 2011-01-16
> **helpdrew said:**
> I am learning that Ubuntu is Like a Box of Chocolates, You Never Know What You Will Get. 

I believe this is the way it's with everything in life :)

> Tonight I started up and I am at full screen 1024X768. Looks great. Great info you gave. I am reading the tutorial of the last link you supplied. SUper stuff.

Impressive :)
I just did some search on google and found those links so hope you'll find some interesting stuff :)

> 
As for other issues - Firefox still does not work but Google Chrome does. I cannot see any videos or hear music from sites like Flixi or YouTube. Tried downloading Adobe Flash but cannot get it to run. Will continue to try.

I don't think the problem with Flash. You can't open Firefox to begin with.

I found some threads about Firefox:

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002)

[http://ubuntuforums.org/showthread.php?t=1215352](http://ubuntuforums.org/showthread.php?t=1215352)
Which is the thread I found the 1st link from.


I hope I was not wrong when I asked you to remove Firefox and install it again!

---

