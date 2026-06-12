---
title: "Help! I'm new: Getting Kworld DVB-T PC160-2T  card to work with Mythtv, anyone?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by danhuke on 2010-04-18
hI

I'm just trying ubuntu (and linux) for the first time today, going pretty well so far but I can't get my TV card to work. Its a [SIZE=1]Kworld DVB-T PC160-2T. I've spent a couple of confusing hours reading pages which suggest it will work (like this one: [http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T](http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T) ), but that I can't install the necessary software. 

Don't think the software can be installed via synaptic, the page above said I'd need to d/l a .gz file, unpack and make install. Got stuck after unzipping the file.  I get the general idea, am pretty experienced windows user but know nothing of linux filesystem, command lines, etc.

any advice gratefully received! though at 2am i probably should give up for today..

thanks
[/SIZE]

---

### Post by danhuke on 2010-04-20
Anyone? Just how to install the zipped file would probably be enough for me to figure out the rest...

Thanks again

---

### Post by danellisuk on 2010-05-31
I just purchased a KWorld Dual DVB-T PCI TV Card (KW-PC160-2T) from Maplin.  I did a fresh install of Mythbuntu 10.04 (32bit as its an old machine).

Mythbuntu failed to detect a tuner card, so I searched and found that same link on the mythtv wiki.  After using the restricted driver manager to install the non-free firmware, I then rebooted, and mythtv setup then detected both tuners.  I'm new to myth tv and so I had to play about a little in the mythtv setup to get both tuners configured properly.

However, I'm now able to watch one channel and stream another to my netbook.  And so I'm very impressed with mythtv!

Looking around though, I can't find any info on getting the supplied remote working.  I think I need to learn a bit more about lirc (linux infrared remote control) first.

---

### Post by geekus_khan on 2010-06-13
I'm running lucid, and I followed the instructions from the link... however I am unable to watch tv. I noticed somewhere in the setup backend that I have the option to increase the power to the card / tuner to get a stronger signal... but I now can't seem to find it. 

I set-up the channel scan for both tuners to have max timeout, and have disabled the 'quick scan' option. I only bought this pci-card yesterday, and I'm eager to be able to watch Mythbusters tomorrow night.

thanks in advance

---

### Post by danellisuk on 2010-06-14
So you have installed the firmware using the restricted driver manager?  That is critical for it to work.  Our transmitter is some distance away and so I have an aerial on the roof with a booster.  I didn't even try the packaged aerial, because I know from experience that there will be no signal.

I have noticed on my card, that a bright blue on-board LED will light if the card is getting a signal.  When I unplug the aerial cable the LED goes out.  It will also go out when the picture breaks up due to bad reception.

---

