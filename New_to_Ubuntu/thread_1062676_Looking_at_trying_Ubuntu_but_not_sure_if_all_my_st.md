---
title: "Looking at trying Ubuntu but not sure if all my stuff will work"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by beddo on 2009-02-07
Hi Folks.
My computer has been ticking away with XP for years now but I'm looking around again. I don't use anything hugely special, except for audio/visual gear.
I'm a guitarist and I have a variety of gear that I use at the moment. The sound card in my computer is quite an old VideoLogic SonicFury but most of the time my recording is done through an external Digitech GNX4 USB device using a not cheap mic.
I also record video off of a Trust 14882 USB webcam.

Currently I use Sony Vegas Pro for recording and video stuff and then split the audio off into Adobe Audition before putting it all back together. I am looking at maybe getting a dedicated external soundcard (either USB or fireware as my PC has both) because I get lag on the audio through the Digitech USB ASIO drivers. The soundcard I was looking at is the Lexicon Omega Studio so I can record both pickup and mic sound at the same time.

I guess my question is quite simple but may have lots of bits to answer. Is any of this kind of setup not supported in Ubuntu or is it amazingly difficult to get any of it working? I spend more time than I should working on other people's computers and don't particularly want to spend days of my spare time trying to figure out how to get it all to work. My PC basically does a/v stuff, Internet stuff and some of my business accounts etc.

I'm not a complete *nix nonce as I've run servers for years but they've been BSD and no X or anything other than what is needed to do the job. It has to be 5 years or so since I last looked at desktop varieties!

---

### Post by cmnorton on 2009-02-07
Look at the Ubuntu minimum installation requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

to make sure your computer will run well. If it's running XP well now, you could probably make the jump especially if you choose the XUbuntu derivative, because that makes fewer graphics demands than KUbuntu and Ubuntu.

I don't know much about the equipment you've listed, but you should be able to test some of this stuff with a live CD, although things will run slower. There are dual-boot options as well as some alternate installation methods. I have preferred to dedicate one box to Ubuntu and not get caught up in the dual-boot problems.

---

### Post by snowpine on 2009-02-07
Just burn a Live CD and try it with no change to your system. If you find your hardware is not supported, you can abort the Ubuntu experiment with no harm done.

You might also be interested in Ubuntu Studio. It has lots of cool audio-related applications, but unfortunately I don't think it has a Live CD...

---

### Post by HavocXphere on 2009-02-07
Might require a bit of patience getting the USB sound recording to work.

I would suggest buying a separate harddrive and trial & error with that while the main harddisk is unplugged. Nothing like knowing you've got a fallback on a harddisk that is safe & sound to boost confidence. And since you mention that your business accounts are on the same box, it might be good if something does go wrong.

It's not entirely clear to me how powerful your PC is. If its as old as XP then you might considered upgrading? (Admittedly I know people who run XP on brand new monster PCs..so its no real indication) Cause I know that editing large amounts of audio on underpowered machines isn't fun.:(

---

### Post by stalkingwolf on 2009-02-07
you might also give Earos a try.  It also is available as a live CD.

You can download it from distrowatch.  It is supposed to be formulated 
for just the things you are talking about.

---

### Post by beddo on 2009-02-07
The computer itself isn't of concern. It is relatively new: dual core, 2gb ram - can't remember the rest which considering my job is IT consultant shows you how little I play around with my own stuff these days. It is running XP because Vista is a bag of wank..

The trial and error messing about with stuff is exactly what I don't want to be spending my spare time doing. I have enough of computers during the day :lol:

Earos looks interesting but I think I'd rather go for something with a decent community support. Earos doesn't seem to have its own forums and directs you to an 'Enterprise' version that doesn't even seem to be listed in the shop that you are directed to.

Actually what I would ideally like to do would be image up the current XP install so that it can run in an emulator but that's a whole other thing. I stumbled onto some other threads about firewire sound interfaces which look like a way forward with Ubuntu Studio but I'd still like to know if anyone has ever tried to use a Digitech with Ubuntu...

---

### Post by Helios1276 on 2009-02-07
Live Cd all the way

---

### Post by avtolle on 2009-02-07
I have no knowledge of what you are trying to do, but found [http://ubuntuforums.org/showthread.php?t=697158](http://ubuntuforums.org/showthread.php?t=697158) and while it doesn't appear directly applicable, perhaps it might give you some clues?

---

### Post by desowin on 2009-03-28
> **beddo said:**
> I'd still like to know if anyone has ever tried to use a Digitech with Ubuntu...

ALSA sound drivers should work.
There's [DigiTech library editor for Linux](http://desowin.org/gdigi/) available, although it would require some work to add support for GNX4 (the task is monotonous and takes quite some time, but it doesn't require any special knowledge (it brings down to using X-Edit, saving patches and noting value changes))

---

### Post by lkraemer on 2009-03-28
Here is what I would have a look at:
[http://artistx.org/site2/](http://artistx.org/site2/)

Download the LiveDVD at:
[http://artistx.org/site2/downloads/](http://artistx.org/site2/downloads/)

I think you will be pleased and overloaded with choices/decisions.

REMEMBER, Download the ISO, VERIFY the MD5SUM via software download
(Windows or Linux), Burn the ISO as Disk at Once (DAO) and at 4x or
8x...... Then, you will have a valid copy with less problems/issues.

Enjoy..... Welcome to Linux.

lkraemer

---

