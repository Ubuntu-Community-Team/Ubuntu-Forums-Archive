---
title: "Dvd player stuttering on play back ."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-19
Hi
My DVD player is stuttering badly on playback ,i have downloaded another player M player, but this is just the same as the one that came with the ubuntu install . Can someone put me on the right track to fixing this problem .
Thanks .

---

### Post by redseventyseven on 2009-01-19
Hi Gary,

In my experience DVD playback is best with Totem (which is the default movie player installed in Ubuntu) but using a different engine to the one that's installed by default.

The one that's installed by default is GStreamer - the other one is called Xine. You can get the other engine from the Synaptic Package Manager - it's called totem-xine. You may have to uninstall the other one (totem-gstreamer) first. That certainly used to be the case in older versions of Ubuntu but I've read from some sources that you can have both at once now.

If you get stuck, try googling "totem dvd xine ubuntu" or something like that for more information.

---

### Post by mdewet on 2009-01-19
VLC did it for me, on my system it works better than totem & m player, but I think user experiences differ on different systems..still worth a try

You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.

```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

---

### Post by garrydog on 2009-01-19
Hi
Downloaded Totem Xine ,and unistalled Gstreamer ,the dvd playback is still stutering .
Downloaded VLC player with the same results .
I have tryed the DVD on windows on my other hard drive and it works fine ,so i think the DVD player unit is OK .

---

### Post by redseventyseven on 2009-01-19
OK, the next thing to try is to see whether you have the codecs from the Medibuntu repositories installed.

These codecs are not included in the default Ubuntu install because they constitute a legal grey area. In some countries they are not legal or protected by copyright, in some countries they are illegal to include in a distribution but legal to go and fetch yourself, and in some countries they are totally legal.

Visit [www.medibuntu.org](www.medibuntu.org) for more information.

---

### Post by jburrell on 2009-01-19
Garry, do you mean by your DVD stuttering on playback that it gets to a certain point and then stops/freezes but the timer is still counting?  If so I have the same problem and I'm using Totem, the player that came with 8.10.  

What happens to mine is that I start a video file and it plays for about 4 - 6 minutes and then it starts freezing up on me.  

Is this similar to what you're experiencing?

---

### Post by garrydog on 2009-01-19
No the DVD plays OK but its as though it is stoping and starting ,every fraction of a second .it also affects the sound .

---

### Post by garrydog on 2009-01-19
Sorry Redseventyseven been onto that site ,but I don't know what to look for .

---

### Post by philinux on 2009-01-19
Have you got your video driver installed ok. System>admin>hardware drivers (intrepid)

---

### Post by redseventyseven on 2009-01-19
Ok, no problem - have a read of the section entitled "Repository HowTo". It gives instructions on how to get these codecs set-up on your system. Read it carefully, though - don't rush it. Don't expect to skim through it in 30 seconds. Maybe 10-15 minutes should be about right.

Essentially the "medibuntu repositories" are libraries of codecs, bundled up as packages that can be installed using Synaptic Package Manager. Repositories are the collections of software packages that you get software from. Synaptic Package Manager is a tool which enables you to do this. The Add/Remove programs tool is another - essentially it's a simplified version of Synaptic. There are a bunch of repositories (with a fairly extensive collection of packages in them) which are set up in Ubuntu by default - however due to the legal grey areas which I mentioned earlier, Medibuntu is not one of them.

If you get stuck there are plenty of threads on these forums already with good advice for getting your codecs set up. There are also plenty of guides on blogs which are fairly easy to follow. Unfortunately there are also plenty of guides which aren't particularly sympathetic to beginners - my advice is if you find one guide a bit impenetrable, go back to your google results and try another one.

Some guides may ask you to use the terminal - don't be afraid of it! In many cases it's more convenient because it's easier to give exact instructions. For example it's easier to give the instruction "Open a terminal and type [command]" than it is to say "Click on the System Menu at the top of the screen, then Preferences, then scroll down to..." - especially since the graphical interface is completely customisable (e.g. either you or the instructor might have put the menu at the bottom of the screen or be using Ubuntu in their native language). Terminal commands are standard throughout (generally speaking).

Good luck!

---

### Post by garrydog on 2009-01-19
Yes i think the driver is installed OK .

---

### Post by MrKlean on 2009-01-19
If it's a copy you made...burned yourself, it might have to be burned at a slower speed.  I don't burn my dvd's faster than 3-4x...no matter what speed it can go.

---

### Post by garrydog on 2009-01-20
Yes it is a copy but it will run OK on windows .I have downloaded codec from medibuntu repositories but the problem is still the same .If I move the pannel with the top bar ,the screen go,s mad and all the pictute breaks up, runing normaly the screen go's black every half a second .

---

### Post by lukjad on 2009-01-20
garrydog, could you tell us the specs of your computer? I didn't see any mention of it. (Although I may have missed it.)

---

### Post by garrydog on 2009-01-20
> **lukjad007 said:**
> garrydog, could you tell us the specs of your computer? I didn't see any mention of it. (Although I may have missed it.)
    description: Desktop Computer
    product: Aspire SA90
    vendor: Acer

---

### Post by lukjad on 2009-01-20
Wow. :shock: That's a lot of info. Could you give us a slightly trimmed version, RAM, CPU (processor), GPU (Video card), hard drive, and estimated age of the PC?

---

### Post by garrydog on 2009-01-20
Hi
Sorry about that ,the computer is 12 months old ,Genuine Intel(R) CPU 2160 @ 1.80GHz,
1gig ram,80gig hard drive,card is ATI RV610 audio device [Radeon HD 2400 PRO].
Is that better .
Thanks .

---

### Post by MrKlean on 2009-01-20
It wouldn't hurt to reburn it slower...it might be yer problem....it's yer decision ; )

---

### Post by lukjad on 2009-01-21
Much better, thanks. Okay, I just wanted to check that it wasn't the age of the machine that was the problem. Hmmm... I have had lots of problems with playing DVDs on Hardy, but I've been told that it's just my old computer. 

When you play these DVDs, is there another program running as well? Maybe if you shut down every other program, these movies would play better? Also, do you have trouble only when playing a DVD, or is it any media file, or just some media files?

---

### Post by garrydog on 2009-01-22
I have tryed runing them with nothing runing ,always the same ,discs will read on the player ,photos ect .Do you think that changing the drive would do any good .

---

### Post by lukjad on 2009-01-22
Maybe, but first, I would like to know if the video clips that are stored on your computer play badly as well, or if it's only DVD's.

---

### Post by miluns on 2009-01-22
This could be a DMA conflict.

Try reading this 
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

I have a Atapi dvd on a Toshiba laptop and this fixed it right up.


Mike

---

### Post by garrydog on 2009-01-25
> **miluns said:**
> This could be a DMA conflict.

Try reading this 
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

I have a Atapi dvd on a Toshiba laptop and this fixed it right up.


Mike
Hi
Thanks for all your help ,the problem is now solved ,I saw a post on this web site ,saying that the 3D effects may cause this .turned them off everything OK .
Thanks .

---

### Post by starcannon on 2009-01-25
Nevermind, I see now its solved.

---

