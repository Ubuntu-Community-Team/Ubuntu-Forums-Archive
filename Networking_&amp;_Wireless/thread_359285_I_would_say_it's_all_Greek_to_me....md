---
title: "I would say it's all Greek to me..."
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by sleeperpup on 2007-02-11
...but I can at least tell when I'm looking at Greek.

I've been trying for about a week now, in my spare time, to get my Belkin F5D7010 PCMCIA wireless card to work with Xubuntu Edgy.  A week ago I had just installed Windows XP Pro on my ancient Toshiba Satellite 2615DVD and everything worked perfectly...well...actually it worked perfectly until the first batch of updates installed, and then it ran incredibly slowly.  So...I finally gave in and did what my friend had been telling me to do since I got the computer a month ago, install Xubuntu.

Great!  Granted it took it six hours (I'm not joking) just to install "anthy", whatever the heck that is, but it looks pretty and runs (relatively) smoothly compared to XP Pro so I was delighted...until I realized that the lights were off on my new wireless card and it wasn't showing up in Networking.

No problem, I thought.  I taught myself the ins and outs of DOS, and the various versions of Windows since 3.1, just by poking around and experimenting, and I have yet to come across a problem I couldn't fix with good old-fashioned deductive sticktuitiveness.  Why should Linux be any different?  ...apparently it should be different because it seems to be a sort of "by computer gurus for computer gurus" kind of OS.

Long problem short...the card doesn't do anything close to working, and all of my searches on the glorious interweb have yielded hundreds of forum posts and dozens of HOWTOs that have been...less than helpful.  In fact, I'm more confused now than I was a week ago.  One of the big problems is that most of the help I've found requires that the computer be hooked up to the 'net to begin with...wait, what?  I'm trying to connect to the internet, what are the chances that I'm already connected?  The aforementioned laptop only has a modem, and as I don't bother maintaining a land-line at my residence (thanks to mobile phones and cable ISPs) I have no connectivity whatsoever.  Please don't make me try to find an old copy of Win98!  I love the way Linux looks and operates (on the casual-user side of things) but I need the internet or the computer's useless to me!

HELP!

-C

PS:  I'm tempted to start a website as a sort of repository of knowledge for Linux beginners (real Linux beginners, not people who already know what 'sudo' is and how to install ndiswrapper).  There's simply nowhere for someone with my utter lack of Linux knowledge to turn to for help...that I can find.  If there is, then someone at least tell me where!  I'm going nuts!

---

### Post by sleeperpup on 2007-02-11
A few things I forgot to mention in the above rant...

When I went to install Xubuntu the first time (I thought it hung up when it went to install 'anthy' so I restarted the install and...y'know, went to bed) I did not have the card plugged in, and I got an error about how there was no networking card found, but when I went to try the install again I had the card in and I didn't get the no network card error.  I was very happy, until I opened Networking and nothing was there except the internal modem...

---

### Post by Floppyjoe on 2007-02-11
If you need to install ndiswrapper for your project and don't have internet connectivity it may be available on your install disk. 

Click on System/Administration/Synaptic Package Manager.

Next click on Edit/Add CDROM follow the instructions then click on reload.

Next search for ndiswrapper and install the necessary packages

Regards,
Floppyjoe

---

### Post by sleeperpup on 2007-02-11
I appreciate the quick reply.  :]

I suppose I should have mentioned that I've already installed ndiswrapper (it was on the Xubuntu Edgy Alternate CD) thanks to one of the more promising HOWTOs I found, but then I realized that the HOWTO was for the same chipset, but a different card altogether, so the driver filenames it was giving me were wrong.  So, that being said...what next?

Thanks again!

---

### Post by Floppyjoe on 2007-02-11
You need to locate some windows driver files that came with your Driver CD for your card. If you don't have such a cd you may be able to go to the manufacturers website and download a windows driver for it there.

You should open a terminal and issue a lspci command to find out the exact version of your card Revision number and all.

Possibly here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Copy the drivers to some removable media and to the computer in question.

---

### Post by sumgi on 2007-02-11
I'm right there with you, and to tell you the truth these forums have been of no use what so ever. All my progress so far I put together myself in the past eight hours from bits of posts and how to's all over the web. I'm a little better off than you are since I have an ethernet port, but my wireless still doesn't work in ubuntu.

I have ubuntu edgy eft all nice and updated.

I'm using a netgear WG511 v1 card

So I might just right down some of the steps I've done just so I can recap for my own self.


```

Is your card installed?

Make sure you have wireless enabled under System ..> Admin ..> Networking

display a list of configured interfaces
[LIST]
[*]ifconfig -a
[/LIST]

that should return at least a couple interfaces, maybe loopback and something else.

If your wireless is present I think it will be either eth1 or eth2.

If it's there then you can scan for signals like so.

[LIST]
[*]iwlist eth# scan
[/LIST]

If there's nothing then I'm guessing your card isn't installed.

How To 1...Install ndiswrapper

[LIST]
[*]sudo apt-get update
[*]sudo apt-get install build-essential
[*]sudo apt-get install linux-headers-`uname -r`
[*]sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
[/LIST]

download latest [**_ndiswrapper_**]("http://sourceforge.net/projects/ndiswrapper/")

[LIST]
[*]tar xvzf ndiswrapper-1.37.tar.gz
[*]cd ndiswrapper-1.37/
[*]make distclean
[*]make
[*]sudo make install
[*]ndiswrapper -v
[/LIST]

Random Driver Searching...find .inf & .sys files for your card

So find the drivers for your card, check [**_here_**]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List").

I have a dual boot with XP Pro and ubuntu so I was able to take the exe on the netgear site and install in XP then get the .inf and .sys files from the WINDOWS directory. .inf files are in WINDOWS/Drivers and .sys files are in WINDOWS/system32/drivers. If you don't have access to windows then I;ve been told these are an option, [ext2fsd]("http://sourceforge.net/projects/ext2fsd") and [ltools]("http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html") but I haven't tried them.

Install Drivers...

[LIST]
[*]sudo ndiswrapper -i <driver_path>.inf
[/LIST]

if you try and install the inf without the sys file and get a messed up driver like I did, just do this
list drivers

[LIST]
[*]ndiswrapper -l
[/LIST]

you will see one that ls messed up

[LIST]
[*]sudo ndiswrapper -e <driver_name>
[/LIST]

When you tried to install the driver it probably told you the name of the .sys file you need, go get it and enjoy.

When that's done add ndiswrapper to the last line of /etc/modules

[LIST]
[*]sudo gedit /etc/modules
[/LIST]

And run the following

[LIST]
[*]sudo ndiswrapper -m
[/LIST]


```

So this is just what I've dug up for myself in the last eight hours or so since I've installed a dual boot on my laptop. I have yet to get any response on this forum though. Good luck with your connection because I still can't connect even though I can see my router. Unfortunately DHCP doesn't seem to be working, no IP. :(

---

