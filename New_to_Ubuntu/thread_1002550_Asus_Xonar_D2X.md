---
title: "Asus Xonar D2X"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by expatCM on 2008-12-05
I have been reading the various threads on the Asus sound cards. I am thinking of buying a Xonar D2X but since I hate trying to fix sound problems more than anything at all I thought I had better open a thread and ask ....... the existing threads give you the answer you want depending on what you are wanting to hear .... the cards work or they don't work depending on the thread you choose.

It is now December 2008. Does the Xonar D2X work with Ubuntu 8.10 out of the box? Like does everything work? Asus appears to have zero support on their site .... is this a problem?

In light of Creative releasing drivers for the X-fi range, would this be a better line to consider purchasing?

I have asked this question in the Multimedia section of the forum but did not get any responses .....

---

### Post by expatCM on 2008-12-05
An update is that I took my computer to the store today and installed a D2X card.  The result was that the card was detected and Analog and Digital entries identifying the card appeared in the System / Preferences / Sound settings.   However, there was no sound to be found at all.  The on-board sound did still work though.

Does anyone have any suggestions of what I should have done to make this work?

---

### Post by _sAm_ on 2008-12-05
1. Did you turn off the on-board sound in BIOS? I had to do this before my "external" soundcard would work. 

2. Did you try to change to ALSA, OSS, Pulsaudio(under Sound Preferences)? I have read on a danish forum that ALSA will give sound out of the box on Ubuntu 8.10 with your card. 
ALSA:
[http://alsa-project.org/main/index.php/User:ClemensLadisch](http://alsa-project.org/main/index.php/User:ClemensLadisch)
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

---

### Post by expatCM on 2008-12-05
No I left the bios setting on Auto.  Do you think this is a fundamental reason for it not to work?

Yes, I tried all of the settings available which include all you suggest and even a few more ....  Some of the Test seemed to run but gave no sound.

---

### Post by expatCM on 2008-12-05
Took at look at the links you suggest, thank you.

I also can find posts where the card works.  I can find them where the card will not work.  Perhaps I am just rushing at this and should wait for a couple of months, after all, Asus are quite big and they compete with Creative with these sound cards.  Creative has recently released Linux drivers so perhaps Asus will do a bit of catching up.

---

### Post by _sAm_ on 2008-12-05
I would try to turn of the internal soundcard in the BIOS and see if that helps(I _had_ to do this before my external would work on Ubuntu). 

If it dosnt help just turn it back to auto as before.

---

### Post by expatCM on 2008-12-06
hmmm ....  well that means another trip back to the shop with my PC.  Need to think about that first.  They all viewed me as a total curiosity when I went in there with an operating system they had never heard of so I guess they will remember me ..... but .....  if it does not work I am no further forward ...  

Perhaps I should wait until April when 9.04 surfaces ... :)  Perhaps by then Asus will have some drivers.

---

### Post by slick666 on 2009-01-17
It seems like it should work. Take a look at [http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso]("http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso"). I'm looking at the Xonar DX Myself. I'm interested if you get the D2X to work.

---

### Post by expatCM on 2009-01-17
Should work is good ....  but I took my pc to the store to test twice and it did not work.  The card was detected but work ....  well nothing I could do would make any sound appear so ...      I did not buy..

Reading all the posts about people who say it works I find that there is one thing missing --  details of their hardware.  I have tried with a Gigabyte motherboard / AMD cpu and I really wonder if this has something to do with it.  I do not know enough to explain why that should be the case but I can think of no other reason why it does not perform.....

---

### Post by brab on 2009-01-23
I have an ASUS motherboard and Intel qaud core cpu, with the D2X and out of the box I have sound, but only the front channel. I didn't turn off the on board sound in the bios and the only conflict I have so far is that my D2x is set to hw:2. My last machine running Ubuntu 8.04 would assign hardware locations based on which sound device it detected first (usually the on board sound) so every so often I had to switch the hardware location setting in alsa/xine to make it work. 

I'm working on getting 5.1 out of the D2X - I'll keep you updated.

---

### Post by expatCM on 2009-01-23
Very interested to read your comments.  Thank you for posting.

I have just (literally) bought a card.  I also decided to put together a dedicated system for a home theater.  So I have the card on an Asus motherboard.

I am still experimenting but what appears is that the sound is working on the front and center / sub woofer but not the rear speakers.

Whilst this is not yet perfect it is a huge improvement from the Gigabyte board which does not work at all.

I would be very interested to hear your future news as you have explored further :)

---

### Post by brab on 2009-01-24
So a very quick and easy fix is always nice, especially after you go out and spend all that money on a relatively decent sound card. I went into synaptic and enabled the pre-release and unsupported updates repositories that I had previously not used. After installing a bunch of sound lib and pulse updates I ran ```
aplay -l
``` and found my D2X at hw:2 so I went into ```
alsamixer -D hw:2 
``` Apparently the card was set to front+surround by default so I switched that to front+surround+back and played around with the 4 (or so) master sliders to balance things out. I now have very nice and surround. Like I said - a very easy fix.

---

### Post by expatCM on 2009-01-24
I just took a look and you are 100% correct.  I have also now changed the default settings to include the "back" and this has put more of the speakers in operation.  I have now only one speaker (center) not performing and so I think a little bit of playing will be in order ....

Thank you for your suggestions, as you say it was an easy fix :)

---

### Post by Francewhoa on 2009-05-22
Asus Xonar DX works for me.

If your Xonar sound card isn't automatically detected by Ubuntu 8.04.2 the below installation script is the easiest way that I know of to install & configure any sound card. It's a script made by *soundcheck*. It does all the hard manual setup process for you. ** [Click here to open the post]("http://ubuntuforums.org/showthread.php?t=1167232&highlight=xonar"), then find the latest installation script attached at the bottom. **Current installation script is title *AlsaUpgrade-1.0.x-rev-1.17.tar*.


If the script works for you please add your results here:

[LIST]
[*][https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
[*][http://www.ubuntuhcl.org/browse/search+sound-cards?category=27](http://www.ubuntuhcl.org/browse/search+sound-cards?category=27)
[/LIST]

---

### Post by expatCM on 2009-06-04
Wish I had known about this in January :)

---

