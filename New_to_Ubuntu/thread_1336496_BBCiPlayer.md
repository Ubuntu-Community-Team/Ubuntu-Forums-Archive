---
title: "BBCiPlayer"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by judith_sw on 2009-11-24
Hi,

Just wondering if anyone could advise me on the UK's BBC iPlayer ... should it run OK on my netbook with Ubuntu 9.10? 

I have an HP 2133 with VIA Chrome 9 graphics card. I tried installing it once before ... installed apparently OK, downloaded a programme, but wouldn't play. I've since done a clean install and would welcome advice on whether it is likely to work / any specific setting need tweaking.

Other specs:

Processor VIA C7-M ULV (1.2GHz) 
Memory 1Gb DDR 2 (2Gb max - one SODIMM slot) 
Graphics VIA Chrome9
Hard disk120Gb SATA (5400rpm)
Screen 8.9in (1280 x 76)

8) Thank you!

---

### Post by goldshirt9 on 2009-11-24
i run it ok on jaunty with no problems.
in fact i can run all the channels with nor problem (bbc / itv / ch4 / c5 ).
cannot run apple movies though:(

---

### Post by doug1212 on 2009-11-24
Hi,
I believe that the BBC iplayer software is windows only, so the only option is to watch in your browser while on-line. to do this you will require Adobe's flash plug-in.

Doug.

---

### Post by Cheesemill on 2009-11-24
> **doug1212 said:**
> Hi,
I believe that the BBC iplayer software is windows only, so the only option is to watch in your browser while on-line. to do this you will require Adobe's flash plug-in.

Doug.

Not true, there's been a native linux version for a while now.

---

### Post by Jose Catre-Vandis on 2009-11-24
If you want to download programmes for later use, try [get_iplayer]("http://linuxcentre.net/getiplayer")

OK, it is command line only, but you can get decent quality versions as per, if not better than iPlayer.

---

### Post by MickS on 2009-11-24
It works fine on my Acer Aspire One with Karmic and look into getting get_iplayer. It's a command line app but very  easy to use.


Mick

---

### Post by doug1212 on 2009-11-24
> **Cheesemill said:**
> Not true, there's been a native linux version for a while now.

Excellent, News to me, thanks.
Doug.

---

### Post by arochester on 2009-11-24
Also check out [http://www.tvcatchup.com/](http://www.tvcatchup.com/) - live freeview tv online and [http://www.livestation.com/](http://www.livestation.com/) tv from all over the world.

---

### Post by themusicalduck on 2009-11-24
There's a non-command line program too. You can get it from here - [http://www.bbc.co.uk/iplayer/install/](http://www.bbc.co.uk/iplayer/install/)

---

### Post by Sir Jasper on 2009-11-24
Hi arochester and any UK reader using ¨tvcatchup¨

I am interested in your recommendation, but whilst it is not a surprise that the licence agreement is so lengthy I do not like the fact that I can hardly read the light text and would need to copy and paste it into a text reader. However, WoT (Web of Trust) gives it a clean report in all four of its categories.

Any further explanatory comments, especially on practical use and experience will be most welcome.

My regards

> **arochester said:**
> Also check out [http://www.tvcatchup.com/](http://www.tvcatchup.com/) - live freeview tv online.

---

### Post by judith_sw on 2009-11-25
Hi,

Sorry about the late reply. Thanks for all the advice. I'm interested in both get_iplayer and the BBC version. Does anyone know if the BBC version for Linux is OK with 9.10? And also my graphics card VIA Chrome9?

Many thanks!

---

### Post by durand on 2009-11-25
The bbc version works fine. You can either watch shows directly from the website via flash or you can download shows and watch them later. It's exactly the same program as in windows so you shouldn't have any problems.

---

### Post by judith_sw on 2009-11-25
Unfortunately my last post didn't send properly. I downloaded BBC iPlayer, and everything seemed to go OK. However, although radio is fine, the TV playback (on play and also download) is very juddery - the pictures are totally out of sync with the sound (- which is running normally). I think flash and air are up to date, but I'm not entirely sure.

Any ideas?

---

### Post by durand on 2009-11-25
Go to System > Administration > Hardware Drivers. You may need to install some for your graphics card.

---

### Post by judith_sw on 2009-11-26
Unfortunately, the only thing that shows up for this is the Broadcom wireless driver that I have already updated. I tried to update the lib32 files yesterday, but kept being told that I had a more recent version already.

I'd really like to be able to use the BBC site, either directly or via downloads, but something is clearly wrong (i.e. picture seriously jumpy and lagging way behind the sound). When I installed iPlayer, everything seemed to load successfully. 

I found a couple of potential updates for the Via Chrome9 graphics card, but these appear to be for the chipset ... and this is where it all starts to go over my head!!! I have downloaded 2 potentially useful drivers but cannot install them:

5.74.33.86a-u904-50937.tgz
and also
via-xserver-86a-50283_src.tgz

Two problems here - firstly I don't know if they are even the right ones (as I can't find the exact model of my Via Chrome9 card), secondly I don't know how to install them. They won't unpack at the moment.

I would be **really, really grateful **for any help! In the mean time I will double-check that Adobe Air is installed properly (I suspect it isn't!). I will be able to respond to messages today as I have brought the HP 2133 to work with me. Believe it or not, this trouble-shooting will keep me sane, as my current task at work is driving me up the wall :-)

Many thanks is advance!

---

### Post by durand on 2009-11-26
Hmm, it looks like your problem is the lack of a Via graphics driver. Thats the only thing that could really cause your playback to lag like that.

Maybe you can use the deb files here: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) You need to choose ubuntu 9.04 from the dropdown. I'm not really sure what the second dropdown is about though..

---

### Post by judith_sw on 2009-11-26
Thanks for that. I think I may need to update the drivers, and it's reassuring that the ones you have identified are the same as the ones I found. If possible, could you tell me how to install the .tgz files? I have downloaded them.

In the meantime, I've realised that Adobe Air isn't installed either. I have downloaded it, but cannot install. When I type:

chmod +x AdobeAIRInstaller.bin

I'm told no such file exists. I think this may be a problem with installing .bin files. I've googled it but cannot see how to remedy this.

---

### Post by themusicalduck on 2009-11-26
If you installed the iPlayer program with Air then it should have installed properly. Chances are it's a problem with your graphics card.

If you do want to try and reinstall Air, then to use that command you need to navigate to the right directory first. If the file is on your desktop then you'll need to use the command ```
cd Desktop
``` then ```
sudo chmod +x AdobeAIRInstaller.bin
``` then to run the installer ```
sudo ./AdobeAIRInstaller.bin
```

---

### Post by judith_sw on 2009-11-26
Hi,

When I tried the chmod command I got:

chmod: cannot access 'AdobeAIRInstaller.bin: no such file or directory 

But it is on the desktop! Any ideas? This has come up in other threads, but not in exactly the same way, I don't think ...


Also, I have moved the .tgz files to the desktop. When I enter tar -xvzf filename.tgz I get:

gzip: stdin: not in gzip format

I'm clearly making some error, just not sure what!

---

### Post by themusicalduck on 2009-11-26
That's very strange.

It might be easier to find the file on your desktop, right click on it, select properties. Go to the permissions tab and check the Allow executing file as program box.

After that, try this command instead ```
sudo ~/Desktop/AdobeAIRInstaller.bin
```

edit: What exactly is the .tgz file for? The adobe air installer should be a .bin file you download from here [http://get.adobe.com/air/](http://get.adobe.com/air/)

edit: realised your talking about the graphics drivers. Not too sure why it wouldn't extract. I downloaded it and tried to right click and extract it which gave the same error.

---

### Post by Jerubaal on 2009-11-26
I've not yet tried iPlayer on 9.10, but on 9.04 I can play old iPlayer programs which I downloaded on Windoze over a year ago.

I assume that Linux iPlayer includes the standard time-limited viewing?

---

### Post by themusicalduck on 2009-11-26
This page might be worth looking it - [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

Glancing at the first couple of paragraphs, it looks like your laptop has a few problems with Karmic, and it looks like the video drivers might only work with 9.04.

But also found this - [http://www.openchrome.org/](http://www.openchrome.org/)

and if you look in synaptic, those drivers seem to be installed by default. So not too sure why they aren't already working well for you.

---

### Post by alexfish on 2009-11-26
found some links worth reading don't know if it helps here

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

 Multiple Sound Solution (ALSA w Pulseaudio)
[http://ubuntuforums.org/showthread.p...embedded+flash](http://ubuntuforums.org/showthread.p...embedded+flash)

---

### Post by judith_sw on 2009-11-26
Hi,

Thanks - the Adobe worked and then told me it was already installed! It was the persmissions issue, so I'll at least be aware of that in future.

Re. the .tgz files, these are the driver updates for the Via Chrome9 card I have. I'm hoping this will be the solution to the jerky out-of-sync playback on iPlayer ...

Just tried iPlayer again - still very jumpy, more like a slide show, but the sound is fine! wondering if I need to try 9.04 instead :-(

---

### Post by judith_sw on 2009-11-26
Still no joy unzipping the two .tgz files to update the Via Chrome9 driver. I have moved both of the files to the desktop. When I double click on them I get:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

Can anyone point me in the right direction? Sorry, I realise that this is due to my own lack of experience ... I've had a look at the links that have been sent, but this is all a bit techical at the moment :-(

---

### Post by durand on 2009-11-26
It looks like either you didn't download them completely or the file extension is wrong. Could you give me a link to where you got them from?

---

### Post by judith_sw on 2009-11-26
Yes, I got them from [www.via.com.tw/en/support/drivers.jsp]("http://www.via.com.tw/en/support/drivers.jsp")

4 drop-down boxes leading to:

Unified GFX driver for Ubuntu 9.04 (- nothing for 9.10 as yet)
Unified 2D/DRM driver source

I just tried to download again - the download manager says it's a Tar archive (gzip compressed). When I try to open with Archive Manager (default) I get a warning:

<file> could not be opened because the associated application helper does not exist. Change the association in your preferences."

Could this be the missing link??? What do I need to do in preferences?

---

### Post by durand on 2009-11-26
Right, they named it badly. Change tgz to tar for the xserver driver. The same probably applies to the other driver.

---

### Post by durand on 2009-11-26
The reason why they specify 9.04 for that driver is that 9.10 uses a new kernel and this is apparently not supported by the driver :( I think the easiest thing to do here is to just use jaunty (9.04) until a newer driver comes out.

---

### Post by judith_sw on 2009-11-26
Hi again,

Thanks for that ... looks like I'll need to install 9.05 then. I know how to do that!!! I suppose the older versions have had most of the problems corrected. I will have a go at the upgrade first though!

... the .tar extension is readable!!!
Could you tell me which command line I need to use and I'll see if it works?

---

### Post by judith_sw on 2009-11-27
Quick update ...

I installed Xubuntu 9.04 this evening and followed the step-by-step fixes. Everything worked and I can now watch iPlayer with reasonably smooth pictures and sound that is in synch.

Thanks for all your advice and help - we got there in the end! :popcorn:

---

### Post by cornelis spronk on 2009-12-06
Thanks for this thread.

I have been very happy for the last few months with how well 9.04 worked with the BBCiplayer.

After experimenting with the an early version of 9.10 in September, a gave up on it, as it gave BBCiplayer problems.  Assuming these might be fixed, I decided to make the move in December to reinstall 9.10.

Now I have been struggling for two days with several reinstallations of 9.10--using BBCiplayer to test if the sound is working properly.  It partly works, but only a certain volume control settings, and the shuddering of the sound is not totally eliminated.  Each installation gave me similar problems.  

I do most of my listening to BBC. I will reinstall 9.04 until 9.10 is fixed for BBCiplayer.  I hope we do not have to wait too long for a fix.

---

