---
title: "Taking It From The Top"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by AlyKat on 2011-08-28
I am so completely over windows and am ready to install ubuntu, but man, I have no idea where to begin!

Is there a checklist I can compare my system against to see if I might have issues?
I have a linksys wireless pci card, but not sure of the model. How do I find it? (without opening the case if possible)
Where can I find a list of compatible programs?
Will the ubuntu install give me the option to format the hdd?
Will my external hdd be recognized by ubuntu?


Any and all would be much appreciated! :D

---

### Post by ubudog on 2011-08-28
Welcome to the world of Ubuntu!  To answer your questions:
1.  What kind of computer do you have?  Nowadays, most computers are supported by Ubuntu.

2.  The wireless card is internal, right?  (not an adapter)  If so,  look up the specs of your computer, and it should say the model.

3. Some good programs for Ubuntu include: [http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)

4. Yep!  You can choose to dual-boot (keep Windows, and install Ubuntu, giving you an option on startup), or format the HDD completely (remove Windows, install Ubuntu).

5. Sure!  Is it USB?

Let us know if you have any more questions!  :-)

---

### Post by flyfishingphil on 2011-08-28
Just a quick thought. Before you install it you can "test drive" it to see if you like it, or not.

If you have 11.04 on a cd all you need to do is set that in the cd drive and shut down the computer. When you start it up it will offer you the selection of "Test" or "Install". This gives you the chance to check it out.

When you install you can have the choice of "sharing" your drive with Win$ and Ubuntu or doing a "clean" install. Ubuntu will format the drive and take you thru the steps. Be patient, answer the questions as they come up and allow the install to go thru its paces.

If I can do anybody can!

Welcome to Ubuntu and, once you get used to it, you'll wonder why you stayed with Win$ fo so long!

---

### Post by ubudog on 2011-08-28
Great advice! 

I also would recommend running Ubuntu for a bit (perhaps 1 hour) from a LiveCD, to make sure it works.  :-)

---

### Post by AlyKat on 2011-08-29
> **ubudog said:**
> Welcome to the world of Ubuntu!  To answer your questions:
1.  What kind of computer do you have?  Nowadays, most computers are supported by Ubuntu.

2.  The wireless card is internal, right?  (not an adapter)  If so,  look up the specs of your computer, and it should say the model.

3. Some good programs for Ubuntu include: [http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)

4. Yep!  You can choose to dual-boot (keep Windows, and install Ubuntu, giving you an option on startup), or format the HDD completely (remove Windows, install Ubuntu).

5. Sure!  Is it USB?

Let us know if you have any more questions!  :-)

It was a custom build I put together years ago for testing purposes (but now actively use because my main rig **** the bed)...AMD Athlon64 3800+, Asus MOBO with nvidia GeForce6150 LE chipset, 1gb memory

It's a Linksys Wireless-G PCI Adapter.

In regards to compatible programs - my question was more along the lines of "Will itunes work? Frostwire? AVG? Plants vs Zombies?"

I noticed on the first page a couple posts regarding nvidia video drivers - should I pre-download these and save them to the ex-hdd first?

Also, is there a manual somewhere that gives me a list of all the terminal commands (what they do, when to use them)?

---

### Post by HarrisonNapper on 2011-08-29
> **AlyKat said:**
> It was a custom build I put together years ago for testing purposes (but now actively use because my main rig **** the bed)...AMD Athlon64 3800+, Asus MOBO with nvidia GeForce6150 LE chipset, 1gb memory

It's a Linksys Wireless-G PCI Adapter.

In regards to compatible programs - my question was more along the lines of "Will itunes work? Frostwire? AVG? Plants vs Zombies?"

I noticed on the first page a couple posts regarding nvidia video drivers - should I pre-download these and save them to the ex-hdd first?

Also, is there a manual somewhere that gives me a list of all the terminal commands (what they do, when to use them)?

1. Hardware: There are a number of compatibility lists out there. Best thing is just to search the name of the hardware followed by "linux compatibility" or "ubuntu compatibility" or just "ubuntu" to see if there are a bunch of posts on these forums dealing with problems.

2. Applications: [http://www.winehq.org/](http://www.winehq.org/) and you can also have a Windows machine in VirtualBox (though be warned that either of these solutions may not work for some things). Plants vs. Zombies and other web applications should work fine.

3. No, you can just use the Additional Drivers program in System>Administration to change driver. Make sure you do all of your updates first.

---

### Post by AlyKat on 2011-08-30
I really appreciate the help so far and I only have one more question. Promise!

After I run the installer, what do I do?

Normally I'd get networking going, then a browser, then updates on EVERYTHING (but that's in windows where you just point 'n click). Does ubuntu come with a native browser? Obviously it must have something, otherwise you go in circles asking 'how do I install a browser without a browser!?'

I know about Wine and all the addons, but the basics is where I am lacking.


Oh, I did open the case and learned the wireless card is WMP54G v4.1, which according to the internets, is compatible. Right?

---

### Post by JKyleOKC on 2011-08-30
> **AlyKat said:**
> Normally I'd get networking going, then a browser, then updates on EVERYTHING (but that's in windows where you just point 'n click). Does ubuntu come with a native browser? Obviously it must have something, otherwise you go in circles asking 'how do I install a browser without a browser!?'My 10.04 came with Firefox by default; I don't know whether that's still true for the latest version but if it's not Firefox there will be something else -- possibly a renamed Firefox such as Seamonkey. You should definitely run the updating program -- but you don't have to search the web for it. As I recall it will run automagically as one of the first things when you reboot after doing the installation, and it will show an amazing number of updates (more than 200 for me last time I installed, since the updating process for *buntu systems is centralized). Just be patient and let it do its thing.

Depending mostly on your specific monitor, you might run into display problems, but they're usually pretty easy to solve. The main cause of these is the fact that many monitors don't generate accurate EDID responses, which leaves the video drivers in a quandary of how to generate the screen. It's been made more complex recently by changes in the standard display system (xorg-server) and the symptom is a black screen. However you'll find lots of help if that should happen, and it doesn't happen to everyone...

Welcome to the party!

---

### Post by AlyKat on 2011-08-30
> **JKyleOKC said:**
> Depending mostly on your specific monitor, you might run into display problems, but they're usually pretty easy to solve. The main cause of these is the fact that many monitors don't generate accurate EDID responses, which leaves the video drivers in a quandary of how to generate the screen. It's been made more complex recently by changes in the standard display system (xorg-server) and the symptom is a black screen. However you'll find lots of help if that should happen, and it doesn't happen to everyone...

Welcome to the party!


What can I do to avoid all of that^?

---

### Post by 3rdalbum on 2011-08-30
> **AlyKat said:**
> What can I do to avoid all of that^?

Relax, it's very rare and not worth worrying about. Cross that bridge if you come to it; I've not seen this happen for donkey's years.

Just to note, a few people here have pointed you towards Wine. Don't expect miracles from Wine - the reality is that probably about 20% of Windows programs work in Wine. No Windows drivers or low-level utilities (such as firewalls) work in Wine for obvious reasons. **Basically, use native Linux programs wherever possible.** Leave Wine as a last resort.

You can find literally thousands of free Linux programs from the Ubuntu Software Center program in Ubuntu. When I say "free", I don't mean trial versions or shareware; I mean 100% free.

Your first step is to try Ubuntu from the CD, see how it works on your hardware and then make the decision on whether you want to install it permanently. **Make sure you back up all your Windows data before running the Ubuntu installer** - it's also rare to lose data in the partitioning step, but it's more likely to happen if you don't have a backup :-)

---

### Post by AlyKat on 2011-08-30
> **3rdalbum said:**
> Your first step is to try Ubuntu from the CD, see how it works on your hardware and then make the decision on whether you want to install it permanently. **Make sure you back up all your Windows data before running the Ubuntu installer** - it's also rare to lose data in the partitioning step, but it's more likely to happen if you don't have a backup :-)

Windows seems to exist in it's own partition, but I think running from the cd first is turning out to be a better idea. If it works, then so long windows!

---

### Post by ubudog on 2011-08-30
> **AlyKat said:**
> Windows seems to exist in it's own partition, but I think running from the cd first is turning out to be a better idea. If it works, then so long windows!

Yeah, but if you want to keep your Windows stuff, (documents, music, etc.) then you should definitely have a good backup.  You can then remove Windows completely and install Ubuntu, copying back your stuff into Ubuntu.  :P

EDIT: And yeah, Ubuntu 11.04 comes with Firefox 4 or 5.

---

### Post by flyfishingphil on 2011-08-30
> **3rdalbum said:**
> Relax, it's very rare and not worth worrying about. Cross that bridge if you come to it; I've not seen this happen for donkey's years.

Just to note, a few people here have pointed you towards Wine. Don't expect miracles from Wine - the reality is that probably about 20% of Windows programs work in Wine. No Windows drivers or low-level utilities (such as firewalls) work in Wine for obvious reasons. **Basically, use native Linux programs wherever possible.** Leave Wine as a last resort.

You can find literally thousands of free Linux programs from the Ubuntu Software Center program in Ubuntu. When I say "free", I don't mean trial versions or shareware; I mean 100% free.

Your first step is to try Ubuntu from the CD, see how it works on your hardware and then make the decision on whether you want to install it permanently. **Make sure you back up all your Windows data before running the Ubuntu installer** - it's also rare to lose data in the partitioning step, but it's more likely to happen if you don't have a backup :-)

Totally agree! Tried working with wine but you can count on that about as much as you can count on a politician keeping his campaign promises!

Also tried VBox. Another laughing matter IMO. Gave up and found just about everything I need between the Software Center, Synaptics and various other sources. 

Now am a complete Ubuntu convert and no plans to ever return to the Win$ system or program.

---

### Post by decoherence on 2011-08-30
> **AlyKat said:**
> Also, is there a manual somewhere that gives me a list of all the terminal commands (what they do, when to use them)?

Here is a brief but handy introduction.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

On my system (Fedora, not Ubuntu) there are about 3500 terminal commands in my PATH (that the terminal will recognize automatically) and god knows how many scattered about elsewhere. There are only about a dozen commands that I use frequently but if I need another command and I'm not sure what it is, 'apropos' is a handy command that will return a list of other commands related to the keyword you supply. For instance 

```
$ apropos sound
alsactl (1)          - advanced controls for ALSA soundcard driver
alsamixer (1)        - soundcard mixer for ALSA soundcard driver, with ncur...
alsaunmute (1)       - a simple script to initialize ALSA sound devices
amixer (1)           - command-line mixer for ALSA soundcard driver
aplay (1)            - command-line sound recorder and player for ALSA soun...
arecord (1)          - command-line sound recorder and player for ALSA soun...
cdda2wav (1)         - a sampling utility that dumps CD audio data into wav...
default.pa (5)       - PulseAudio Sound Server Startup Script
icedax (1)           - a sampling utility that dumps CD audio data into wav...
jackd (1)            - JACK Audio Connection Kit sound server
pacat (1)            - Play back or record raw or encoded audio streams on ...
pacmd (1)            - Reconfigure a PulseAudio sound server during runtime
pactl (1)            - Control a running PulseAudio sound server
paplay (1)           - Play back audio files on a PulseAudio sound server
pitchplay (1)        - wrapper script to play audio tracks with cdda2wav wi...
play (1)             - Sound eXchange, the Swiss Army knife of audio manipu...
pulseaudio (1)       - The PulseAudio Sound System
rec (1)              - Sound eXchange, the Swiss Army knife of audio manipu...
sound-juicer (1)     - GNOME-desktop CD ripper and player using GStreamer
sox (1)              - Sound eXchange, the Swiss Army knife of audio manipu...
soxeffect (7)        - Sound eXchange, the Swiss Army knife of audio manipu...
soxformat (7)        - Sound eXchange, the Swiss Army knife of audio manipu...
soxi (1)             - Sound eXchange Information, display sound file metadata
Text::Soundex (3pm)  - Implementation of the soundex algorithm.

```

Now I can type 'man jackd' to find out more about the "JACK Audio Connection Kit sound server" (for example)

---

### Post by JKyleOKC on 2011-08-30
Perhaps I ought not have mentioned possible video problems; as others have told you, they're really not all that common. However they do seem to provoke the most panicked queries from those new to Ubuntu, when everything seems to go right and then all of a sudden they cannot get video to display anything. Or, as sometimes happen, it's just multicolored "snow" that bears no resemblance to anything reasonable.

Trying the "test" is the best idea as a first step.

---

### Post by rosencrantz on 2011-08-30
As you were mentioning iTunes: to the best of my knowledge, wine doesn't have USB support, so the most major problems we still have are with exotic external hardware and Mac/Windows only drivers/software. This might affect you if you own a recent iPhone/iTouch 4G (for earlier models there are very good workarounds). If you just use iTunes for playing and managing mp3s, there are excellent Linux solutions for that (amarok, exaile etc.)
It's also problematic if you are utterly and truly dependent on some high-powered software like Photoshop, arcane features of MS Office or most CAD programs. However, if you're a standard user, open-source standards like Open/LibreOffice or gimp should be sufficient for everything.
Edit: You also mentioned AVG (the virus scanner, right?) You don't actually need to run one, as a) there's no market value in writing linux viruses, b) the linux security hierarchy makes it almost impossible to write malware that can affect the system from outside. There is a Linux version for AVG, though, it can come in handy to check questionable files (or other people's computers) for Windoes malware.

---

### Post by madjr on 2011-08-30
> **AlyKat said:**
> 

In regards to compatible programs - my question was more along the lines of "Will itunes work? Frostwire? AVG? Plants vs Zombies?"


frostwire: is available for ubuntu, yes.

AVG: no need for antivirus in ubuntu/linux. Nor defraging, nor spyware.

Plants vs Zombies: is available in the **Google Chrome web store**. So yes, you can play it, just need to install chrome.

itunes: it has problems, because apple doesnt allow it, but there are some very good substitutes like **Banshee** for syncing/managing your music library, it even has lots of music available for free and purchasable DRM free.

> 
I noticed on the first page a couple posts regarding nvidia video drivers - should I pre-download these and save them to the ex-hdd first?


ubuntu should automatically detect and prompt to install these drivers. 

> 
Also, is there a manual somewhere that gives me a list of all the terminal commands (what they do, when to use them)?

you dont need to use the terminal very often in ubuntu. But yes, is good to know a few commands:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[http://www.youtube.com/watch?v=LabQTWylMCc&feature=related](http://www.youtube.com/watch?v=LabQTWylMCc&feature=related)
[http://www.youtube.com/watch?v=BOIbDKOXyR4&feature=related](http://www.youtube.com/watch?v=BOIbDKOXyR4&feature=related)


and last,
**Overall guide** to get started with ubuntu (must :)):
[http://www.youtube.com/watch?v=FIMO0eglEJA&feature=relmfu](http://www.youtube.com/watch?v=FIMO0eglEJA&feature=relmfu)

---

### Post by ubudog on 2011-08-30
A note on security in Ubuntu: You don't have to worry about random viruses, just use common sense, because you can get spyware that doesn't require root.  (If you follow every link, downloading everything you see)  

Just be sure to use common sense, and you'll be fine.

---

### Post by AlyKat on 2011-08-30
So the manual that was linked is all printed out. This'll make for some good morning reading!

-I use iTunes to load music onto my iDroid (I rooted my iTouch)...Banshee will let me do this, right?

-I have PS CS3 now, but as long as Gimp is decent, then no big loss.

-Everyone mentions running Ubuntu from a cd first when I do the test run...what about a thumb drive?

---

### Post by ubudog on 2011-08-30
> **AlyKat said:**
> So the manual that was linked is all printed out. This'll make for some good morning reading!

-I use iTunes to load music onto my iDroid (I rooted my iTouch)...Banshee will let me do this, right?

-I have PS CS3 now, but as long as Gimp is decent, then no big loss.

-Everyone mentions running Ubuntu from a cd first when I do the test run...what about a thumb drive?

Banshee should allow some sort of syncing, yes.

Hmm, depends what you will want to do.  GIMP is useful for many things, but it can't do everything PS can do.  You may however be able to run PS in Wine.  (check this out: [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop))

Sure!  Go to: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and there are instructions on how to install Ubuntu to a thumb drive in Windows, Mac, or Ubuntu.

---

