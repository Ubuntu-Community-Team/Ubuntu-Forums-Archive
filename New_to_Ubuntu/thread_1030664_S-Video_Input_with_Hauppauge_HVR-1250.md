---
title: "S-Video Input with Hauppauge HVR-1250"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by gforshay on 2009-01-04
I am extremely new to posting  threads so apologies in advance.

I am trying to access the s-video input of my Hauppauge HVR-1250.  I do not find anything in the Ubuntu forums that respond to S-Video and HVR-1250...so if I missed a post, please respond with that and I'll proceed from there.

I can see the card, I can View Live TV, schedule and record OTA programs using Mythbuntu.  However, I do not see this feature of the card when I am defining my input cards.  When I go to terminal in UBUNTU I get the following responses to the following queries...

** sudo lspci -v**
(excerpt)
03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 03)
	Subsystem: Hauppauge computer works Inc. Unknown device 7911
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at e5000000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint IRQ 0
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Vital Product Data
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
(/excerpt)


**dmesg | grep cx23885**
[   46.749980] cx23885 driver version 0.0.1 loaded
[   46.750279] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   46.874875] cx23885[0]: i2c bus 0 registered
[   46.874891] cx23885[0]: i2c bus 1 registered
[   46.874902] cx23885[0]: i2c bus 2 registered
[   46.901269] cx23885[0]: warning: unknown hauppauge model #0
[   46.901270] cx23885[0]: hauppauge eeprom: model=0
[   46.901271] cx23885[0]: cx23885 based dvb card
[   47.021011] DVB: registering new adapter (cx23885[0])
[   47.021208] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 21, latency: 0, mmio: 0xe5000000

---

### Post by edco on 2009-01-06
You seem to be having better luck with your hvr-1250 than I am:

 dmesg | grep cx23885
[   15.587598] cx23885 driver version 0.0.1 loaded
[   15.588250] cx23885 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   15.588362] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   15.719389] cx23885[0]: warning: unknown hauppauge model #0
[   15.719391] cx23885[0]: hauppauge eeprom: model=0
[   15.719394] cx23885_dvb_register() allocating 1 frontend(s)
[   15.719661] cx23885[0]: cx23885 based dvb card
[   15.896634] DVB: registering new adapter (cx23885[0])
[   15.897091] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   15.897098] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfce00000
[   15.897105] cx23885 0000:03:00.0: setting latency timer to 64

How did you get it to recognize the model number?  Is there a new driver I can download?  This has been driving me nuts.  Thanks for any help.

---

### Post by gforshay on 2009-01-06
I really don't know if there was a specific driver that I installed.  After my initial installation of Mythbuntu, I entered the Mythbuntu Control Center and Added Ubuntu as a desktop...checked the Sofware Sources to be downloadale fom the internet (selected all) and download from the nearest archive.

Afterward, I performed an Update, and voila...everything worked...at least the coax feed did...now I'm trying to figure out how to activate the Composite Video/Svideo in.

I believe that the cx23885 must have been successful as an mpeg input, but not in the HVR-1250.  I found an article in the "how to" category ([http://www.linuxtv.org/wiki/index.php/Development:_How_to_add_support_for_a_device](http://www.linuxtv.org/wiki/index.php/Development:_How_to_add_support_for_a_device))  which I hope will walk me through creating a definition that will activate the s-video input.  Ive never done this so...it may take a while...lots of trial and error.

If anyone out there has been successful in activating the mpeg on cx23885, I'm certain there will be plenty of us interested in making it work for the HVR-1250.

---

### Post by gforshay on 2009-01-07
[FONT="Arial Black"]Update to my progress...
I still cannot get my s-video to be recognized after following some directions on updating with the latest drivers.  I'm guessing that I need to somehow set some configuration parameters for the card, but do not know where to go, or what to look for...

Searching through Ubuntu forums, I came across the following Instructions from propagandhi...
(link>[http://ubuntuforums.org/showthread.php?t=550276](http://ubuntuforums.org/showthread.php?t=550276))

[/FONT]
[PHP]++++++++++++++++++++++++++++++++++
For anybody else that is playing with a tuner card with a Conexant CX23885 chipset, use mercurial to check out the latest v4l-dvb sources. For example:

make sure you have build-essential packages and the headers for your running kernel.

sudo apt-get install mercurial

mkdir v4l_source

cd v4l_source

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb

make & make install

+++++++++++++++++++++++++++++++++++++++[/PHP]
[FONT="Arial Black"]I then ran the command

sudo modprobe cx23885

which gave me no response...so I executed dmesg Resulting in the following...[/FONT]
[PHP]+++++++++++++++++++++++++++++++++
gforshay@PVR:~/v4l_source/v4l-dvb$ dmesg | grep cx23885
[   50.527259] cx23885 driver version 0.0.1 loaded
[   50.527562] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   50.926603] cx23885[0]: i2c bus 0 registered
[   50.926641] cx23885[0]: i2c bus 1 registered
[   50.926653] cx23885[0]: i2c bus 2 registered
[   50.953052] cx23885[0]: warning: unknown hauppauge model #0
[   50.953053] cx23885[0]: hauppauge eeprom: model=0
[   50.953055] cx23885[0]: cx23885 based dvb card
[   51.023266] DVB: registering new adapter (cx23885[0])
[   51.023422] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 21, latency: 0, mmio: 0xe5000000
[81969.911721] cx23885_wakeup: 2 buffers handled (should be 1)
[103748.089526] cx23885_wakeup: 2 buffers handled (should be 1)
[103761.423371] cx23885_wakeup: 3 buffers handled (should be 1)
++++++++++++++++++++++++++++++++++++++
[/PHP]
[FONT="Arial Black"]I never saw the last "wakeup:.." lines before...so something must be happening...dont know what...
In any event, when I get into MythTV card setup, the mpeg card entry comes back as "Failed to open".  However, the good news is...I still have my OTA input (DVB0) recognized....so I haven't lost any functionality.[/FONT]

---

### Post by edco on 2009-01-07
I've been following this thread trying to get my HVR-1250 up and running.  I did the mercurial install and did the modprobe of cx23885, but still no luck.  Note the tveeprom error message when I do dmesg:

[   13.406147] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   13.533893] tveeprom 0-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   13.533898] cx23885[0]: warning: unknown hauppauge model #0
[   13.533900] cx23885[0]: hauppauge eeprom: model=0
[   13.533903] cx23885_dvb_register() allocating 1 frontend(s)
[   13.533923] cx23885[0]: cx23885 based dvb card
[   13.635240] MT2131: successfully identified at address 0x61
[   13.635251] DVB: registering new adapter (cx23885[0])
[   13.635256] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   13.635813] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   13.635820] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfce00000
[   13.635827] cx23885 0000:03:00.0: setting latency timer to 64

I'm new to all this, so please forgive me if it's something obvious.  Do I need to reload something to fix a corrupt file?  

Thanks.

---

### Post by gforshay on 2009-01-08
Edco,
I too am new to this, and am learning to swim as well.  I don't think that it is all that obvious...and I do notice a few differences, but I think it is a result of our different setups.  I think the critical pieces are in place, and I think the issue might be in the front end you are using.  For example, I don't have both DVB statements in my dmesg...yours has:

[ 13.635256] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...

Maybe the issue is with the application.  What application are you using to access the card?  I am using Mythbuntu.  In Mythbuntu, I can see the DVB statement above as a card input.


However, when I leave Mythbuntu, and enter my ubuntu desktop and try using TVTime, I cannot get any input card recognized.  I'm sure there's some way to configure the card, but I have not figure out how to navigate TVTime's menu to configure an input card.

I don't know what to say about the tveeprom, hopefully someone might wander by and offer some additional info.  Could possibly be left over from a previous attempt?  Is this the first time you've seen this in a dmesg response?

---

### Post by edco on 2009-01-08
I have a scattershot of programs I have installed trying to access the card...MythTV along with a bunch of other TV viewers.  I'm not at the machine with the card in it right now, but the most common error I get is that the programs can't find video.o (or something like that.) I'm not sure where that resides in Ubuntu or how to let any of these programs know where it is.

Frankly, I don't care if it can tune in TV channels or not, I really want to use it to take input from my miniDV camera.  Anything anyone can suggest to get the card to wake up and do this would be greatly appreciated.

---

### Post by gforshay on 2009-01-08
I understand...this s-video input is truly frustrating.  If you can access a terrestrial feed (using TV antennae) then you know that your card and your system are interacting properly.  Once you've established that your card/computer/OS/Application are communicating, then we can focus on the s-video as input.

---

### Post by edco on 2009-01-08
All my video programs TVtime, Cinelerra, etc, seem to be looking for this directory, which doesn't exist:  /dev/video0

Any thoughts on what it is and what's supposed to be there and what program builds it?

---

### Post by gforshay on 2009-01-09
I think that the definition location of the hvr-1250 we are looking for is in dvb/dvb/adapter0.  I'm not certain how to change the input location in TVTime to confirm this.  Is there a maintenance tool to update the input location for TVTime?

---

### Post by gforshay on 2009-01-09
Sorry...should have looked before replying earlier...but found some additional info at this site...

[http://www.linuxquestions.org/questions/linux-software-2/tvtime-cant-select-tuner-input-433618/](http://www.linuxquestions.org/questions/linux-software-2/tvtime-cant-select-tuner-input-433618/)

In short, this states that TVTime is for analog only.  By setting up the HVR-1250 using v4l-dvb, I believe that we are only defining its digital video broadcast mode and probably need another program to access the dvb directory for tv input.  

They offer some advice on modprobe commands with parameters that I believe will allow us to select the appropriate features of the card.  I'll poke around and see what I find...if you get there sooner, please post!

---

### Post by edco on 2009-01-11
I've been traveling for the past 4 days or so.  Should get home tonight.  Now that I know where the folder is located, I might either copy it to the location that TVtime wants or see if I can get TVtime to look in the right place.  I'll let you know if I can get it to find the driver.

---

### Post by edco on 2009-01-12
I found this on TVtime.  Lots of good stuff on setup.

[http://ubuntuforums.org/showthread.php?t=921233](http://ubuntuforums.org/showthread.php?t=921233)

---

### Post by gforshay on 2009-01-12
TVTime is the wrong program to run the HVR-1250.  

It was buried in my last post, so I thought I'd re-post it at the top this time.  TVTime is for Analog input...LinuxTV drivers do not support Analog at this time...nor..given the Feb deadline for all digital, i do not think the analog will materialize.

However, I find that the VLC player does accept digital.  I haven't had the time to understand all of the preferences parameters, but did notice that there was plenty of opportunity to specify mpeg...the question is still..how do we (mount?) enable the interface to the s-video capture.

I was able to find and install VLC through Synaptics.

---

### Post by edco on 2009-01-12
I have VLC installed already and the cable to the card is straight from the wall, so the digital signals already on it should be getting through.  I'll give it a try.

---

### Post by Phiwum on 2009-01-13
I picked up this card just today, so I'm watching this thread with interest.  So far, I've had no luck getting "scan" to work as outlined at [http://www.linuxtv.org/wiki/index.php/Scan#Scanning_for_channels_you_can_receive](http://www.linuxtv.org/wiki/index.php/Scan#Scanning_for_channels_you_can_receive)

I'll keep you posted if I miraculously become clueful.

---

### Post by edco on 2009-01-15
My card is just dead in the water.  I haven't been able to get it to do anything.  Has anyone had their HVR1250 become even slightly functional in Ubuntu?

---

### Post by edco on 2009-01-17
I tried using this program:  Me TV 0.5.30.  Georgia Public Television will come up for about 10 seconds, play and then the player crashes.  This is the first sign of life out of my HVR1250.  

I'm still a bit frustrated with it, but at least there is a glimmer of hope.

---

### Post by edco on 2009-01-17
Just tried MythTV and Watch TV does nothing.

---

### Post by edco on 2009-01-17
I did some more searches and it looks like I can bypass the HVR1250 altogether with a FireWire card.  There is a program called dvgrab that should let me import video from my camera, which is all I want to do.  Just ordered a card for $12.  I'll let you know if I have any luck with it.

---

### Post by gforshay on 2009-01-18
Does a driver for the specific s-video feature need to be written for the HVR-1250 on MythTV, or UBUNTU?  If this is the case, can someone point me to a "how to" on assembling a video driver?

I understand Edco's frustration regarding the HVR-1250, and it seems as if the firewire solved your camera interface needs and you are off and running...good for you!

However, i am relying on using HVR-1250 to eventually receive output from my Samsung DirecTV tuner, and eventually control the tuner, so first things first.  As I have posted earlier, I can see the card through the various lspci and dmesg commands.  So, in UBUNTU I know the system sees the card, but I cannot process any signal, as I believe I need to go through a series of configurations...for example setting up channels and defining the channel.

In MythBuntu, I am able to view and record live tv, and playback.  However, I have not been able to access the s-video as described in the MythTV link

 [http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat#Svideo_or_Composite_from_the_STB](http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat#Svideo_or_Composite_from_the_STB)

---

### Post by korgman on 2009-01-25
gforshay, i am in the exact same position.  I got the 1250 card for HDTV knowing that the analog drivers were not there .  Now that my satellite dvr broke, I figured I'd buy a standard receiver and let myth become my sat dvr.  
From the mythtv wiki: [http://www.mythtv.org/wiki/Hauppauge_HVR-1250](http://www.mythtv.org/wiki/Hauppauge_HVR-1250)
> The drivers currently only support digital capture.

I was hoping this would have changed by now. Guess not, possibly never.  Development effort will probably focus on newer cards.

---

### Post by gforshay on 2009-01-26
Korgman,
Thank you for replying.  I was looking at the site you cited in your response.  In the example provided for the Gentoo build, there was a reference to the bt848 and the conexant cx23885.  

Two questions:
[LIST=1]
[*]Do I understand correctly that the bt848 is the tuner (changes channel) for the cx23885 which handles the incoming signal from the antennae?

[*]What chipset would handle the s-video signal input?
[/LIST]

I keep thinking that if I can identify how to enable the s-video/composite signal, then I could map it to a channel and be ready for he next step...connect to a DirecTV tuner.  But first things first...

---

### Post by edco on 2009-02-02
I gave up and bought a firewire card.  Plugged it in and it just worked.  I can import digital video via Kino with no problems whatsoever.  

Guess I'll just check the HVR-1250 from time to time to see if it comes alive via an update.  Would be nice to watch TV on this box, but at least I can use it to edit video from my camera now.

---

