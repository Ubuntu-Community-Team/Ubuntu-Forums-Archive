---
title: "Setting up a tv tuner card"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by kevsimo on 2011-01-29
Hi, I am battling my way through as a very new linux user to get my computer working as I was used to under Windows. I have managed most things, but getting tv set up has completely defeated me.

I have been trying to set up mythtv under ubuntu 10.10 I think I have it installed correctly, but that the problem lies with my TV tuner card which I believe to be dvb-t.

My computer is a medion akoya md8870 but I cannot find the exact type of card.

Raking through tons of forums I have got as far as listing this in the terminal.

07:00.0 Multimedia controller [0480]: Philips Semiconductors Device [1131:7231] (rev ca)
    Subsystem: Creatix Polymedia GmbH Device [16be:0008]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>

However, now I am lost, following further forum info nothing seems to be found or recognised. I really do need a very beginners guide to finding the correct firmware/drivers and how to install them, everything I find is way beyond me and I long for a windows style installation wizard unfortunately!

All help appreciated. Thanks

---

### Post by robsoles on 2011-01-29
Welcome to UF.

Please don't post all in blue, it hurt my eyes trying to make it all the way through your post.

Try MeTV on the PC with the tv tuner card in it. It is likely that the card has been picked up by the system and I found that where I had to configure stuff in MythTV to use my tuner card MeTV just opened using it already.

MeTV is in the Ubuntu Software Centre, please let me know if it doesn't just start playing TV to you when you open it.

---

### Post by kevsimo on 2011-01-30
(Sorry about the blue font, not sure how that happened!)

Thanks for the reply, I have installed and run Me TV, it immediately gives me an error "There are no DVB devices available"

So I'm back where I was before, I know that there is a tv tuner card installed, it appears unrecognised or unsupported.

The details previously are the best I could manage to find.

Thanks in advance for further advice.

---

### Post by wep940 on 2011-01-30
I've tried searching the web on the 2 pci ids you showed (Phillips as [COLOR=black]1131:7231, and Creatix Polymedia GmbH Device 16be:0008). It appears that the device driver is specifically needed for the Creatix Polymedia device at 16be:0008. However, I did not find a driver yet. You may want to try searching the net as well with 16be:0008 linux in the search string. I tried to check the Creatix site, but you need to know the card name/number to continue searching there.[/COLOR]
 
EDIT:  okay, according to a document in the Creatix support site FAQ, that id of 1131:7231 is a Creatix [FONT=Arial-BoldItalicMT][SIZE=2][FONT=Arial-BoldItalicMT][SIZE=2]
***CTX 1924 ***card.  It only lists a driver for Windows 7.  I'll do some more net searching using CTX 1924 linux in the string and see what turns up.
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by robsoles on 2011-01-30
I am using a DVB-T card that just got picked up by the system and MeTV already had access by the time I was trying.

In "System"->"Administration"->"Synaptic Package Manager" I found linux-firmware-nonfree of which the description says it contains non-free firmware used by Linux kernel drivers and it goes on to say that this currently contains firmware for DVB cards.

Install that and give it another whirl please.

---

### Post by robsoles on 2011-01-30
Sorry: If you can't find it then check that you have 'restricted' and 'multiverse' repositories enabled in your sources list. Make sure 'universe' is checked as well - I will be stunned to hear if 'main' isn't checked :lol:

In Synaptic Package Manager: "Settings"->"Repository Manager" will open "Software Sources", first tab "Ubuntu Software" is the one to look at.

Does it get the card 'up' ?

<edited>meant to mention: You may need to restart the machine before the nonfree firmware will 'kick in'.</edited>

---

### Post by kevsimo on 2011-01-30
Thanks to both of you.

Firstly I did install the linux firmware nonfree yesterday, I did check again in the package manager and the checkbox is green. Have rebooted etc just to double check and still get the same error message "There are no DVB devices available"

I took the back off the computer (its an all in one so not easy to get at things")

Wep940 you are absolutely correct it is a Creatix card but it is CTX 1920_V1.1.1.2

I cant find any linux drivers, but in truth from what I have read even if I do ,I am struggling to know how to install them!

Thanks again

---

### Post by kevsimo on 2011-01-30
I did get this info from a pdf on the creatix site.

CTX1920 is a highly integrated Mini Card  using the PCIe bus signals
and supports analog and digital TV.
 
Chipset: NXP TDA18271HD/C2, NXP SAA7231NE

Connector: Hirose U.FL-R-SMT-1
TV System: Supports DVB-T and TV broadcasting PAL, B/G/D/K/I & SECAM L/L’,

Maybe I can use a supported driver from the linuxtv site list? but as I say I'm very much out of my depth now.

---

### Post by Stephen Morgan on 2011-01-30
Whenever I reinstall I have to install a driver for my USB DVB-T tuner, which I do by going to System > Administration > Additional Drivers.

---

### Post by kevsimo on 2011-01-30
Thanks for that, I was optimistic, but it through up and update for a graphics card but otherwise no luck

---

### Post by wep940 on 2011-01-30
Hummmm, if you look at the 1st pdf file on the Creatix support site, it maps to what I gave you. Either way around, at least you've ID'd the card. I'm afraid I'm not familiar with using tv tuners on a PC, so I've really exhausted what I could search for for you. I hope continued searching on the net will turn up something.
 
EDIT: Be sure you are looking at the correct card. When I do a search on the net for Creatix CTX 1920, it says it is a modem, not a tuner card.  ALso, try contacting Creatix support to see if they know if anyone has a linux driver for the 1924 (not the 1920) at [EMAIL="ssupport@creatix.de"][EMAIL="support@creatix.de"]support@creatix.de[/EMAIL][/EMAIL]

---

### Post by kevsimo on 2011-01-31
Well thanks  for all your work and help. I will indeed try the support team.

Otherwise I guess I will need to look for swapping it for something that is supported.

Thanks again.

---

### Post by kevsimo on 2011-02-01
Final plea for any TV experts - I got this reply from Creatix support

I am sorry but we don't offer linux drivers.

The card has a Philipps/NXP/Trident SAA7231 chip inside.

Any final offers how to get this working with Ubuntu 10.10, very much appreciated.

---

### Post by wep940 on 2011-02-01
I *think* I've seen mention of Linux drivers and some of the saa chipsets.  I'll try checking the net again.

---

### Post by lisati on 2011-02-01
> **robsoles said:**
> Please don't post all in blue, it hurt my eyes trying to make it all the way through your post.


Fixed. :)

---

### Post by robsoles on 2011-02-02
> **lisati said:**
> Fixed. :)

Thanks Richie, I hope I'm not being too informal ;)


I took a look at linuxtv.org and I couldn't find a dead match for "SAA7231" but I found near matches like this: [www.google.com/search?q=site%3Alinuxtv.org+creatix]("http://www.google.com/search?q=site%3Alinuxtv.org+creatix")

I tried 'nxp' and saa7231. saa7131 appears to be the nearest match, if you are desperate enough I will do my best to help you get it to fly in your system.

I halfway expect that the saa7131 firmware/driver is already a part of 2.6.x Linux and trying it will just be frustrating but I expect you want to keep trying stuff and we can't be sure we won't get your DVB working without trying.

---

### Post by wep940 on 2011-02-02
I did notice that as well.  For the OP's card, all I could find was page after page of it not working, people looking for a driver, and someone trying to compile a driver from source only to find out the driver isn't complete from the person who was writing it.
 
Since I've exhausted everything I know to look at, I'm dropping out now.  I hope someone like robsoles or one of the other responders can help you.
 
Best of luck!

---

### Post by rajeev1204 on 2011-02-02
Are you using a digital tv broadcast ? And is your card capable of playing digital broadcasts?

Me tv is only for digital tv and it wont work for analog devices.

The greatest software for analog tv is tvtime in the software center. Its small and lightweight and easy to set up.

Try it.ANd please report back.And please try the latest ubuntu version 10.10 if you already are not.

[URL="http://www.spinics.net/lists/vfl/msg42371.html"]
[/URL]

---

### Post by robsoles on 2011-02-02
> **rajeev1204 said:**
> ...

The greatest software for analog tv is tvtime in the software center. Its small and lightweight and easy to set up.

Try it.ANd please report back.And please try the latest ubuntu version 10.10 if you already are not.

...

Your enthusiasm is super, the OP can't even start their card because they can't find a driver for it.

Do us all a favour kevsimo, install Tvtime Television Viewer from the repository and confirm that it doesn't happen to supply a driver (somehow) for your card.

Nb.: I installed it and I'm still trying to get it to actually tune a channel on my DVB Card, it selects composite and s-video just great but I can't see where to select a channel yet.

---

### Post by rajeev1204 on 2011-02-02
> **robsoles said:**
> Your enthusiasm is super, the OP can't even start their card because they can't find a driver for it.

Do us all a favour kevsimo, install Tvtime Television Viewer from the repository and confirm that it doesn't happen to supply a driver (somehow) for your card.

Nb.: I installed it and I'm still trying to get it to actually tune a channel on my DVB Card, it selects composite and s-video just great but I can't see where to select a channel yet.

Is this sarcasm?

---

### Post by realzippy on 2011-02-02
....crossreading some german VDR/linux forums,this creatix TV card
will not work under linux.

---

### Post by rajeev1204 on 2011-02-02
I suggest filing a bug on launchpad with command ubuntu-bug linux and also trying one of the plain vannila kernels from kernel.org as newer kernels add support for many newer dvb cards.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by robsoles on 2011-02-02
> **rajeev1204 said:**
> Is this sarcasm?

Mmmh, you can take it that way if you like. I see how "Your enthusiasm is super" could seem like it's in a mean spirit but I genuinly hope kevsimo installs the app you've suggested and confirms that it doesn't happen to make the tuner work.


In all seriousness, I had a DVB-T card for quite some time before the Analog channels in Australia started advertising Digital TV (more than once a day in the middle of the night) and, I can't get TvTime to allow me to select a channel in my DVB-T tuner - it selects the 'DVB' input and I can select the two external inputs the card has but how just where is the channel selector in this thing?

Thanks.

---

### Post by rajeev1204 on 2011-02-02
> **robsoles said:**
> Mmmh, you can take it that way if you like. I see how "Your enthusiasm is super" could seem like it's in a mean spirit but I genuinly hope kevsimo installs the app you've suggested and confirms that it doesn't happen to make the tuner work.


In all seriousness, I had a DVB-T card for quite some time before the Analog channels in Australia started advertising Digital TV and, I can't get TvTime to all me to select a channel in my DVB-T tuner - it selects the 'DVB' input and I can select the two external inputs the card has but how just where is the channel selector in this thing?

Thanks.

TVtime is only for analog devices as far as i know, so i just want him to specify if he is using an analog broadcast and see if it works. I have an saa 7134 card so thought i could pitch in.

Anyways, he should file  a bug and also try the new plain vanilla kernels .

---

### Post by robsoles on 2011-02-02
I am not sure unsupported hardware is a reportable bug.

[http://ubuntuforums.org/showthread.php?t=872554](http://ubuntuforums.org/showthread.php?t=872554) suggests to me that [Perastikos]("http://ubuntuforums.org/member.php?u=562831") had a DVB-T card going with TVtime and they obviously found how to change channels. I got the sense from that thread that they were tuning it via terminal (maybe having it scan the channels), please tell me: Is that how you have to tune it once it's got a channel list?

---

### Post by rajeev1204 on 2011-02-02
> **robsoles said:**
> I am not sure unsupported hardware is a reportable bug.

[http://ubuntuforums.org/showthread.php?t=872554](http://ubuntuforums.org/showthread.php?t=872554) suggests to me that [Perastikos]("http://ubuntuforums.org/member.php?u=562831") had a DVB-T card going with TVtime and they obviously found how to change channels. I got the sense from that thread that they were tuning it via terminal (maybe having it scan the channels), please tell me: Is that how you have to tune it once it's got a channel list?

Of course , if a piece of hardware does not work on ubuntu, you can file a bug on launchpad and in this case since its a kernel module thing they will forward it upstream to the linux kernel team .

Well, dmesg lists out a bunch of info for a tuner and it also includes actual info on how to do trial and error tuning assigning different tuner numbers until you find something in case the eeprom on a tuner is missing.Its a painstaking process though and you will spend nights trying to hit gold.I had this issue with an unbranded card so i replaced it with a pinnacle one.It worked fine later on.

For DVB  devices metv is  a better option and if you want a full blown PVR you can use myth tv.Tvtime can display satellite or digital broadcasts as it accepts it as input  but it only tunes analog signals as far as i know.

In kev's case filing a bug will greatly enhance his chances of getting it supported in the next kernels.

Thanks for the perastikos link, i have to definitely try that out, though i never wanted to record tv hence i use tvtime.
cheers :)

---

### Post by wep940 on 2011-02-02
For what it's worth, everything I read on the net about the OP's card indicate that a LOT of the work was done in software, not in the hardware on the card.  Also, I have yet to find anyone with  a working driver for the OP's card.

---

### Post by robsoles on 2011-02-02
Sorry to say it, kevsimo, but it looks to me like you should wrap that card up in gift wrapping paper and give it to someone who prefers Windows.

Writing a bug report may influence somebody, with the time to do so, to source a card using the chipset in question and beat the problems that have stopped others from being able to produce a working firmware or driver for it BUT it's not worth waiting for if you want to see/record TV on your PC sooner than later.

I imagine you've found some listings (and mentions) of DVB-T (and old analog) cards that are fully supported in Ubuntu/Linux whilst trying to get that one going - before buying a new one check out the second hand market for them.

@rajeev1204: MeTV records streams and reads the EPG info, it is as near to a full blown PVR as I require.

---

### Post by wep940 on 2011-02-02
robsoles - couldn't agree more - the op would definetly be better off with a supported card - hope they check the list.  Also, couldn't agree more on the driver is part of the kernel so post a bug on launchpad.  Contrary to what rajeev1204 stated, it currently is not a kernel module, and therefore there is no bug to report.  What should be done is to post in the "future wants" list for support of the card, but I wouldn't keep my fingers crossed either - there are too many variations of all of these cards to include support for all or most of them.  It's kind of like the Broadcom wireless - a couple of years ago it seemed everything came with Broadcom wireless, and no linux drivers to support them.  So all the work was done to support them as best as possible because of the large installed base and requests for help on the forum.  This tvtuner is a completely different animal from that.
 
So, as I said, I couldn't agree with you more!  You're right on target with your suggestions!

---

### Post by rajeev1204 on 2011-02-03
> **wep940 said:**
> robsoles - couldn't agree more - the op would definetly be better off with a supported card - hope they check the list.  Also, couldn't agree more on the driver is part of the kernel so post a bug on launchpad.  Contrary to what rajeev1204 stated, it currently is not a kernel module, and therefore there is no bug to report. 
 



This is incorrect ( without trying to sound rude ). There is no tv tuner card which comes with official support under linux.Most of the ones which work are due to having similar chips inside one of which is the popular philips saa series tuners.And also depending on hardware available for testing.Cards which work are 'known' or confirmed by users to work on ubuntu or linux.

A wishlist is like an enhancement or feature request , for example lets say the tuner works, but there is no tvout feature working , that is a wishlist.A piece of hardware not working on linux is a bug and a report can be filed.


Here is a similar bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624) 

The user's card does not work and he files a bug/ report. Some one from the ubuntu kernel team asks him to test with the newer kernels to see if its been fixed.

Since this is a continuing philips saa 7* series chipset it is possible to get it working on future kernels if bug shows more activity as users will search for it and comment on it.

Depends on bug 'heat' . 

Just search for dvb and you will find many such bugs ( or reports as i say) filed because some tuner or other does not work.

---

### Post by robsoles on 2011-02-03
Make bug heat all you like - OP wants TV on his PC now, not when somebody can make it work ***eventually*** when people have been trying for a couple of years now.

Pity if nobody ever mentions it and pursues it with the developers, just for the sake of managing yet another tuner card, but hedging that bet and just waiting for it won't put TV on your PC overnight.

I won't post to this thread on this side topic again.

---

### Post by wep940 on 2011-02-03
Ditto - the OP just wants it to work - not filing a "bug" report and waiting who knows how long for something that will probably never happen.

---

### Post by rajeev1204 on 2011-02-03
> **wep940 said:**
> Ditto - the OP just wants it to work - not filing a "bug" report and waiting who knows how long for something that will probably never happen.

  It may not work for him now but reporting a bug might help others with this card in the future.And possibly him.

Anyways, its for the OP to decide if he wants to pursue it further. 

Good luck.Ill leave the thread to you guys .

---

