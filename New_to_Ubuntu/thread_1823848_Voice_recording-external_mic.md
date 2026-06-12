---
title: "Voice recording-external mic"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-08-12
Have Sound Recorder installed but when I click on it, to do some voice recording to dub over a video I'm building, I get this notice:

[I]Could not create the GStreamer GConf audio recording element.
Please install the 'gconfelements' plug-in from the 'gst-plugins-good' module.
Verify that the installation is correct by running
    gst-inspect-0.10 gconfaudiosrc
and then restart gnome-sound-recorder.[/I]

In checking the Software Center, gsstreamer, etc, they all show as installed.

Any suggestions as to how to get it working again? Want to do some voice recording using a USB connect headset/mic for clean voice recording on an instructional video.

Thanks for assists. (Laptop info below)

---

### Post by gordintoronto on 2011-08-12
Are you really running 10.04? If so, run preferences/Sound and see what input is selected.

Sound is one area which has changed substantially from release to release. For example, I have had much better results with 11.04 than with previous releases. (My computer is about the same age as your laptop.) You might even find that running from a LiveCD of 11.04 solves your recording issue, after you mount the hard drive so you can save the result there. Just click on "nnn GB file system" to get it mounted.

---

### Post by flyfishingphil on 2011-08-12
> **gordintoronto said:**
> Are you really running 10.04? If so, run preferences/Sound and see what input is selected.

Sound is one area which has changed substantially from release to release. For example, I have had much better results with 11.04 than with previous releases. (My computer is about the same age as your laptop.) You might even find that running from a LiveCD of 11.04 solves your recording issue, after you mount the hard drive so you can save the result there. Just click on "nnn GB file system" to get it mounted.
Yes, still using 10.04. Depending on who you "chat" with it can be a very good idea to not change until the next "full term version" is released, or do constant upgrade along the way. I changed to Ubuntu during the last "major" update to 10.04 and had a real pain getting changed up from the 9 version. (Had to do a total "save/reinstall" of everything I had worked on during the "upgrade". If there is an easier way I'd be more than willing to take directions step-by-step and upgrade.)

RE: The sound

It shows Internal Audio Analog stereo as the input. Suggestions?

OK, found the info on resetting the Update Manager to "upgrade", so I can go to 10/10 & 11.04, but need some help before I do it.

Edit 1
Have a Maxtor 160GB external drive I can do a backup in, before I risk losing everything I've worked on, but don't remember how to do the backup. Anybody know of instructions on that I can print and follow? DISREGARD. Transfered files to external hard drive. Have everything saved there that I needed to save (I think). Doing upgrade to 10.10.

Edit 2:

Did upgrade to 10.10 but still unable to figure out the "Sound Recorder" problem. Still shows the same message as noted in first posting. Any help greatly appreciated.

---

### Post by flyfishingphil on 2011-08-13
Still looking for answer to Sound Recorder problem. Have spent the last several hours looking around Ubuntu but have found no answer to the problem:

GoTo Applications> Sound&Video> Sound Recorder and get this message:

[I]Could not create the GStreamer GConf audio recording element.
Please install the 'gconfelements' plug-in from the 'gst-plugins-good' module.
Verify that the installation is correct by running
gst-inspect-0.10 gconfaudiosrc
and then restart gnome-sound-recorder.[/I]

Any suggestions on how to get it working? Upgraded to 10.10 but still  having the same problem.

---

### Post by gordintoronto on 2011-08-13
I'm sorry, I don't advocate upgrading. I install with root and home as separate partitions, and do a fresh install of a new release. (Actually, on my primary computer, I am currently dual-booting 10.10 and 11.04, with 10.10 still as my "main" OS. I plan to replace 11.04 with a fresh install of 11.10 when it reaches "release candidate" status.)

"Internal Audio Analog stereo as the input" sounds like it is pointing to the built-in mic. There should be a drop-down list of devices. 

Have you played with Alsmixer? Audacity?

---

### Post by flyfishingphil on 2011-08-13
> **gordintoronto said:**
> I'm sorry, I don't advocate upgrading. I install with root and home as separate partitions, and do a fresh install of a new release. (Actually, on my primary computer, I am currently dual-booting 10.10 and 11.04, with 10.10 still as my "main" OS. I plan to replace 11.04 with a fresh install of 11.10 when it reaches "release candidate" status.)

"Internal Audio Analog stereo as the input" sounds like it is pointing to the built-in mic. There should be a drop-down list of devices. 

Have you played with Alsmixer? Audacity?
Wasn't thinking clearly when I did upgrade but was hoping I could overcome the VBox problems and recover some info in there too. That didn't work either. Also having problems now with Firefox browser I never had before (lots of shutdowns for no apparent reason. Unable to do anything in Pogo) and problems with the screensaver photo not showing correctly. 

Will probably have to get 10.04 on disc and do a total format- fresh install - to get back to where I had a working system with only minor problems. Not real impressed with what I've seen so far on 10.10 and, with the problems there, not sure I want to step up to 11.04. Looking thru the Absolute Beginner there seems to be lots of problems with that one too.

The Sound Recorder problems started with the last update, to 10.04, but that was the only problem from that. VBox problem had started a short time ago but hadn't found the info on correcting that yet.

Tried Audacity but no mic volume control so sound barely audible. Looked all over for settings but found none regarding that. Logitech mic/headset showed, speaker volume no problem, red light on mic on, but no recording of the sound. Same record level on internal mic, almost no sound at all. Haven't tried Alsmixer yet, but not counting on that either.

EDIT:
Currently downloading 11.04 and, when that finishes, will also download 10.04 so I can do a total format clean up and install of either. Couple of questions re 11.04 (if it works correctly):

1. With saving all of the files I need (I hope) will I be able to transfer the ones I work with all of the time back onto the desktop and work with them in 11.04? 

2. Are there any "tricks" I need to know to transfer these files so they are workable in 11.04?

3. Are files like HP 3.11.5 workable, in 11.04, so I can connect to my WiFi HP printer?

I know I'll need to do some updating once the 11.04 is installed, and get a couple of the programs I use, like BlueFish Editor, but is there anything else I might need to do to make the transition easy?

Thanks for the prep help.

---

### Post by flyfishingphil on 2011-08-14
No need for assist. Gave up on the upgrade to 10.10 and went for a full clean install of 11.04. Seems to be working well, have everything I need to continue with what I was doing in production, now just need to learn the "style" of Naughty desktop and get used to the different operational pattern. Impressed so far, just need to learn "new methods".

---

### Post by gordintoronto on 2011-08-14
Thanks for letting us know!

---

