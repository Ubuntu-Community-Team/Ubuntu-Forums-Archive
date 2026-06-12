---
title: "Some n00b-ish Video Questions"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by embiggened.badger on 2009-08-23
So, to confirm that Ubuntu Linux hates me, it crashed at least three times this evening. One of these crashes was actually at the exact moment I clicked the "Submit" button here on the Forums.

At the time, I was in the middle of writing a detailed post with the following questions:

(1) Why is Adobe Flash performance on this machine so horrible? Any site with embedded Flash graphics or video looks like total crap. It's definitely not the video card (512 MB ATI Radeon X1950 Pro) or lack of RAM (2 GB). Does it have anything to do with an inability to use 2D hardware acceleration?

... which ties into my second question ...

(2) How do I regain the features and functionality of my video card in Ubuntu? I tried following the instructions - located [here]("https://help.ubuntu.com/community/RadeonDriver") and [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") - to the letter, and ended up doing more damage to my rendering abilities than I could have anticipated. I had to roll back to the pre-configured drivers that are automatically installed along with Ubuntu. Is there some way to perhaps get Catalyst Control Center or ATI Tray Tools to run within the Linux environment?

I'm about ready to wipe my PC clean and start over from scratch ... but with Windows XP. There's no way I'm trying Ubuntu again until I figure out how to correct these issues. Any ideas?

---

### Post by mikewhatever on 2009-08-23
Well, ATI was notorious for providing bad or no support for linux drivers, and while the trend seems to be towards improvement, it may take some time. I hope you understand that having powerful graphics cards without good drivers is pretty much useless.
There seems to be a driver for your card at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx), try that or use what works for you.

---

### Post by embiggened.badger on 2009-08-23
> **mikewhatever said:**
> There seems to be a driver for your card at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx), try that or use what works for you.

I could try that, but doesn't that fly in the face of the tutorial to which I linked earlier? The original author of that article made it very clear that the installation of any drivers which weren't provided by the open-source community was a terrible idea.

---

### Post by twright on 2009-08-23
You might want to try the LTS release of Ubuntu (8.04) as that still works with the older ATI driver which supports loads more cards (support for many relatively new cards been dropped). The situation is the same on Windows but as the old version still works (for now) not many people have noticed.

---

### Post by embiggened.badger on 2009-08-23
> **twright said:**
> You might want to try the LTS release of Ubuntu (8.04) as that still works with the older ATI driver which supports loads more cards (support for many relatively new cards been dropped). The situation is the same on Windows but as the old version still works (for now) not many people have noticed.

Hmmm. This might be worth a shot. Thanks, TW. However, do you think this would alleviate any of the problems with Adobe Flash's poor performance, or is this mainly a solution for the loss of functionality that I referred to above?

---

### Post by sandyd on 2009-08-23
the poor performance is becasue of your video card drivers.
if downgrading to 8.04 fixes your video card drivers, it will mean that your flash player should work properly again.

---

### Post by twright on 2009-08-23
> **embiggened.badger said:**
> Hmmm. This might be worth a shot. Thanks, TW. However, do you think this would alleviate any of the problems with Adobe Flash's poor performance, or is this mainly a solution for the loss of functionality that I referred to above?
If your video drivers suck then flash will suck as a result :-) . Flash does a lot of things badly performance wise anyway (well, they make flash games run fast but not videos) whatever you are running it on and is often misused so tends to make simple tasks very graphics intensive which can be extremely painful. On my other laptop I actually have similar problems thanks to ATI's disloyalty to its own customers so I might put that one back on hardy myself (hopefully in the 3ish years whilst hardy is still supported the open source drivers will improve enough to be more usable).

---

### Post by embiggened.badger on 2009-08-23
Thanks guys! This 'downgrade' to 8.04 doesn't sound like much of a 'downgrade' at all, haha. I think I might give this a shot.

Coincidentally, would it matter if I maybe tried a different variant of Ubuntu? I've had Kubuntu (KDE + Ubuntu) recommended to me by a friend who also happens to be a gamer (and thus has a true appreciation for graphics cards).

---

### Post by rednano12 on 2009-08-23
Kubuntu, is an option, as are all other linux distros. However, KDE has gone through a major overhaul in the last year or two, and you either love it/hate it. It has some pretty eye candy, but so does Gnome. I find vanilla Ubuntu simple to use. It works great for me, and does everything I need.

---

### Post by alexlafreniere on 2009-08-23
> **embiggened.badger said:**
> 
Coincidentally, would it matter if I maybe tried a different variant of Ubuntu? I've had Kubuntu (KDE + Ubuntu) recommended to me by a friend who also happens to be a gamer (and thus has a true appreciation for graphics cards).

The drivers provided in Ubuntu and Kubuntu are exactly the same, as they most likely will be with most other Linux distros. And if your friend truly has an appreciation for graphics cards, he has an nVidia card, which are supported on the Linux platform much better than ATI's cards (sorry ATI fans). 

Flash video sucking is another issue entirely - that's a result of the Flash player for Linux being very immature. But don't worry - it is being actively developed. So this isn't specific to your hardware, and there isn't much that you can do about it. See this link: [http://xkcd.com/619/](http://xkcd.com/619/)

---

### Post by alexlafreniere on 2009-08-23
Also, what Flash player are you using? If you are using Gnash, or anything other than the official Adobe player, I reccomend switching to the official one, which in all honesty is far superior to everything else out there, even though it isn't open source.

---

### Post by embiggened.badger on 2009-08-23
> **alexlafreniere said:**
> And if your friend truly has an appreciation for graphics cards, he has an nVidia card, which are supported on the Linux platform much better than ATI's cards (sorry ATI fans).

Yeah, I've been hearing that a whole lot lately. I was under the impression ATI had opened themselves up to Open Source ever since AMD bought them out, but what I've seen over the last few days makes me question that assessment.

> **alexlafreniere said:**
> Flash video sucking is another issue entirely - that's a result of the Flash player for Linux being very immature. But don't worry - it is being actively developed. So this isn't specific to your hardware, and there isn't much that you can do about it. See this link: [http://xkcd.com/619/](http://xkcd.com/619/)

I saw that the other day and didn't get the joke. Now that I've spent a few hours with Linux, I get it. It's amazing how these things come full circle sometimes. Haha. :mrgreen:

> **alexlafreniere said:**
> Also, what Flash player are you using? If you are using Gnash, or anything other than the official Adobe player, I reccomend switching to the official one, which in all honesty is far superior to everything else out there, even though it isn't open source.

Er ... I'm not sure? The app that I downloaded originally was "SWFdec." How do you install and use the official Adobe player in Linux? I was under the impression the only way to install it was through the usual .exe format used in Windows.

---

### Post by sandyd on 2009-08-23
NOW i know whats wrong!
```

sudo apt-get remove swfdec
sudo apt-get install flashplayer-nonfree

```
should sort you out.

or go to adobe's site and download the deb. (yes there IS a version for linux on adobe's site)

---

### Post by embiggened.badger on 2009-08-23
I just tried those commands you posted Carlee. Here's what I get.

In response to "$ sudo apt-get install flashplayer-nonfree" I receive:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-nonfree.In response to "$ sudo apt-get remove swfdec" I receive:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec

I also tried downloading and installing the .deb version from Adobe just now. Here's what I got:

> Package: adobe-flashplugin
Status: Error: A later version is already installed

I'm certain that I removed this earlier. I tried running a search through the Add/Remove option under Applications, and what I found didn't work, so I removed it ... What's the deal?

---

### Post by sandyd on 2009-08-23
ive lost my ability to speel aparently
its
flashplugin-nonfree
not flashplayer-nonfree
silly me.

---

### Post by sandyd on 2009-08-23
i feel like posting isntructions to cover the version directly from adobe's site too, so...

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
sudo dpkg -i install_flash_player_10_linux.deb
sudo apt-get -f install

```

---

### Post by embiggened.badger on 2009-08-23
No worries, m'dear.

> **carlee said:**
> flashplugin-nonfree

I just tried the corrected command and something definitely installed. Let me close out Mozilla and try a few sites to see if it improves matters at all.

**Update:** Gah. Flash-animated sites still resemble Refried Crap. Backgrounds are all washed out, frame-rates are pathetic, and embedded controls don't work. What am I not doing right?

---

### Post by sandyd on 2009-08-23
theirs something definately wrong
open up firefox
and type in about : plugins. (one word, but i can't stick it together, either forum will turn that into a emotion.

give a screenshot or copy and paste.

---

### Post by embiggened.badger on 2009-08-23
**[FONT=Verdana][SIZE=2]Here's the whole thing, just in case:[/SIZE][/FONT]**

---------

**Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Demo Print Plugin for unix/linux**

 File name:  libunixprintplugin.so The demo print plugin for unix.   MIME Type Description Suffixes Enabled    application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **VLC Multimedia Plugin (compatible Totem 2.26.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

[B]------

Edit:[/B] Can somebody PLEASE tell me why Firefox keeps randomly quitting? It crashed on me for the fifth or sixth time a few minutes ago. No error message, no warning sounds, nothing.

**Edit:** The hits just keep on comin' ... Now I can't send or receive messages in Pidgin without having it "magically disappear" (i.e. crash).

---

### Post by embiggened.badger on 2009-08-24
No more takers on these bizarre issues I've been facing, huh?

Quick synopsis for anyone just joining the discussion:

(1) Adobe Flash performance is terrible in Mozilla Firefox.
(2) Can't locate appropriate video drivers or control software (e.g. Catalyst).
(3) Apps randomly crashing/disappearing in mid-use.

Any help any of the experienced Linux vets here can provide will be very welcome. Thanks guys.

---

### Post by Bartender on 2009-08-24
Buy an Nvidia graphics card.  

The ASUS EN8400GS is a good example if you're not a gamer.  I've put 8400GS's in two completely different Ubuntu PC's and they work fine.  It's a fanless PCI-x card, goes for about $30.  You plug it in, turn Ubuntu on, make sure you're connected to the internet, go to "Hardware Drivers", ask it to look, it reports back that you need an Nvidia driver, you "Enable", it gets the driver, you're good to go.

That or keep fighting bad drivers...

---

### Post by decoherence on 2009-08-24
Hi there!

First, to temporarily address the video card issue, please go to System > Preferences > Appearance, click the Visual Effects tab and select "None." See if this stops the incessant crashing.

Now to get Flash going, try

```
sudo apt-get remove swfdec-mozilla
sudo apt-get install flashplugin-nonfree
```

restart Firefox and see how things go.

Finally, to get a better idea of what the situation is with the video card, please type
```

sudo lshw -C video
```

and post the output here.

---

### Post by embiggened.badger on 2009-08-24
> **Bartender said:**
> Buy an Nvidia graphics card.  

Yep, I'm starting to actually regret having an ATI at this point. I bought it ages ago so I could play 'Oblivion' with HDR + AA, and it's all been downhill since (including its performance in 'Oblivion').

If it helps, I actually have dual nVidia GeForce 6600GTs in storage, equipped for SLI. Do you think it would help at all if I switched over to those? They should still be good; just have to circulate the dust a bit, haha.

> **decoherence said:**
>  Finally, to get a better idea of what the situation is with the video card, please type
```
 sudo lshw -C video
```and post the output here.

Thanks Dec! I'll do this as soon as I get home. (I'm at my office, at the moment.)

---

### Post by embiggened.badger on 2009-08-24
Good evening, once again, folks. I'm proud to announce that, after wiping my HDD and reinstalling from scratch, I am now using Ubuntu v9.04 exclusively. I absolutely love it so far.

This still leaves the need for tracking down effective video drivers. Specifically, I need drivers for an **ATI Radeon X1950 Pro** graphics card.

@ decoherence: I figured I would go ahead and try the command you listed earlier, even though I'm starting fresh. Here are the results:

> *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV570 [Radeon X1950 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV570 [Radeon X1950 Pro] (secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress cap_list
       configuration: latency=0Where do I begin searching for drivers?

If it would help my efforts at all, I also have twin **nVidia GeForce 6600GT** graphics cards (SLI-ready) that I can use. I would prefer to stick with my ATI Radeon, however, as this has more built-in memory and is a far more recent model (though still quite outdated by today's standards).

**Update:** Just thought I would point out that I tried viewing a few pages with embedded Adobe Flash content a moment ago ... and it worked! Frame-rate was still noticeably low, which suggests to me a continued need to find appropriate drivers for my graphics card, but it's good to know that Flash didn't necessarily butcher web content this time around. (My previous install was ... a bit wonky, shall we say.) I'm going to try and load up a few YouTube videos and see how those work.

**Update 2:** Mixed bag of results on YouTube. Many of the videos I sampled ran with crystalline clarity and great frame-rates, but some were a bit jerky. This may have something to do with their original upload quality, however. Still, the point is: Flash works (or at least appears to work)!

---

### Post by Windows Nerd on 2009-08-24
Hopefully more Ati cards will be supported better when Karmic is released. I have an Intel Card and it works fine. 

Scott

---

### Post by embiggened.badger on 2009-08-25
Good morning, folks.

Under the circumstances - that is, running Linux for the first time on a three-year-old ATI card - I've decided it may be time to look into a new graphics card. Thus, an nVidia-based chipset is a must-have.

[http://www.circuitcity.com/applications/SearchTools/item-details.asp?EdpNo=4111742&CatId=28](http://www.circuitcity.com/applications/SearchTools/item-details.asp?EdpNo=4111742&CatId=28)

This one, at the moment, is at the top of my list. It appears to balance performance with its heavily discounted price. What do you guys think? Would this be worth picking up for an Ubuntu v9.04 build?

**Edit:** Before anybody says anything, I do realize that the memory type is GDDR2, rather than the newer, faster GDDR3. However, this is a bit closer to my price point - and come on, an entire GB of memory? That's pretty slick. Still, let me know if I'm barking up the wrong tree, here.

**Edit: **I think I just found another really great option.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130297](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130297)

GDDR3 memory, higher clocks all around ... and it's $40. Add to this the fact that several people are saying the card is actually mislabeled - supposedly it features 512MB rather than the 256MB listed - and this is looking like a pretty darn nice deal. Thoughts?

---

### Post by Bartender on 2009-08-25
You get 2 DVI ports with the 9500 card.  That might be handy.  But the 9500 will pull more power than the 8600.  Is your power supply up to it?  Can your PC deal with the extra cooling requirements?

---

### Post by embiggened.badger on 2009-08-25
> **Bartender said:**
> You get 2 DVI ports with the 9500 card.  That might be handy.

That sounds promising. What use do you suppose I could get out of a second DVI port? (I'm only running a single monitor at the moment, an Acer 22" wide-screen.)

> **Bartender said:**
> But the 9500 will pull more power than the 8600.  Is your power supply up to it?

I think so. My PC runs on a 480w PSU. (It's a very odd number, I know.) Also, my older Radeon card required its own power connection for the attached fan system, so that's probably a good indication that I have enough reserve power.

> **Bartender said:**
> Can your PC deal with the extra cooling requirements?

Most likely, yes. It's a sturdy 100% aluminum case from Lian-Li and has some ridiculous number of high-speed fans.

Do you suppose the 9500 would be a better deal than the 8600? If so, I just found out that the Best Buy store five minutes from my apartment has the 9500 in stock for the same price as either CircuitCity.com or NewEgg.

**Edit: **Also, notice that the 9500 GT is using GDDR2 memory, not GDDR3. I think it may be an older model.

**Edit 2:** Hey again, Bar. I did some digging for statistics on the nVidia GeForce 9500 GT chipset. I found two things in a critical review that are directly related to what you asked above.

> "The first thing to point out on the GeForce 9500 GT is that it is a single slot solution with a cooling fan that is actually quiet during use.  The second thing to notice is that the GeForce 9500 GT doesn't need any additional power as the maximum thermal design power (TDP) is just 50W for the entire video card. Since the x16 PCI Express slot can handle ~75W of power the GeForce 9500 GT has ample power from the PCIe slot." - [Legit Reviews]("http://www.legitreviews.com/article/760/1/")

---

