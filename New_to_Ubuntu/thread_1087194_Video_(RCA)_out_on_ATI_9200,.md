---
title: "Video (RCA) out on ATI 9200,"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by PermNoob on 2009-03-04
So I have been doing a lot of research to see how to acheive video out w/ my ATI 9200.  There is a lot of talk of 3 or so different drivers that can be used with the card, however on my restricted drivers page there is no option to enable a restricted driver.  Is there a way for me to setup my video card to push video out?  I don't care if its dual screen or cloned, I just want to be able to use this as a media machine from time to time.  The driver wiki just says how to install different drivers, I want to know if I can do what I want with this or any other driver.

As far as I can tell its impossible, but I would really rather hear otherwise.

---

### Post by PermNoob on 2009-03-04
also, my lshw gives me this, which doesn't seem to include a driver
odd?
```
    description: VGA compatible controller
                product: RV280 [Radeon 9200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=64 mingnt=8

```

---

### Post by PermNoob on 2009-03-04
ok, so I am an idiot.  I am not trying to use my video card, I am trying to use some second card.  the card only has DVI and S-video out.
There is a second card in my PC (its a sony viao) that has component inputs and such.
Can that card be used for video out?  how can i figure out what that  card is?

---

### Post by anewguy on 2009-03-04
Are you sure the 2nd card is a video card?  If so, you may want to try one of the envy products to install that driver.  If you are using a release prior to 8.04, use envy; release 8.04 and 8.10 require using envyng.  It's in synaptic package manager.

Dave :)

---

### Post by PermNoob on 2009-03-04
well it has a tv tuner on it, and component video, and maybe a svideo,  it was clearly meant to be a input, but I want to use it as output, the compent video atleast.  Is it one way, or is it just a question of the proper drivers?  I would assume the tuner is one way, but what about everything else?

---

### Post by anewguy on 2009-03-06
Currently we have no idea what it is, who makes it, so please do the following and post back the entire output (just copy and paste):

- go to a terminal window (applications/accessories/terminal)

- type:

lspci and press enter

post all of the output back here.  We need something to identify the device - just a description won't help us right now.  If it is a tuner, from what I've read some of them work fine in Linux and others are harder to get working.  Depending on the tuner card, there may not be any outputs - they might all be inputs (but doubtful from what you describe).  They might be able to be used as outputs for watching things from the tuner, but I don't know if you can direct regular output to them.  Also, you started with your ATI card and talking about which driver to use, then switched to this second card.  I assume you have a working driver installed for your ATI card?

Post back the info from above and we'll try to go from there.

Dave :)

---

### Post by PermNoob on 2009-03-10
ok, so I coulda sworn I replied to this.  Here goes again.  Just to set the mood, I am currently attemptign to use the SVIDEO out on my ATI 9200 card, running 8.10, to clear up any confusion I may have caused.

output from lspci:
```
suse@BRadley:~/ati/xf86-video-ati-6.6.3$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)


```

---

### Post by anewguy on 2009-03-10
For what it's worth, based on what you posted, I don't think it's the ATI9200 you need the help with.  There is another device that I am sure is going to be the one you were talking about with all the connectors on it:

02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder 


This will be your TV tuner card.  I think you will need to search for drivers for Linux for an iTVC16 or CX23416.

You may want to start here:

[http://packages.ubuntu.com/gutsy/x11/ivtv-source]("http://packages.ubuntu.com/gutsy/x11/ivtv-source")

From there, do a Yahoo or Google search using ubuntu cx23416 driver and scan through the results.

Dave :)

---

### Post by PermNoob on 2009-03-10
I will look into that, thank you.  However the other day I came across this walk thru, which is specific to my hardware, but from a much older flavor of ubuntu.  It fails when I try to build the driver, is this somethign too old to follow now, or can it be made to work?

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

once I get to the make step, I begin to get errors upon completion of whatever it is doing. I would post the output, but it is loooooong.

while you think about that, I will follow your link and advice.  thanks

---

### Post by PermNoob on 2009-03-10
OH!  one more thing, to be totally clear, my final goal is to display whatever is playing on my computer on the TV using the S-video output(iow videos on my HDD, games, youtube etc).  I do not have cable, so such capabilitys are nice (broadcast), but not my primary goal.

---

### Post by anewguy on 2009-03-11
You probably have to make sure you have the linux headers and the build-essential packages installed.  I'm not sure of the exact syntax right now, but I believe it is:

sudo apt-get install linux-headers-$`uname -r` build-essential

Then I would follow a newer post.

As far as displaying your normal PC video on a TV via the svideo or other connections on the tuner card, I can't really say.  One would need to look up the tech specs to see if it allows normal video out, or perhaps someone following here (or in one of the many posts on that chipset) will be able to tell you more.

I believe with MythTV and (I think it's called) iPTV (something like that) that what goes out the outputs if from that particular program (i.e., tuner, video-recorder playback, etc.).

Hopefully someone else can chime in on more specifics with that.

Dave :)

---

### Post by PermNoob on 2009-03-11
so following up your lead, that card appears to be my tuner, which I understand to be COAX for inputs such as cable or broadcast tv.  I belive such a plug is IN only?  It also has component, or is it composite (red yellow white), adn s-video.  I do not know if those are in or out or both. 

however since the ati 9200 is normally used for video out, I thinik I will start there.  Also following up the iTCc16 card only led to a lot of threads on using its tuner.

---

### Post by PermNoob on 2009-03-11
oops, you slipped that reply in there between my refreshes.  I will check if I have such things installed.  

random question, what purpose does the $ serve?  and the 'uname -r' bit?  Just trying to learn as I copy paste

before running what you said, I looked in synaptic to check for those packages, and they have the green installed box next to them, although there are multiple linux headers, I seem to have the two newest ones installed?
linux-headers-2.6.27.11
linux-headers-2.6.27.7

although strangly linux-headers-2.6.27.9 is not installed.

---

### Post by amadeus266 on 2009-03-11
I just removed my ati aiw 9200 and put in an ati hd 3850. I could never get any output from the 9200 except on the vga monitor. Also, the tv tuner on that card is not compatible with linux nor the other inputs as far as I am aware. That card works very well under windows. I even got it to work with MCE2005. The default drivers installed by Ubuntu will work best and no need to even try any of the newer ones as they will cause more headaches than they will solve. Most compiz plugins will work as well.(from my own experience... Don't enable the motion blur plugin. It will slow the system down so much that even pressing {ctrl-alt-bkspce} will take a few minutes to take effect.) I would like to see if you can get the 2nd output working though.

---

### Post by PermNoob on 2009-03-11
but I don't think my 9200 has a tuner...

am I dumber than I think, or are we talking about two different things?  there are only 3 plugs on the back of my 9200, VGA, S-video, and that big rectangle one, dvi?

there is a second card in the next slot that I described above in repply 12.

---

### Post by amadeus266 on 2009-03-11
> **PermNoob said:**
> but I don't think my 9200 has a tuner...

am I dumber than I think, or are we talking about two different things?  there are only 3 plugs on the back of my 9200, VGA, S-video, and that big rectangle one, dvi?

there is a second card in the next slot that I described above in repply 12.

O.K. You just the basic 9200. Mine is an All-In_Wonder 9200 with the onboard tv tuner. It has 4 plugs on it - video in used with a proprietay cable with s-video and RCA plugs for composite video and right and left audio, coax for connecting to a cable or antenna, video out used with a proprietary cable with s-video and composite video, and a vga plug. Disregard the information I gave before about the tuner but the driver part is important.

---

