---
title: "[SOLVED] Struggling Newbie, no sound, Gnome changes"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Biped on 2008-12-12
Total Noob here so bear with me.  Have been hearing so much about linux that I took the plunge and bought a Toshiba NB100 with Ubuntu 8.04 installed to see how I would get on. So far 12 hours spent and considering just forgetting it and giving up.

Here is what happened.  System arrived, started it, got it online - great.
It went off and did an update (current rev 100 days old).  I let it run that as I thought I might as well have everything current.  Downloaded info and installed. Asked me if I wanted to change config files or keep originals - said keep.  Rebooted, all looks fine then I see speaker symbol has red circle and line through it. Don't have right Gstreamer plugins istalalled. No sound at all.

Started checking this forum an went through this thread [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Tried aplay -1   nothing
lspci shows
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device ff7b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
Tried to install as per sudo modprobe snd-intel8x0
no joy
Tried to remove the problematic packages as suggested and reinstall
no joy
however that did mess up the automatic startuo into Gnome, now I get the terminal login and have to type startx to get Gnome
Lost shutdown option in Gnome also and can only log off back to the shell.
Still no sound by the way so it looks like I have caused more issues than if I had done nothing.

This is where  I am at the moment when I type: modinfo soundcore

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device ff7b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

If I go into Preferences> Sound and try to test bt selecting the various options (ALSA, Pulse Audio, Autodetect, OSS) I just get the following error
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

If anyone can help, I would appreciate it.  I am getting fed up as I hoped that this should have been much simpler.  

Thanks again and sorry for being such a thicko :confused:

---

### Post by jay li on 2008-12-12
I am also a Newbie like you, and I am sure you get help here. 
But have you tried reinstall ubuntu again to fix these problems?

---

### Post by ibizatunes on 2008-12-12
maybe you should try ubuntu 8.10, you could download that, burn a liveCD and see if that works?!

---

### Post by benc123 on 2008-12-12
I might be completely missing the issue here but you might try this. 

go into package manager, type in gstreamer, make sure you have gnome media and gstreamer0.10 alsa installed. if they are already installed then try reinstalling. 

Sorry if this is no help.

Benc123

---

### Post by iminhell on 2008-12-12
I'm new too but tell ya what, these two threads got sound working flawlessly for me:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)


Hope it helps.

---

### Post by Biped on 2008-12-12
Thanks for the feedback guys - here's my reposnses:

@ibizatunes - I don't have CD/DVD Rom for the machine as its just a netbook so would need to get a USB one somewhere.

@benc123 - tried that in package manager, they all appear to be there but did a reinstall to be sure, no change

@iminhell - followed the pulse audio guide, everything seemed to go fine but when I get to point 5 below and select the Pulse Audio Chooser it lunchs an icon in the top right bar.I lick on that and select Volume, the screen flashs but I get o options or list of devices.  Did I miss somehing

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished

Just out of interest I looked in Device Manager and the system shows 82801G (ICH7 Family) High Definition Audio Controller as the Audio Device.

Can I test it any other way or can I reinstall these drivers. I looked at the Alsa Project site and I think the drivers are this onehttp://developer.intel.com/design/chipsets/820/ 

I am not clear as to what to do from here - should I just go to this page and download the package of drivers [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) ie the top file to the desktop and if so how do I install it.

Sorry for being so useless- I am also just figuring out the syntax and struggling through terminal mode

---

### Post by albinootje on 2008-12-12
This could help : [https://answers.launchpad.net/nb100/+question/53970](https://answers.launchpad.net/nb100/+question/53970)
And did you install a newer alsa-version and did you add specific lines to /etc/modprobe.d/alsa-base ?

---

### Post by Biped on 2008-12-12
> **albinootje said:**
> This could help : [https://answers.launchpad.net/nb100/+question/53970](https://answers.launchpad.net/nb100/+question/53970)
And did you install a newer alsa-version and did you add specific lines to /etc/modprobe.d/alsa-base ?

Brilliant - genius, I had just registerd on launchpad and had done a hardware check.  Fantastic, sound is back so now I can get back to the original plan of seeing how I get on with Ubuntu on a netbook and remote access to our server as opposed to a MS laptop and all the baggage that goes with that.

Thanks again\\:D/

---

### Post by JKBurton on 2008-12-12
Don't forget to send some unhappy feedback to Toshiba. Selling a vendor-installed Linux computer without working sound sucks.

Unless, of course, sound worked until you told the OS to update...but I can't tell from your original post.

Congrats on getting the sound working. I hope you're happy with Ubuntu now!

---

### Post by Biped on 2008-12-12
To be honest - I don't know if it worked or not. I took it out installed the 1GB of Ram, plugged it in, got it online and off it went for the updates.  Figured that I should get everthing up to date before I started playing with it and installing stuff. I didn't try to surf or do anything so I have no idea if the updates caused the problem or if it was turned off from the start.

While it was not the most perfect start I have to say it was a good introduction to the forums and the info available. I feel much happier trying something on Ubuntu now as opposed to Windows due a fear of the windows system imploding.

I'm learning so its all good. Thanks again.

---

