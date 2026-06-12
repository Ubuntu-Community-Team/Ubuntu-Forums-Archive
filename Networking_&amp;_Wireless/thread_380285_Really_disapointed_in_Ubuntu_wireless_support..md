---
title: "Really disapointed in Ubuntu wireless support."
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Don Carcharo on 2007-03-09
Let me start by saying that I'm primarily a Mac guy, I've been one since about 1993. I also use Windows daily and manage a Windows 2003 server. My experience with Linux is limited at best. I've got a Fedora VPS server and know enough to do most basic things vis WHM/Cpanel. Clearly I favor doing things via the GUI, I even vnc into my servers and would rather sudo nautilus and gedit things than try fumbling through the CLI. The point is I guess I'm a Linux noob by most accounts.

With this in mind, Ubuntu has been my first real stab at trying to run Linux on the desktop in about 5 years. Everyone has been praising it so much that I had to see what all the fuss was about. And so far I have been surprised. It's nice. Nice enough that I've opted to replace an in house Windows 2003 server (used only for light hosting and educational purposes) with Ubuntu server + ububtu-desktop. And that's where things start falling apart. This server has to use a wireless connection, it's just not possible any other way. And from what I've found Ubuntu's wireless support is, well, awful.

I've got three USB wireless B adapters (Linksysy, Belkin, Lucent) none are recognized. I've also got a Belkin PCI wireless G card. That one I was able to get working several times by adding the Alternate install CD-ROM to my repository (again I have no Internet access otherwise) and installing the madwifi drivers. But then as soon as I do get network access and update my system (edgy) I lose Wifi. This has happened about three times this week and as of this morning I can't even get it to come back. So I've tried NDISWrapper which I was able to get off the Edgy Alternate CD. That doesn't work either. 

At this point I'm just frustrated. I installed Ubuntu, Apache, MySQL, Webmin, ububutu-desktop and customized my server in about 2 hours. It was a breeze. Yet here I've been fiddling with wireless for about a week now editing config files, stumbling through the command line, trying to "make install". There has to be an easier way than this. If not I can't see how Ubuntu is ready for everyday use by everyday people. Sorry for the rant, I'm just frustrated. 

Here's the card I'd like to get working, Belkin Wireless G Desktop Card (F5D7000). It works on the Live CD just fine (both Dapper and Edgy) but it won't work on Ubuntu Desktop. I've posted for help in some other places and people suggested I apt-get whatever. I can't since I have no network access. I can download files from my Mac or PC and move them over but that's it. Can anyone help? I'm about ready to give up here.

---

### Post by Floppyjoe on 2007-03-09
Have you tried to install the linux-restricted-modules? There is a link here that suggests that this may be all that is needed for a Belkin F5D7000.

[http://www.ubuntuforums.org/showpost.php?p=2025121&postcount=7](http://www.ubuntuforums.org/showpost.php?p=2025121&postcount=7)

If you have the Ubuntu install disk you can probably install it by clicking on System/Administration/Synaptic Package Manager.
Then click on Edit/Add CDRom
Then click reload.
Then search for linux-restricted-modules(the ones for your kernel type)

---

### Post by Don Carcharo on 2007-03-09
That's how I fixed it the last two times however this time it didn't work. As best I can tell I'm using kernel 2.6.17-10 which I imagine is the default for Edgy. The thing is I honestly can't remember if it was the 2.6.17-10 or 2.6.15-26 package that was working. Either way I've completely uninstalled both packages and reinstalled each with no luck.

I reeeeeeally don't want to reinstall everything for the third time just to get my wireless to work. At this point I'd rather run a 200ft cable through my living room. Though I'm not sure if my wife would appreciate that very much. :)

---

### Post by MetalMusicAddict on 2007-03-09
Blame hardware manufacturers.

---

### Post by Floppyjoe on 2007-03-09
You can tell what kernel you are using by entering the following at the terminal:
```
uname -r
```
Other than editing some config files which I know you are frustrated with I am at a loss to help you further. Sometimes updates will break things that were working before. Possibly one of the updates was a kernel update which would possibly require you to install the new linux-restricted-modules for the new kernel.

---

### Post by Don Carcharo on 2007-03-09
Thanks for the tip. My kernel is 2.6.17-11 and the options for packages I have on my CD are 2.6.15-26 or  2.6.17-10

---

### Post by Don Carcharo on 2007-03-09
> **MetalMusicAddict said:**
> Blame hardware manufacturers.

Well that's fine but hardware manufacturers mainly support Windows, it's what the market dictates. And if the Ubuntu community is expecting this to change anytime soon, that's bad news for people like myself who want to use WiFi.

Yes not having access to hardware makes providing drivers incredibly hard, if not impossible, I realize that. But what some people don't appreciate is that for people like me it's also hard to install and remove these questionable drivers. If I were just double-clicking deb packages here and checking to see if things worked, that's one thing. But I'm not. I'm editing config files and typing in commands that I don't even understand. Heck right now I probably *have* drivers that work I just don't know what to do with them. That's frustrating.

---

### Post by Ethelbert2 on 2007-03-11
[SIZE="3"][FONT="Georgia"][COLOR="DarkGreen"]
 I had similar problems with an Atheros chipset which was supposedly very easy and "work on installation" but didn't until you discovered the "restricted-modules" thing which is central - then I kept getting the update issue too.

The answer to that is to install the linux kernel generic (you find it somewhere on Synaptic lists if you are lucky enough to have a way to connect to the Internet).  I got some good advice during similar confusion ([url]http:
//ubuntuforums.org/showthread.php?t=374280)[/url].  

The way to connect incidentally since you did previously get the card going, is to catch the boot up menu when you start, and choose the older Ubuntu version listed (maybe you have to press Esc during booting)
The older version will work with the wireless card - then use Synaptic to mark up the generic Linux (its dependencies seem to include the restricted-modules too).  Then run the updating stuff. What this seems to do is update everythiing dependent when there is a change to the core so that wireless keeps working.  Anyway it has so far - I don't know what will happen when I go for 7.4 soon!! 

(I am spending time now trying to get a modem going to be a backup in case the wirelss goes , and for faxes - but it is just as complex hunting down information - even though there are some very helpful people putting themselves out to help.)[/SIZE]

[SIZE="2"]<comment bit>I agree with much that you say: I like Ubuntu and have seriously started experimenting with Linux which has lots of nice things about it. But wifi (and to double the problem - modems too) are a pain and an impossible  major obstacle for anyone who knows little about computers (my mother, who thinks that basically "the computer" can "do things or not" and does not understand software even. And like myself early on, many people would be terrified about actually opening a computer box or messing with settings - "I knew it would go wrong if you tampered with it" the family is ready to say!)

I accept the arguments that it is US Federal law paranoia about "secret" radio links which restricts manfuactuers from releasing workable driver information and this in turn hobbles Linux developers. But even when drivers are available it is incredibly hard to find straightforward instructions on how to install them and configure etc. I tried a Realtek 8185 which was terrible (still can't use it), a Broadcom which was very workable and once you disentangled the instructions (the hard bit) actually quite easy to get going</comment bit>[/COLOR][/FONT][/SIZE]

---

### Post by Don Carcharo on 2007-03-11
> **Ethelbert2 said:**
> 
The way to connect incidentally since you did previously get the card going, is to catch the boot up menu when you start, and choose the older Ubuntu version listed (maybe you have to press Esc during booting)

Thanks. See that's where the Linux noob in me comes out. I had no idea you could install multiple kernels and select them at boot. Apparently this is exactly what I had already done (4 times) and why it worked previously but then stopped. Simply reverting to the one working kernel of the four fixed everything. Once it came back up I removed the new kernels with broken wifi and the server kernel which doesn't support the card.

Everything works smoothly now. I even got Beryl on the box (for now) just to see what it's like.

---

### Post by Vadi on 2007-10-16
> **MetalMusicAddict said:**
> Blame hardware manufacturers.

That works in most cases, but not when the card was working in previous releases.

---

### Post by bliffle on 2007-10-16
I tried a few of my old wifi PCMCIA cards in laptop #2, finally decided to just go to the computer store, but another PCMCIA wifi card and return it until I got one that worked. Got a bingo! on the 1st one, an Airlink101 (Atheros chipset). It worked right out of the box and hasn't failed me since. Cost: $30 and well worth it.

---

