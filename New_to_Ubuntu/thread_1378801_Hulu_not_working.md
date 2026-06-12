---
title: "Hulu not working"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by klemperal on 2010-01-11
Every time I click on a video I want to watch on hulu I get an error message saying; "Sorry, we are unable to stream this video.  Please check your internet connection and try again."  

The weird thing is...
(1)  Flash is working just fine
(2)  I'm not using a proxy or trying to access hulu from outside the US

Please let me know if you have any idea what the problem might be.

---

### Post by DamenW on 2010-01-11
Is this a new problem?  Do you have a good steady line with your ISP?  I get that error at times and it can be on hulu's end,  if you wait 30 seconds and reload do you still get it?

---

### Post by Tiberion on 2010-01-11
Does Youtube work and other flash intensive sites?

---

### Post by klemperal on 2010-01-11
> **DamenW said:**
> Is this a new problem?  Do you have a good steady line with your ISP?  I get that error at times and it can be on hulu's end,  if you wait 30 seconds and reload do you still get it?

Yes, this is a pretty new problem--about a week or so now.  No, waiting 30 seconds doesn't allow me to watch--I get the aforementioned error message everytime.

---

### Post by klemperal on 2010-01-11
> **Tiberion said:**
> Does Youtube work and other flash intensive sites?

Yes, flash works fine with everything else.

---

### Post by DamenW on 2010-01-11
If your on wireless try a wired connection, if that is not involved try axing your streaming plug-in, i thing you used flash and reinstall it.  Just remember to install it from a repository instead of from the web if you can help it (will help it to update when updates are available)

---

### Post by marshmallow1304 on 2010-01-11
> **klemperal said:**
> Every time I click on a video I want to watch on hulu I get an error message saying; "Sorry, we are unable to stream this video.  Please check your internet connection and try again."  

The weird thing is...
(1)  Flash is working just fine
(2)  I'm not using a proxy or trying to access hulu from outside the US

Same here.  I first noticed it last night.  No *Office* for me. :(

Edit: Updated Flash to latest 64-bit prerelease.  No dice.

---

### Post by MooPi on 2010-01-11
I have the same issue , just checked BUMMERS.

---

### Post by klemperal on 2010-01-11
> **DamenW said:**
> If your on wireless try a wired connection, if that is not involved try axing your streaming plug-in, i thing you used flash and reinstall it.  Just remember to install it from a repository instead of from the web if you can help it (will help it to update when updates are available)

I'm using a wired connection and I reinstalled flash from the repo, but still no luck.

---

### Post by adam814 on 2010-01-11
I'm also having the same issue.  Interestingly enough it still works running Windows Firefox under Wine.  I tried to fool it with User-Agent Switcher in native Firefox with no luck.  I'm guessing it just doesn't quite give the exact one needed.  Either that or hulu requires you to accept 3rd-party ad cookies just to watch their videos.

---

### Post by MooPi on 2010-01-11
Is everyone using the latest Firefox ? Mine was just updated.

---

### Post by adam814 on 2010-01-11
Update:  Tried switching User-Agent in Firefox under Wine to see if I could make it not work impersonating a Linux browser.  It still works.  So much for the quick-fix idea.

---

### Post by aquabanianskakid on 2010-01-11
I'm having the same problem. I tried reinstalling the flash drivers (64bit) and still no dice. It does work in a windows virtual machine though. The most I can find on the Hulu site is help topics suggesting you have at least version 10 of flash... which I do.

---

### Post by klemperal on 2010-01-11
> **MooPi said:**
> Is everyone using the latest Firefox ? Mine was just updated.

My whole system is up to date.  By the way, I'm running 64 bit 9.10--is everyone else who is getting this error also running 64 bit Ubuntu?

---

### Post by aquabanianskakid on 2010-01-11
I'm also using 9.10 64bit. Firefox 3.5 and 3.6pre as well as Chrome. I've found similar postings throughout the forums and it appears this is affecting 64bit systems... I assume specifically the 64bit flash plugin.

---

### Post by aquabanianskakid on 2010-01-11
Update: Deleted all instances of the flash plugin. Then I reinstalled it through synaptic. It now partially works in Chrome but not Firefox. I can't seem to pause videos or select anything within the window.

---

### Post by zenxi on 2010-01-11
> **klemperal said:**
> Every time I click on a video I want to watch on hulu I get an error message saying; "Sorry, we are unable to stream this video.  Please check your internet connection and try again."  

The weird thing is...
(1)  Flash is working just fine
(2)  I'm not using a proxy or trying to access hulu from outside the US

Please let me know if you have any idea what the problem might be.

have you tried using this alpha version of flash x64 from this ppa?
make sure you dont have any other versions of flash installed, also look under ~.mozilla/firefox*/plugins some times it installs there

```

**sudo add-apt-repository ppa:sevenmachines/flash**** && ****sudo apt-get update && sudo apt-get install -y flashplugin64-installer**
```also if your not already check out the mozilla teams ppa
for the daily builds
```
sudo add-apt-repository **ppa:ubuntu-mozilla-daily/ppa && **sudo apt-get update && sudo apt-get upgrade -y
```for security updates only 
```
sudo add-apt-repository **ppa:ubuntu-mozilla-security/ppa && sudo apt-get update && sudo apt-get upgrade -y**
```

---

### Post by slick_nick on 2010-01-11
Another fully updated 64bit Karmic user having problems...
Neither Chrome nor Firefox have worked for at least a couple of days. Hulu Desktop will work until the first commercial break, then it breaks.

Edit: Found post #11 here, if it helps: [http://www.uluga.ubuntuforums.org/showthread.php?t=1378352&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1378352&page=2)

---

### Post by zenxi on 2010-01-11
> **slick_nick said:**
> Another fully updated 64bit Karmic user having problems...
Neither Chrome nor Firefox have worked for at least a couple of days. Hulu Desktop will work until the first commercial break, then it breaks.

Edit: Found post #11 here, if it helps: [http://www.uluga.ubuntuforums.org/showthread.php?t=1378352&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1378352&page=2)

bah found this [http://www.hulu.com/support](http://www.hulu.com/support) 
"
          **Software Requirements**

          To enjoy videos at Hulu, you will need the following software installed on your computer:      

[LIST]
[*]Internet Explorer 6.0 or above, Firefox 1.5 or above, or Safari 2.0 or above
[*]JavaScript and Cookies must also be enabled
[*]Adobe Flash Player 10.0.22 or above
[*]Microsoft Windows XP SP2 or later, Macintosh OS X or Linux
[/LIST]
           In addition, you will need an internet connection with sufficient bandwidth. Our videos stream at 480Kbps or 700Kbps, and we'll adjust our stream based on your bandwidth, but we recommend a downstream bandwidth of 1,000Kbps or higher for the smoothest playback experience. You can test your downstream bandwidth at [http://www.speedtest.net]("http://www.speedtest.net/"). Once there, click on the yellow pyramid on the map (if none of the pyramids are yellow, select one that is closest to your geographic location). This will initiate a speed test. Once complete, your downstream bandwidth is displayed in the "Download" box near the top of your screen. 
      Some of our videos now come in a 1,000 Kbps, H.264, 480p stream. You can recognize these streams by the 480p Hi-Res button that will appear in the lower right of the player. To watch these high-resolution streams, you'll need to upgrade to [Flash Player 10.0.22]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") or later. We recommend a downstream bandwidth of 1,500Kbps for the smoothest playback experience.      
      You'll also need Flash Player 10.0.22 or later to watch the 720p clips in our HD Gallery. Those are encoded at 2,500Kbps, and we recommend a downstream bandwidth of over 3,500Kbps to stream those. You can also pause the video and allow the streams to buffer before playing."


but i have 10.0.42.34 install

---

### Post by zenxi on 2010-01-11
i found a work around that may hold you over for now [http://www.fancast.com/](http://www.fancast.com/) it basically has the same streams as hulu
EDIT never mind thats broken to.

---

### Post by zenxi on 2010-01-11
hulu embeded player is working

---

### Post by zenxi on 2010-01-12
ok i was able to get it working by going into firefox and the right corner and select the little plugin symbol while your on one of hulus videos, then selected the adobe flash player dropdown box, then clicked search and chose adobe flash player installed and it worked its magic!

---

### Post by ubun_two on 2010-01-12
Anyone came up with good solution for this?  

I am on Karmic 64bit with full update.

---

### Post by adam814 on 2010-01-12
I'm also running Karmic 64-bit using the alpha-version 64-bit flash plugin.

---

### Post by LowSky on 2010-01-12
I have run into the same problem. Hulu works on 32bit Ubuntu just fine, doesn't work in Firefox on 64Bit.

Oddly Hulu Desktop is running just fine on 64bit. I have no idea why. It isn't flash thats the problem, or Firefox. It has to be something Hulu has done on their end.

---

### Post by clhsharky on 2010-01-12
HI

I have same problem as of late. Karmic-64, Firefox-3.5-7, 64-Adobe flash ,and the same problem with Chromium.

Although Hulu works in Vbox with

Crunchbang-32 with firefox 3.x.
And
Lucid-64.firefox 3.5-7, 64-Adobe flash
and
XPsp3, Explore-8, firefox 3.5-7

So how can it stream in Vbox but not on Main system?

Sharky

---

### Post by LowSky on 2010-01-12
No idea why Virtualbox is working>???

Best thing to do is email hulu support and ask them to fix it.

[http://www.hulu.com/support/contact](http://www.hulu.com/support/contact)

---

### Post by ApplachianHikes on 2010-01-13
Actually, it is a flash plugin issue. I removed the 64bit flash plugin, and then installed the 32 bit plugin, and it works as it should.

I'd also mention that other sites are sometimes affected. For instance, Youtube's player seemed to leave black space around the right and left sides of the player, causing me to lose an inch or so of viewing area. Fullscreen did work, however. I even tried using Adobe's latest flash from their PPA, and it still did not work.

At any rate, that's a solution that works. I'd still contact Adobe about this. I had other problems with it as well. High CPU usage, RAM usage, and my laptop even overheated while having multiple flash windows open... a first. However, with the 32 bit version, I'm having no problems at all.

---

### Post by gdimike on 2010-01-15
**I had the same problem, but it just went away.** 

I am using Ubuntu 9.10 64-bit, which I keep up to date. Flash in Linux has always been a pain in the neck for me on install or upgrade.

I could watch Hulu videos yesterday, but this morning all videos were unavailable on Hulu and NBC. Youtube videos worked, but anything "commercial" would not play. Hulu recommended clearing the browser cache and restarting the browser. (This happens often).  Usually that works, but today I tried several times with no joy.  Rebooting the system and clearing the browser cache gave no joy. It did remind me of why I changed my desktop from Windows to Linux.

huludesktop and Boxee did not work either.

So after some reboots and browser cache clears, pointing huludesktop at the 64-bit flashplayer (I use the 32-bit version in Firefox), searching for others with the same problem,  I decided to report the problem to Adobe. In the middle of filling out the fricking problem report, flash started working again on Hulu. I don't know why.

Does anyone know what's going on here?

**When in doubt, wave a dead chicken over it.**

Mike Goldberg, who needs a good laugh now, so he will watch *30 Rock*.

---

### Post by Redsunz on 2010-01-16
I'm using Ubuntu 9.10 with latest 64 bit version of flash 10.0.42.32.
Hulu no longer plays in the browser but I am able to watch Hulu by installing the Hulu desktop application on Hulu's site. Plus I can use my remote with it.

---

### Post by Laidbacklux on 2010-01-19
Found a solution that worked for me:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888)

For 64-bit 9.04, click on the october update and follow the directs.

Firefox, Chrome now play hulu!

---

### Post by klemperal on 2010-02-09
Just in case anyone was wondering about the above poster's solution, it is to install the 32bit version of flash.  Anyone have any good news about the 64bit version of flash?

---

### Post by daniell59 on 2010-02-09
Mine is working fine. I am not sure which version of flash that I installed. How can I make that determination?

Thanks

---

### Post by klemperal on 2010-02-09
If you didn't specifically install the 64bit version of flash, then your using the 32bit version.

---

### Post by rayburn0 on 2010-02-10
I am running a 32-bit system and having problems as well. From all the posts I've read, it looks like the problem is in Firefox 3.5.7 implementation of flash. I have another computer running Firefox 3.0.5 and flash seems to be working there.

Is anyone having a problem with Firefox 3.0.5 and flash?

---

### Post by adam814 on 2010-02-10
That sounds like a different issue.  The one described here isn't that flash doesn't work at all, rather that it works for every site except hulu.com.

I can say it happens in Firefox 3.6 as well as Google Chrome.

---

### Post by Linsteadborn on 2010-02-10
Are you getting this error code C00D36C4? Were you able to resolve it since you made this posting?

---

### Post by derrick81787 on 2010-02-10
> **klemperal said:**
> Just in case anyone was wondering about the above poster's solution, it is to install the 32bit version of flash.  Anyone have any good news about the 64bit version of flash?

I downloaded the 64-bit Flash alpha a long time ago, and it has worked perfectly for me.  I was a little nervous about installing alpha software, but from what I can see, it's just as good as regular 32-bit flash, and probably better than most other alternatives.

---

### Post by SickNick on 2010-02-11
Ok to confirm my results...

I had flash 64bit alpha installed on my ubuntu 9.10 and was getting the same error.

I removed it from the folder that i dropped it into and installed flash-installer from the synaptic package manager, this is the 32 bit version of flash that uses ndiswrapper to work. 

I went to hulu, and magic, it worked  :D

---

### Post by Foxcow on 2010-02-11
Too all of the 64-bit users out there:


Hang on to 64-bit flash!  If you installed it correctly, Hulu is the only thing that does not work.  I solved the problem by installing Hulu desktop which works beautifully!


You can get the deb from here:

[http://www.hulu.com/labs/hulu-desktop](http://www.hulu.com/labs/hulu-desktop)

---

### Post by SickNick on 2010-02-11
A bit of an update, 64 bit flash definitely was a bit more stable, the 32 bit works smooth but at times if I switch tabs all of the flash windows open would just go gray and just play back the sound. 

Another thing I discovered last night. While I had 32 bit plugin installed. I Installed Boxee Beta for 64 bit Ubuntu, which is a beautiful media center. I went to the Hulu plugin, and I got the same error I was getting with the 64 bit flash plugin :(

---

### Post by Eredeath on 2010-02-24
I was having the same problem and what I did was go to Tools>Manage Content Plug-ins in the Mozilla Menu.On the plug-ins in use page i selected the Flash player and updated it. And now it works.

---

### Post by Boynas on 2010-05-26
If you go to this website:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

It will load the flash plugin settings.

Its been reported that when HULU changed to the new player this new player is using the old player's settings.

Try going to "Website storage settings" and remove all the sites (to be in the safe side) or if its a big deal for you to reset the "per website settings" try removing at least:

flash.quantserve.com
player.hulu.com
[www.hulu.com](www.hulu.com) 

and obviously anything that "smells" like hulu.

Then, make sure that in "Global Storage Settings" you have "third party whatever" enabled and also at least 10k storage at least. I think that the new hulu player settings require 8k... I just set it to 100k.

This have worked for a lot of people, but I've seen other computers still having problems. 

What kills me is that you can watch the ads, but not the show, it just freezes like if it was waiting for your input but there are no dialog or anything.

Hulu desktop player works great though, something you might want to try in the mean time.

---

