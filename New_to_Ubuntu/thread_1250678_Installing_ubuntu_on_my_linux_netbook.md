---
title: "Installing ubuntu on my linux netbook"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by ceece on 2009-08-26
:KSI am going to install ubuntu onto my asus netbook 900 which is running on what I will guess is basic Linux. 
I ordered a cd but in the meantime I am going to try to burn my own cd ad install from that.
Questions:
1. Do I have to uninstall the LInux OS that is on my netbook first or does that get wiped out when I plug in the cd (using external cd driver):confused:
2. Will it automatically start installing onto my netbook when I put the cd in? Or do I have to open it up or extract etc??
3. Does Ubuntu have a program that will let me tether my blackberry to the netbook?
 
Thank you!!!:P

---

### Post by j.bell730 on 2009-08-26
1. During the Ubuntu installation, you can choose to either keep your current Linux installation or delete it in entirety.

2. When you put the CD in and reboot, there will be a menu and from there you can select to install Ubuntu. Nothing else is required just select an item on a menu.

3. Sorry, I don't know, maybe someone else can post?

---

### Post by earthpigg on 2009-08-26
j.bell is correct, except that:

> **j.bell730 said:**
> 2. When you put the CD in and reboot, there will be a menu and from there you can select to install Ubuntu. Nothing else is required just select an item on a menu.


before getting to that menu, you ***may*** need to change the bios settings. that is where it says 'press del to enter setup' when you ***first*** turn on the computer from power off. it may be del, it may be f12, etc... it varies, but the concept is the same.

once you enter the bios setup, you need to change the 'boot order' or 'boot priority' to put the cd drive first (if it is not already done by default by Asus at the factory).

for question 3, i suggest you make a new thread with a descriptive thread title specific to your question so the thread will attract people that are specifically knowledgeable and/or have tried to do or actually done that before themselves.

---

### Post by ceece on 2009-08-26
:PThanks Jbell and Earthpigg,
Hopefully things will install without a problem. I'm still waiting for the download to complete. It's taking longer than I thought. It could be a busy download location I chose.
 
Is there anything tricky I should know when it comes to burning it on the cd?
 
I take it that I will be installing a program on my computer to enable burning his particular download. Although I do have a cd/dvd burner already on my desktop.

---

### Post by Wehrdo on 2009-08-26
> **ceece said:**
> :PThanks Jbell and Earthpigg,
Hopefully things will install without a problem. I'm still waiting for the download to complete. It's taking longer than I thought. It could be a busy download location I chose.
 
Is there anything tricky I should know when it comes to burning it on the cd?
 
I take it that I will be installing a program on my computer to enable burning his particular download. Although I do have a cd/dvd burner already on my desktop.
Just be sure that your program can handle ISO burning.  The program I use to burn ISO images is InfraRecorder.  Just google it.  I've heard that burning at 1x speed will give you a better chance of having an intact copy, can anybody verify that?

---

### Post by earthpigg on 2009-08-26
> **ceece said:**
> :PThanks Jbell and Earthpigg,
Hopefully things will install without a problem. I'm still waiting for the download to complete. It's taking longer than I thought. It could be a busy download location I chose.
 
Is there anything tricky I should know when it comes to burning it on the cd?
 
I take it that I will be installing a program on my computer to enable burning his particular download. Although I do have a cd/dvd burner already on my desktop.

1. in the future, use the .torrent instead of the direct download. torrents are generally accepted as the preferred method of mass software distribution in the Free Software world - a well seeded torrent will always be faster than a direct download, *has a lower chance of errors that could potentially ruin your install*, is more reliable, and costs less money. anything with large amounts of community support (such as ubuntu) will almost certainly be well seeded.

2 and 3. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

the short version of that link is this - use a CD-R, and burn at very slow speed. 2x or 4x. any burner that can burn an .iso file (aka, "CD Image") will do just fine.

---

### Post by j.bell730 on 2009-08-26
After you download the ISO, you might want to check the MD5sum on it. [This]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Linux") should help you with that.

And yes, 1x will give better results.

---

### Post by ceece on 2009-08-26
Thanks All,:)
OH I hope this works!:lolflag:

---

### Post by winotree on 2009-08-27
In no way do I want to take this thread off-course, but I know you'll be more than pleased with your decision.  Look at what can be done with an original ASUS 701 with its default 4GB SSD:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3621020   1600604   1836476  47% /

so just imagine what *you'll have in store for yourself tomorrow!*  Best wishes.  ;)

---

### Post by Bigtime_Scrub on 2009-08-27
If it is Ubuntu 9.04 I think it will tether a Blackberry, It tethers my Blackjack II....but thats not 100% certainty, although I think it will do it out of the box.

UPDATE

I think it depends on the Balckberry model u use.

See this thread. [http://ubuntuforums.org/showthread.php?t=1165996](http://ubuntuforums.org/showthread.php?t=1165996)

The way I tether is just plug it into a USB port and connect with the network manager.

---

### Post by ceece on 2009-08-27
:POk I got the cd up and running and it looks like the install is working. Thanks everyone for your help!
 
Only problem..To save space, I chose to uninstall the Linux (I have a recovery cd, so hopefully I can use that if I ever want my old OS back) and just have Ubuntu as my OS. 
But I did  not consider some of the things available on the old OS like "webcam"
 
Will I have any problem using my webcam that is built into my netbook with the Ubuntu system?
 
Ceece

---

### Post by earthpigg on 2009-08-28
time to start learning to fish a bit, friend:

google search "ubuntu 9.04 webcam model-of-your-netbook" and find someone else that has already tried it.

also consult the ubuntu hardware compatibility list.

if you cannot find the answer in 10-15 minutes, then go ahead and post a *new* thread regarding that specific question with a descriptive thread title.

good luck! :D

---

### Post by ceece on 2009-08-29
Oh, I** have** been fishing Earthpig!:P  Believe me. This has been my obsession lately!

---

### Post by LewRockwell on 2009-08-29
> **earthpigg said:**
> time to start learning to fish a bit, friend:

google search "ubuntu 9.04 webcam model-of-your-netbook" and find someone else that has already tried it.

also consult the ubuntu hardware compatibility list.

if you cannot find the answer in 10-15 minutes, then go ahead and post a *new* thread regarding that specific question with a descriptive thread title.

good luck! :D

+1  for giving the OP a FISHING POLE...instead of just throwing another dead fish!


cheese will probably work fine...

.

---

### Post by ceece on 2009-09-01
Thanks everyone for helping a green ubuntu user!
I hope to get this figured out. This year, myabe :)


to lewrockwell...:(

---

### Post by earthpigg on 2009-09-01
> **ceece said:**
> Thanks everyone for helping a green ubuntu user!
I hope to get this figured out. This year, myabe :)


to lewrockwell...:(

make a new thread, specific to your blackberry tethering question. that will, hopefully, attract folks to your aid who *know about tethering blackberries*. 

(i have never tried, so i know nothing about it.)

---

### Post by k33bz on 2009-09-01
> **ceece said:**
> :POk I got the cd up and running and it looks like the install is working. Thanks everyone for your help!
 
Only problem..To save space, I chose to uninstall the Linux (I have a recovery cd, so hopefully I can use that if I ever want my old OS back) and just have Ubuntu as my OS. 
But I did  not consider some of the things available on the old OS like "webcam"
 
Will I have any problem using my webcam that is built into my netbook with the Ubuntu system?
 
Ceece

Alot of things will work right out of the box, but as stated above do some research, because some things you do need to tweek a little bit.

---

### Post by CaptainMark on 2009-09-02
> **j.bell730 said:**
> And yes, 1x will give better results.
x2, found out the hard way, sometimes people get an input/output error message, this usually means the cds a problem

---

### Post by ceece on 2009-09-02
I agree, it will take alot of tweaking, trial and error.
I will keep you all posted.
I'm thinking of reinstalling the original Linux and then reinstall the ubuntu (side by side)
That way I could use the webcam, dvd player etc, then still have the option to work with ubuntu.
Ceece:D

---

### Post by akiratheoni on 2009-09-02
I have an Asus EeePC 900 as well, the webcam didn't work out of the box (still looking for a fix, but it's not important to me) but everything else did.

EDIT: Actually my webcam was just disabled in the BIOS. Problem solved :P

---

### Post by k33bz on 2009-09-03
> **ceece said:**
> I agree, it will take alot of tweaking, trial and error.
I will keep you all posted.
I'm thinking of reinstalling the original Linux and then reinstall the ubuntu (side by side)
That way I could use the webcam, dvd player etc, then still have the option to work with ubuntu.
Ceece:D

The DVD player should work right out of the box, most webcams do as well. Just can be a pain to get your webcam working with an Instant Messenger.

---

