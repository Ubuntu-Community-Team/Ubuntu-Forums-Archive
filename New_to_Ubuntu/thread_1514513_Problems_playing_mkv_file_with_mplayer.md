---
title: "Problems playing mkv file with mplayer"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by RandomP on 2010-06-21
I have all of the needed codecs installed I think that make mkv's playable in ubuntu, but the video is choppy, but the audio keeps going. 

I am using integrated video on this PC, but I do have 2.9GB of RAM and have a 2GHz CPU. I do not see why it would be so problematic.... :|

It does not seem to just be with Mplayer, VLC seems to do it too. 

Strange thing is, before I reinstalled Ubuntu 10.04 earlier this month, they played ok. (I was using 10.04 at that time too).

I will be installing 64 bit ubuntu in a little bit since I have upgraded my ram and more is on the way.

---

### Post by warfacegod on 2010-06-21
Make sure you have the "Recommended" video driver activated in Jockey. System> Admin.> Hardware Drivers.

You might also want to get this:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ep1centre on 2010-06-21
i'm having the same trouble, i have a Zotac ION N330 (dual core 1.6 atom with the ION graphics processor which is soposed to be spot on for 1080p playback) and it does the same, when i try to playback any 720p or 1080p material it just goes out of sync where audio keeps playing but video slows down!
 
i've installed all the codec packs i could think of but no difference, i've tryed other programs but i mainly use XBMC the problem is the same whatever i use to play the files!

---

### Post by RandomP on 2010-06-21
I am trying the restricted extras thing right now. Is it alright if I have Sun Java 6 installed? Since I see it installing the opensource version of Java that is in the repos...

ep1centre, my brother is using Ubuntu on his 2.4GHz Intel Core 2 Duo PC with 2GB of RAM and all of the videos work great. The question is what are the other specs on your PC. The video card or integrated graphics may not be powerful enough, or you do not have a good amount of RAM.


EDIT:
Restricted extras seem to have done nothing. The video still lags. Right now it is only doing this to one mkv file, another one I have runs very smoothly. I however do know that it is not the video.

---

### Post by acrazyplayer on 2010-06-21
The problem is if the source is "HD" or not. Most .MKVs on my old computer did exactly the same no matter what I installed. Check your cpu usage whilst playing, I bet its maxed out. If not then try installing the player "VLC", it works pretty good.

---

### Post by warfacegod on 2010-06-21
That's an excellent point. High Def can take a tremendous amount of processor time. I don't remember what the recommended minimum specs are but I wouldn't be surprised if it was at least 2 GB RAM and a mid-grade dual core.

---

### Post by RandomP on 2010-06-21
> **warfacegod said:**
> That's an excellent point. High Def can take a tremendous amount of processor time. I don't remember what the recommended minimum specs are but I wouldn't be surprised if it was at least 2 GB RAM and a mid-grade dual core.

I doubt that very much as this computer used to play the files fine and it plays some of the 720p mkv's I have without any sort of lag. Besides that when this PC ran windows it played all of the 720 and 1080p files, but it only had 512mb of RAM.

---

### Post by warfacegod on 2010-06-21
My laptop has 2 GB Crucial RAM and an Intel P4 2.8 GHz Hyper Thread CPU. High Def brings it to it's knees. It will do HD *only* if nothing else is running and Compiz is off. Which is a bad thing to try, now that I think about it.

---

### Post by RandomP on 2010-06-21
> **warfacegod said:**
> My laptop has 2 GB Crucial RAM and an Intel P4 2.8 GHz Hyper Thread CPU. High Def brings it to it's knees. It will do HD *only* if nothing else is running and Compiz is off. Which is a bad thing to try, now that I think about it.

I just checked it..... Yep, it is using 100% of the processor while playing that mkv.

I was thinking of trying to overclock this CPU to something a little higher, since the other 720p video works almost flawlessly. Also, would a graphics card not work?

I might just try and see if I can get a AMD Athlon X64 II in socket 939...

---

### Post by warfacegod on 2010-06-21
> **RandomP said:**
> I just checked it..... Yep, it is using 100% of the processor while playing that mkv.

I was thinking of trying to overclock this CPU to something a little higher, since the other 720p video works almost flawlessly. Also, would a graphics card not work?

I might just try and see if I can get a AMD Athlon X64 II in socket 939...

Even assuming you have enough cooling in your system, overclocking can only get you so much before your processor becomes unstable. It probably won't be enough to make any difference.

A better graphics card *might* help allot or not at all. Really depends on what you are using now.

From Wikipedia about the AMD Athlon X64 X2:

> On April 21, 2005, less than a week after the release of Venice and San Diego, AMD announced its next addition to the Athlon 64 line, the Athlon 64 X2.[23]  Released on May 31, 2005,[24]  it also initially had two different core revisions available to the public, Manchester and Toledo, the only appreciable difference between them being the amount of L2 cache.[25]  Both were released only for Socket 939.[26]  The Athlon 64 X2 was received very well by reviewers and the general public, with a general consensus emerging that AMD's implementation of multi-core was superior to that of the competing Pentium D.[27][28]  Some felt initially that the X2 would cause market confusion with regard to price points since the new processor was targeted at the same "enthusiast," US$350 and above market[29]  already occupied by AMD's existing socket 939 Athlon 64s.[30]  AMD's official breakdown of the chips placed the Athlon X2 aimed at a segment they called the "prosumer", along with digital media fans.[24]  The Athlon 64 was targeted at the mainstream consumer, and the Athlon FX at gamers. The Sempron budget processor was targeted at value-conscious consumers.[31]  Following the launch of the Athlon 64 X2, AMD surpassed Intel in US retail sales for a period of time, although Intel retained overall market leadership because of its exclusive relationships with direct sellers such as Dell.

---

### Post by RandomP on 2010-06-21
Might just buy a new PC soon....

---

### Post by warfacegod on 2010-06-21
In the longterm, that's almost certainly your best option. If your gong to run Ubuntu, do your homework first.

---

### Post by ep1centre on 2010-06-22
> **RandomP said:**
> I am trying the restricted extras thing right now. Is it alright if I have Sun Java 6 installed? Since I see it installing the opensource version of Java that is in the repos...
 
ep1centre, my brother is using Ubuntu on his 2.4GHz Intel Core 2 Duo PC with 2GB of RAM and all of the videos work great. The question is what are the other specs on your PC. The video card or integrated graphics may not be powerful enough, or you do not have a good amount of RAM.
 
 
EDIT:
Restricted extras seem to have done nothing. The video still lags. Right now it is only doing this to one mkv file, another one I have runs very smoothly. I however do know that it is not the video.
 
 
Well i have 4GB of ram if that's what you were asking and the processor is a dual core 1.6GHz atom chip as for the graphics side of things its Nvidia's ION processor i dont know the specs of it but i'd expect they're readly avaliable on the net, what i do know is that both the main ION and my motherboard's (for that matter) marketing points is the ability to play 1080p content smoothly which it used to on windows (not bigging that rubbish up) which as far as my diagnosis goes it rules out hardware... so that leaves something software related...
 
any ideas?

---

### Post by chamber on 2010-06-22
I have 1gb RAM in Dell Dimension E something.

MKV's play fine in mplayer for me.

---

### Post by rustutzman on 2010-06-22
To get HD (1920x1080(i or p)) to play decent on my netbook I bought and installed CoreAVC's H.264 Video Codec. You have to mess around with WINE a bit to install it but it did do the job.

Russ

---

### Post by cascade9 on 2010-06-22
> **warfacegod said:**
> That's an excellent point. High Def can take a tremendous amount of processor time. I don't remember what the recommended minimum specs are but I wouldn't be surprised if it was at least 2 GB RAM and a mid-grade dual core.

RAM didnt matter so much, and the specs will vary (as Ghz is a crappy way to meausre system speed) but without hardware video decoding (VDPAU, XvBA) the most common numbers to play HD is- single core, 3.5Ghz, dual core, 2.5Ghz.

> **RandomP said:**
> I doubt that very much as this computer used to play the files fine and it plays some of the 720p mkv's I have without any sort of lag. Besides that when this PC ran windows it played all of the 720 and 1080p files, but it only had 512mb of RAM.

Let me guess, you've got an nVidia card? Windows would probably have been using 'pure video' 

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

Pure Video runs on lower level cards than VDPAU (6 series minimum for pure vid, 8 series minimum for VDPAU). With VDPAU even gutless atoms can play HD content ;) 

> **RandomP said:**
> I just checked it..... Yep, it is using 100% of the processor while playing that mkv.

I was thinking of trying to overclock this CPU to something a little higher, since the other 720p video works almost flawlessly. Also, would a graphics card not work?

I might just try and see if I can get a AMD Athlon X64 II in socket 939...

Overclocking wont help much IMO.

Yeah, if you've got a 8 series card then it will help a lot. Check outt eh forums for how to complie mplayer to use VDPAU. If you've got an eariler card, but you do have a PCIe slot, then an upgrade + VDPAU should help a lot. If its AGP, then you will never get VDPAU going (last nvidia AGP cards were the 7XXX series). Well, you could get a PCI 8400GS, but I wouldnt.....  

You should be able to find a socket 939 athlon X2 2nd hand somewhere. The best of them is the X2 4800+......though there is the Fx-60, its faster, but a lot more expensive. I'd check your motherboard manufacturer for what CPUs it supports before you even go looking for a CPU.

---

### Post by ep1centre on 2010-06-22
cascade9, you seem to know about this subject, can you shed any light on my situation, i have a Zotac ION with a dual core 1.6GHz atom... i use XBMC to play stuff mostly but i have trying the Ubuntu built in player (mplayer?) and vlc to see if either could play my 1080p and 720p stuff but no player seems to play it properly no matter what i do.

I'm fairly windows literate but I'm quite new to Ubuntu so take it easy with technical terms please!

Thank you!

---

### Post by fooman on 2010-06-22
> **ep1centre said:**
> cascade9, you seem to know about this subject, can you shed any light on my situation, i have a Zotac ION with a dual core 1.6GHz atom... i use XBMC to play stuff mostly but i have trying the Ubuntu built in player (mplayer?) and vlc to see if either could play my 1080p and 720p stuff but no player seems to play it properly no matter what i do.

I'm fairly windows literate but I'm quite new to Ubuntu so take it easy with technical terms please!

Thank you!

here is how i have mine setup on a couple of different nvidia cards (PCI 8400gs on an old dell and a PCI-e 8800gt on this abit motherboard):

install the nvidia drivers via system > administration > hardware drivers
install the libvdpau1 package via synaptic package manager or open a terminal and type or copy/paste this command:
```
sudo apt-get install libvdpau1
```install smplayer (a nice frontend for mplayer) via synaptic or in a terminal:
```
sudo apt-get install smplayer
```after they install, open smplayer and in the toolbar, go to options > preferences...click the video tab and for "output driver", scroll down the list and choose "vdpau"

that should do it...using smplayer, 1080p content runs smoothly and uses about 5% of my cpu. :)

---

### Post by ep1centre on 2010-06-22
ohh thank you, installing vdpau worked a treat for me.... as for that sm player it looks nicer than ubuntu's standard player... how do i get rid of the standard one and make smplayer the standard ubuntu player?

thank you!

---

### Post by fooman on 2010-06-22
is this a file on your drive that you are playing?  if so,  then just right-click on the file and choose "properties"
in the properties box, click the "open with" tab.  then find smplayer in the list and put a check next to it.  close that box,  and whenever you open a file with that same file extension (.avi, .mkv,...etc) it will open with smplayer.  no need to uninstall any standard player.

hope that helps.

---

### Post by warfacegod on 2010-06-22
> **ep1centre said:**
> ohh thank you, installing vdpau worked a treat for me.... as for that sm player it looks nicer than ubuntu's standard player... how do i get rid of the standard one and make smplayer the standard ubuntu player?

thank you!

Use Synaptic to remove Totem. Pretty sure whatever player you have installed will become default after removing it.

---

### Post by ep1centre on 2010-06-23
Thanks guys, i opened my mouth before checking things out properly though, sm player only seems to do videos anyway... and besides like i said i use XBMC anyway so its a bit pointless worrying about it!
 
I am however very happy that i can finnaly play my 1080p stuff without lagg... it looks awsome!

---

