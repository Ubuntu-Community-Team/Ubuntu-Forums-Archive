---
title: "New HTPC Needs Help Getting it to Run"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by RusH487 on 2009-03-03
This past weekend all the parts to my brand new HTPC arrived.  Excited to get it up and running as a huge media center for my collection, I quickly assembled it and installed the latest 64 bit version of Intrepid.

That's when all the problems started.  It installed and booted fine, but I've been running into a host of driver/hardware issues ever since.  My setup is as follows:

M3A79-EM Asus Motherboard
AMD Phenom 9550 Black
Hitachi 1TB 7200RPM SATA
AVerTVHD MCE A180 TV Tuner
4GB Patriot 1066MHz RAM
650watt Raidmax Modular Power Supply

So far I have had a list of problems and nothing is working the way I would like it to, other than basic operations such as surfing the web or checking email (silently).  So far these are my issues:

No sound -- either from the regular, front channel outputs or the Optical output in the back (I don't even get a red light for the optical out)

MythTV -- while it recognizes the name of my card, neither MythTV, Me-TV, or TVTime will pick up any channels, despite me having attached an antenna and assuming I've installed all the proper drivers/firmware

Wacom Graphire 4 Tablet -- For whatever reason I can only get the pen to register with this.  The mouse portion might as well be garbage...  Admittedly, however, I have not taken the time to look into this issue as much as I have been dealing with the other two.

Please, I have been searching and reading for hours upon hours for documentation regarding getting the sound to work and the TV Tuner to work.  I've even tried downloading the Linux drivers from the Asus website for my motherboard and following their readme directions...  I can only get so far with them in the terminal before some error will pop up that neither I nor Google will be able to decipher (something about not having the kernel sources?)  I've tried posting on many different forums for these specific problems and no one seems to be able to help me...  No, strike that, no one has responded.  Is there anyone out there that can at least point me in the right direction as to how to install the drivers for my motherboard and perhaps get the sound working?  I'm willing to try anything (other than Vista).

---

### Post by jbrown96 on 2009-03-03
I can try to help with the sound issue. There's a new sound server for Ubuntu called Pulseaudio, and it's supposed to be really great, but I've never had luck with it. You should try to change to ALSA. Go to System--->Preferences--->Sound, then change all the devices to ALSA. Open a terminal Applications--->Accessories--->Terminal, then ```
alsamixer
``` If you only have one channel available, and it says pulseaudio, then restart and do this step again. If you get a whole bunch of channels, then choose to "test" your sound in the sound prefereces. You should be able to hear a tone. If you don't move through the channels and unmute them ("m" key). If you get it working, then mute all the stations that are not necessary to have audio because they can cause interference. 

As far as the flash issue, you should download a newer version from [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") Download the .deb (this is the same as a .exe installer in Windows). Open Synaptic System--->administration--->Synaptic. Remove the package called flashplugin-nonfree. Close out all web browsers that could be using flash, then double click on the flash .deb file to run it.

---

### Post by RusH487 on 2009-03-03
Thanks very much, jbrown for getting back to me -- you're the first person to have responded to any of my posts.

I did what you said and went through System->Preferences->Sound and changed everything to ALSA.  I then rebooted and, checked to make sure the settings stayed when it came back online (they did), and ran alsamixer in the terminal.  It still said 'pulseaudio' and only had the master channel available.

As for the flash, I downloaded the .deb, removed the flashplugin-nonfree from Synaptic, closed all browsers, and ran the .deb package -- to which it told me that I had the wrong architecture (i386)...?  Could that be because I'm running the 64 bit version of intrepid and they tried giving me a 32 bit .deb file?

---

### Post by RusH487 on 2009-03-03
I followed the directions on this page

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml)

and got the 64 bit flash player working (at least as far as I can tell....  Youtube works)

UPDATE:  I followed the directions here:

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

and managed to get alsamixer to show me the following:

Card: HDA ATI SB
Chip: Realtek ALC888

and a whole bunch of channels -- of which the Master, PCM, and Front are turned all the way up.  However, when going to click on 'test' I still have no sound :-\  Any ideas?

---

### Post by jbrown96 on 2009-03-04
Good job with the Flash player. I thought you were using the 32-bit version. The 64-bit alpha that you installed has significant improvements over the version in synaptic. 

As far as sound goes, do you get an error when you try to test the sound? Anything about a sine wave and 512 (I can't specifically remember the error message)? If you don't get any errors, then try playing some music or a youtube video. There is a file that can play some speaker tests, but I was unable to find it, but you can try the following command. It will make something like a knocking noise. If that still doesn't work, double check you alsamixer settings to make sure that your channels aren't muted. Usually, you need front, pcm, and master unmuted at least. Since you have a desktop and I imagine it has quite a few ports on the sound card, try some other ports.

---

### Post by RusH487 on 2009-03-04
Yes, this is the error I am receiving:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

UPDATE:  I ran gstreamer-properties like they suggested here:  [http://ubuntuforums.org/showthread.php?t=937902](http://ubuntuforums.org/showthread.php?t=937902)
I changed the default audio to Digital, and rebooted.  During the reboot I checked in BIOS to make sure that everything was turned on -- it was.  I turned off HDMI audio just to be sure.
Still no test sound from digital or analog.  There hasn't been a red light coming from the optical output either making me think it might be something wrong with the board...  However, it's been my experience in situations like this that it's usually not the hardware that's defective, but the operator... So I'm not shipping it back to newegg just yet.  Right now I am downloading the Linux Drivers off the Realtek website but I'm not entirely sure how I'm going to go about installing them just yet as it's an archive I'm not familiar with (tar.bz2).

Another Update:

Ok, so let me try and explain how I got a little bit of sound to come out of my speakers....  I went to the Realtek site and downloaded their latest linux drivers (realtek-linux-audiopack-5.10).  I unpacked all 4 or so tar files into a directory and followed the instructions included in the readme.  After running the make and make install commands they had requested in the readme, I rebooted the computer...  Hoping to see a glimmer of red light from the other end of the optical cord I was looking into.  Nothing.  I ran gstreamer-properties again and noticed this time that the driver had changed to ALC1200Analog, which I knew my onboard codec was supposed to be from the beginning.  This time I ran the Sound Properties 'Test' again with headphones plugged into the front of my case and I got the faintest beeping sound.  I double-clicked on the speaker icon at the top of the screen (next to the date) and went to switches, where I ticked the 'Headphones' switch.  This amplified the sound a lot.  I tried switching the headphones to the green port attached to the motherboard and it too works.  Unfortunately, I am still not getting any light from the optical output which means that I can only have stereo output to my receiver right now (not what I want to do)...  If there are any suggestions for how to get that damn red light lit up and playing some friggin' digital audio, that would be awesome.

Update Regarding the TV Tuner:

I managed to find this thread that I somehow must have overlooked which has been the most helpful thread I've found on the subject thusfar:

[http://ubuntuforums.org/showthread.php?t=942876](http://ubuntuforums.org/showthread.php?t=942876)

After following the directions as it said, while I still have not figured out how to import a channels.conf file into MythTV, I have managed to get the program guide for channel 3 in my local area to be visible in MeTV.  No picture or sound comes through, just the program guide for that one channel...  But that alone is enough to make me think that my tuner is working...  Perhaps just not as well as I'd intended being as I'm in the basement with an old, crappy antenna.  I'm going to try bringing a small TV down here tomorrow with one of those $40 Digital Converter Boxes to see if it picks up any signal....  So, so far today I've managed to get crappy sound and one digital listing of the local religion channel...  But it's better than nothing.

---

### Post by RusH487 on 2009-03-09
I've since gotten the regular analogue audio output to work perfectly fine, but that's simply not good enough -- I need my surround sound to work for this HTPC to be worth anything.  I've tried everything -- I even installed a small SPDIF card with 1 coax and 1 optical output that hooks directly into my motherboard (a little 3 pin SPDIF slot above the Azalea slot) and changed my default HD Audio output to SPDIF in the bios (instead of HDMI)...  Again, I'm not getting any light from the optical output and I'm not getting any sound from the Coax output either.  This card works perfectly on my old machine that's running Heron.  Any ideas on how to get this running properly?

---

