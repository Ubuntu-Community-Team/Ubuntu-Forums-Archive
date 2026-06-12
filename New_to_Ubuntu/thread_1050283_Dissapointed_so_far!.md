---
title: "Dissapointed so far!"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by russppt on 2009-01-25
Hi all

I thought I would give Unbuntu a go after a friend raved on about it before I bought a Mac.
Had no problem with the installation and I really like Ubuntu but so far in the first 24 hours the PC has frozen five times so I have to turn off and turn on again.  Also, I loaded up a DVD for my daughter and it wont go past the first chapter menu.  I never even had these issues with windows!
I don't want to give up at this early stage on Unbuntu, someone please inspire me?:(

Thanks.

Russell

---

### Post by mmitt on 2009-01-25
Im not a Linux expert, AT ALL, but you should try installing proprietary drivers under Applications > Add/Remove. As for crashes, I have no clue.

---

### Post by Stalker72 on 2009-01-25
Have you tried to run Update Manager?

Stalker72

---

### Post by SunnyRabbiera on 2009-01-25
Well firstly you can tell us the version you are trying out, secondly that DVD issue is probably there because ubuntu doesnt ship DVD codecs by default and the gstreamer plugins can only do so much but lets get to that later.
Anyhow what version are you using now?

---

### Post by philinux on 2009-01-25
For DVD's and codecs etc, click the medibuntu link below and . Also install vlc player for dvd's from add/remove or synaptic.

Also install ubuntu-restricted-extras.

---

### Post by Stalker72 on 2009-01-25
> **philinux said:**
> Also install ubuntu-restricted-extras.
```
sudo apt-get install ubuntu-restricted-extras
```

Stalker72

---

### Post by neotasic1 on 2009-01-25
> **russppt said:**
> Hi all

I thought I would give Unbuntu a go after a friend raved on about it before I bought a Mac.
Had no problem with the installation and I really like Ubuntu but so far in the first 24 hours the PC has frozen five times so I have to turn off and turn on again.  Also, I loaded up a DVD for my daughter and it wont go past the first chapter menu.  I never even had these issues with windows!
I don't want to give up at this early stage on Unbuntu, someone please inspire me?:(

Thanks.

Russell

Have you installed on a pc or a mac?
To play proprietory disks in linux you must install restricted drivers. These are not installed by default by Ubuntu, because such installation is illegal in some countries.
To install such drivers, follow the instructions in the desktop help menu accessed by hitting the F1 key on your keyboard. Follow the link regarding music, videos and photos. This will tell you all you need to know.
I came over to ubuntu about 2 years ago and will never go back. It is worth the effort but may take some effort to start with.

---

### Post by Dan_Dranath999 on 2009-01-25
for LEGAL REASONS, Ubuntu can't include DVD support, in the CD or in the official repositories.

You'll need to enable Medibuntu repositories [http://www.medibuntu.org/](http://www.medibuntu.org/)
(you'll get the instructions there)

and then using Synaptic, install:
**libdvdcss2**  (for Encrypted DVDs)
**ubuntu-restricted-extras** (or kubuntu-restricted-extras, or xubuntu-restricted-extras, depending on your distro)
and **w32codecs** and there you go: Multimedia ready.

(won't hurt to install **VLC **media player: that thing reads everything)

---

### Post by Dr Small on 2009-01-25
[Linux is NOT Windows](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by pi.boy.travis on 2009-01-25
How old is your computer?  How much memory do you have?  Does the freezing occur only when a certain application is running?

It can be confusing at first, but learning to use Ubuntu is very well worth it!

---

### Post by tbuss on 2009-01-25
russppt,

Sorry to hear you are having problems. It has already been mentioned but could you post what version of Ubuntu you installed. What application are you are using to play DVD's? VLC (also already mentioned) is a great media player that can handle almost any format you throw at it. Have you added the 'medibuntu' repository to your sources.list? This first part after the install can be frustrating for some users. If you are unsure how you feel about Ubuntu try the LiveCD and have a look around. You can also Dual Boot or even use virtualization to run Ubuntu on top of your other OS. Work into it at your own pace and as problems come up check back here at the forums or try the ubuntu channel on IRC (irc.freenode.net)

**I have listed some thread from here in the Forums you might find useful:**

**Comprehensive Multimedia & Video Howto**
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

**Complete Guide to Software Installation in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=781352]("http://ubuntuforums.org/showthread.php?t=781352")

**HowTO Ubuntu System**
[http://ubuntuforums.org/showthread.php?t=842307]("http://ubuntuforums.org/showthread.php?t=842307")

**HOWTO: Customize Ubuntu A-Z**
[http://ubuntuforums.org/showthread.php?t=856190]("http://ubuntuforums.org/showthread.php?t=856190")

---

### Post by russppt on 2009-01-25
> **pi.boy.travis said:**
> How old is your computer?  How much memory do you have?  Does the freezing occur only when a certain application is running?

It can be confusing at first, but learning to use Ubuntu is very well worth it!

I'm running a toshiba mx-40 laptop with 1.5 gig of ram and 1ghz procesor.  Its about 4 years old now but a good reliable machine.

Freezing has occured randomly but on two occassion when I was trying open a webcam being transmited.  The system did ask to downloads some software at this point.

Any help would be appreciated thank you.

---

### Post by russppt on 2009-01-25
Thanks for all the feedback.  I will soldier on!

---

### Post by SunnyRabbiera on 2009-01-25
> **russppt said:**
> I'm running a toshiba mx-40 laptop with 1.5 gig of ram and 1ghz procesor.  Its about 4 years old now but a good reliable machine.

Freezing has occured randomly but on two occassion when I was trying open a webcam being transmited.  The system did ask to downloads some software at this point.

Any help would be appreciated thank you.

Well again I ask what version you are running, if its 8.10 there are many reports of stability issues

---

### Post by russppt on 2009-01-25
Will do.
Starting to see what Ubuntu is about!
Thank you

---

### Post by SunnyRabbiera on 2009-01-25
> **russppt said:**
> Will do.
Starting to see what Ubuntu is about!
Thank you

Well ubuntu can be a great OS once you get it cooking, just keep in mind that some versions work better then others but thats from my personal experiences.
But good thing is that Ubuntu has a community, a community that works with you a good percent of the time

---

### Post by russppt on 2009-01-25
Hi Sunny
Thanks for the feedback again.  I am running 8.10.
Looks like this is somthing I can't rush!

---

### Post by russppt on 2009-01-25
Thank you.
will look at these.

---

### Post by russppt on 2009-01-25
> **mmitt said:**
> Im not a Linux expert, AT ALL, but you should try installing proprietary drivers under Applications > Add/Remove. As for crashes, I have no clue.
Ok, I am less of a Linux person than you.
What is a proprietry driver?
Cheers
Russell

---

### Post by russppt on 2009-01-25
> **Stalker72 said:**
> Have you tried to run Update Manager?

Stalker72
First thing I did.
Thanks for taking the time to reply.
Russell

---

### Post by SunnyRabbiera on 2009-01-25
> **russppt said:**
> Ok, I am less of a Linux person than you.
What is a proprietry driver?
Cheers
Russell

Propriety drivers are requested by some video cards, it could be tghe reason for your crashes as some cards dont like us that much.
And as I see you are using 8.10, if it gives you too much trouble give the previous version 8.04 a shot.
There are not a whole lot of differences between the two, you wont loose any real security or anything if you install 8.04 over 8.10.

---

### Post by russppt on 2009-01-25
> **neotasic1 said:**
> Have you installed on a pc or a mac?
To play proprietory disks in linux you must install restricted drivers. These are not installed by default by Ubuntu, because such installation is illegal in some countries.
To install such drivers, follow the instructions in the desktop help menu accessed by hitting the F1 key on your keyboard. Follow the link regarding music, videos and photos. This will tell you all you need to know.
I came over to ubuntu about 2 years ago and will never go back. It is worth the effort but may take some effort to start with.
Working with a pc.
Thanks for the advice.
Russell

---

### Post by SunnyRabbiera on 2009-01-25
> **russppt said:**
> Working with a pc.
Thanks for the advice.
Russell

The PC vs Mac debate is kind of moot here, as Ubuntu can work on both...
But its the type of Mac or PC is where it matters, your brand/ make/ model of PC and what it has inside will tell us what we need.

---

### Post by sneeks on 2009-01-25
if you are really having problems with 8.10,try the lts 8.04 hardy heron version,as most of the probs are now ironed out and is very stable me thinks.

---

### Post by russppt on 2009-01-25
> **Dr Small said:**
> [Linux is NOT Windows](http://linux.oneandoneis2.org/LNW.htm)
Point taken!
Regards
Russell

---

### Post by OutOfReach on 2009-01-25
Are you aware of what kind of video card this machine has?

---

### Post by Talon2 on 2009-01-25
> **russppt said:**
> 
Looks like this is somthing I can't rush!

Pre-loaded systems you can rush:

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

Systems that were bought before a person knows to keep Linux compatibility in mind may have an issue or two that requires attention from the kind folks here.

---

### Post by Sealbhach on 2009-01-25
> **russppt said:**
> 
What is a proprietry driver?
Cheers
Russell

Proprietary means it's not Open Source. It's supplied by the hardware vendor but the code is closed and is their "property". An example would be the Nvidia drivers supplied by Nvidia for graphics cards.

They're still free to download and use, so don't worry about that.


.

---

### Post by kaldor on 2009-01-25
After reading some posts, I have a few small suggestions.

1) Open the terminal (Applications>Accessories) and type ```
sudo apt-get install hardinfo
``` I am not entirely sure that this is the right command, but it is very useful. After you install it, type "hardinfo" in the terminal to bring up all of your specs.

2) Ditch Intrepid Ibex and try out Hardy Heron. Some people have complaints with Intrepid. Hardy is an LTS, meaning it is a stable release and is longer supported. I consider non-LTS releases to be test OS's.

3) Use VLC media player for your movies. Everything works fine for me on this :)

I need to say I love your attitude toward Ubuntu! You are not complaining about things like many do, instead you try to fix things and learn. That is a great way to learn about Ubuntu and GNU/Linux in general. If you enjoy your Ubuntu experience but want to learn more about computers or Linux, try out other distributions such as Slackware.

Good luck :)

---

### Post by vividia on 2009-01-25
Hey I know you're struggling through the tweak process.  I just wanted to give some hope.  I only started using ubuntu in June.  I had little to no experience with Linux.  I was able to find help I needed in this forum without having to register until earlier this month.  I have learned a lot in that time.  These are some of the nicest people on the 'nets.  

It'll all be ok.  The effort may seem like more than its worth but it gets better and leads to a far richer computing experience.

Take Care

Michelle

P.S. Hardy Heron, or 8.04, would be the better choice since it is LTS as as someone mentioned before.  It will be supported until April 2011.  8.10 will only be supported till April 2010.  Intrepid is also less stable than Hardy though I haven't really had any major issues to report.

---

### Post by t0p on 2009-01-25
> **kaldor said:**
> I consider non-LTS releases to be test OS's.

Really?  I don't.

---

### Post by lswb on 2009-01-25
> **t0p said:**
> Really?  I don't.

Yes, beginning with 8.04 we can now consider LTS releases to also be "test releases" :)

---

### Post by russppt on 2009-01-25
> **OutOfReach said:**
> Are you aware of what kind of video card this machine has?
Hi
Says ATI on the plastics, not sure where to look on Ubuntu to find out!

---

### Post by russppt on 2009-01-25
> **Talon2 said:**
> Pre-loaded systems you can rush:

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

Systems that were bought before a person knows to keep Linux compatibility in mind may have an issue or two that requires attention from the kind folks here.
Never seen so much support.  Dowloading 8.04 as we speak.
Thank you

---

### Post by russppt on 2009-01-25
> **lswb said:**
> Yes, beginning with 8.04 we can now consider LTS releases to also be "test releases" :)
ok.  I know I am new to this, but was it LTS?

---

### Post by snova on 2009-01-25
> **russppt said:**
> ok.  I know I am new to this, but was it LTS?

Yes, I believe so.

---

### Post by Captain_tux on 2009-01-25
> **russppt said:**
> ok.  I know I am new to this, but was it LTS?

What does Google tell ya when you search for LTS in relation to Ubuntu...?

---

### Post by pi.boy.travis on 2009-01-25
> **russppt said:**
> ok.  I know I am new to this, but was it LTS?

LTS stands for long term support.  Most Ubuntu releases are supported with updates for 18 months, but LTS releases get three years of support on the desktop, and five years of support on the server.

---

### Post by jakupl on 2009-01-25
> **t0p said:**
> [QUOTE="kaldor"]I consider non-LTS releases to be test OS's.Really?  I don't.[/QUOTE]

I do.

---

### Post by tbuss on 2009-01-25
> **Captain_tux said:**
> What does Google tell ya when you search for LTS in relation to Ubuntu...?

I was wondering how long this thread would go on before someone dropped the 'G' bomb. 

**russppt,**

You will need to keep this in mind after you install 8.04 should you want to upgrade to 8.10 in the future.

> By default Ubuntu 8.04 LTS will not offer a upgrade to 8.10. This is because the 8.04 LTS version is a long term support release and 8.10 is a regular release. **Upgrades from 8.04 LTS to 8.10 are fully supported,** of course, and easy to enable.

[INDENT]You can directly upgrade to Ubuntu 8.10 from Ubuntu 8.04 LTS. (see [[COLOR="RoyalBlue"]UpgradeNotes)[/COLOR]]("https://help.ubuntu.com/community/UpgradeNotes")

The upgrade will not be presented by default because 8.10 is not a Long Term Support (LTS) release.

Be sure that you have all updates applied to Ubuntu 8.04 LTS before you upgrade.

Before upgrading it is recommended that you read the release notes  for Ubuntu 8.10, which document caveats and workarounds for known  issues in this version. (see [[COLOR="RoyalBlue"]Release Notes)[/COLOR]]("http://www.ubuntu.com/getubuntu/releasenotes/810")[/INDENT]

Keep this link handy if you decide you want to upgrade to 8.10
--> [[COLOR="RoyalBlue"]Network Upgrade for Ubuntu Desktops (Recommended)[/COLOR]]("https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended)")

---

### Post by blueridgedog on 2009-01-25
The simple first steps to getting media working on a new install:

Documented at: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

```
sudo apt-get install Ubuntu-restricted-extras
```

Documented at: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
sudo apt-get install ttf-xfree86-nonfree
```

The above installed the non-free restricted extras and the tools needed to play most any file type. The Medibuntu page is essential reading.  These commands can be copied and pasted into a terminal.  Paste in a terminal is Shift-Control+V.

---

### Post by Captain_tux on 2009-01-27
> **tbuss said:**
> I was wondering how long this thread would go on before someone dropped the 'G' bomb. 



I think a little initiative goes a long way, dontcha think?

---

### Post by boof1988 on 2009-01-27
> **Captain_tux said:**
> I think a little initiative goes a long way, dontcha think?

JUST BECAUSE YOU ARE ABLE TO SEARCH ON THE INTERNET AND FIND WHAT YOU WANT, DOES NOT MEAN THAT EVERYONE ELSE CAN.

:p So please keep this in mind before you say things like "I think a little initiative goes a long way, dontcha think?".  I am sure there are many things that a person who isn't able to find things online (as good as you) can do other tasks far above your level.  In other words, don't make assumptions about other people. :p

---

### Post by Captain_tux on 2009-01-27
> **boof1988 said:**
> JUST BECAUSE YOU ARE ABLE TO SEARCH ON THE INTERNET AND FIND WHAT YOU WANT, DOES NOT MEAN THAT EVERYONE ELSE CAN.

:p So please keep this in mind before you say things like "I think a little initiative goes a long way, dontcha think?".  I am sure there are many things that a person who isn't able to find things online (as good as you) can do other tasks far above your level.  In other words, don't make assumptions about other people. :p

And initiative is what drives a person to do things [whatever they may be] better than the next, just as how you describe... thanks for making my point for me :)

Use your words cautiously, Sir... the only assumption made here is that you think I can find things online (or do anything else for that matter) better than anyone else.

Good day.

---

### Post by blueridgedog on 2009-01-27
Ok, philosophy here:

Actually, I think it is more interesting than searching and skill.  Some people know that almost everything is available online and that they can find it if they persist and are clever at searching.  They are net people.  I am one.  I can find the proverbial four leaf clover almost every time.  I have been on the net since day one (before HTTP). 

Others however are not native net citizens.  To them, when they are in a conversation and hear something they do not understand, they ask "what is that".  When they are in a forum and see LTS mentioned, they ask "what is that".  The reality is that this is normal and is the way humans interact.  Bless those that are still engaged enough to ask, to engage others rather than to assume or soldier on alone.  I think that is the core difference.  They think of the forums as conversations among people, but the net hardened citizens see it as an iterative research project.

I could never imagine telling someone to Google something in real life while chatting, and I hope I can keep my forum posting to the same level of humanness.  As we become more net integrated in our life, I wonder what other conflicts will arise out of the the differences between real life and net life.

That is not to say that I won't say something like:  "I searched Google on your issue and came up with the following links" or "I found this older thread in the forums that seems to match your issue"

---

### Post by vividia on 2009-01-28
> **blueridgedog said:**
> Ok, philosophy here:

Actually, I think it is more interesting than searching and skill.  Some people know that almost everything is available online and that they can find it if they persist and are clever at searching.  They are net people.  I am one.  I can find the proverbial four leaf clover almost every time.  I have been on the net since day one (before HTTP). 

Others however are not native net citizens.  To them, when they are in a conversation and hear something they do not understand, they ask "what is that".  When they are in a forum and see LTS mentioned, they ask "what is that".  The reality is that this is normal and is the way humans interact.  Bless those that are still engaged enough to ask, to engage others rather than to assume or soldier on alone.  I think that is the core difference.  They think of the forums as conversations among people, but the net hardened citizens see it as an iterative research project.

I could never imagine telling someone to Google something in real life while chatting, and I hope I can keep my forum posting to the same level of humanness.  As we become more net integrated in our life, I wonder what other conflicts will arise out of the the differences between real live and net life.

That is not to say that I won't say something like:  "I searched Google on your issue and came up with the following links" or "I found this older thread in the forums that seems to match your issue"

I'm quoting all of what was said because I can't decide what to throw out.  I agree with this.  I'm a net citizen who can indeed find the proverbial four-leaf-clover.  I get e-mails from friends and family asking me to find something they can't and its takes me moments.  And yes, I've been online since we had a 300-baud modem. 

When someone asks a question in a forum that is designed for people to come and ask questions, telling them to google something is self-defeating.  Think of an information desk.  What if someone went there for information and was met with a weary sigh and told to go use some database to find an answer?  An answer the person at the information desk could easily give?  Think that person is going to use that resource again?  Or have a favorable description of it?

---

