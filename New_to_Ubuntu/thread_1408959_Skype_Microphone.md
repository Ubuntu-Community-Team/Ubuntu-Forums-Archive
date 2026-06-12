---
title: "Skype Microphone"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-02-17
After many hours of stress, I finally got skype with video working in Ubuntu 9.10 Karmic. Video worked great, but people on the other end kept saying that they could hear me trying to talk, but it was choppy and I kept going in and out. I googled getting my microphone to work (since it must have to a degree since it was capturing SOME audio) and I got the microphone working great, but then my webcam stopped transfering video so I could see the other person, but they couldn't see me. I have no problem seeing and hearing whoever Im skyping, but it seems only the microphone or the camera work at the same time. Both seem to be installed fine and when I rebooted my computer the webcam began working again, but the mic went out.

---

### Post by superprash2003 on 2010-02-17
could it be bandwidth? do you have good internet speeds? try disabling skype to automatically start webcam , then audio chat for a few seconds and then manually start webcam

---

### Post by Captainflowers91 on 2010-02-17
bandwidth isn't the problem because my friends are perfectly fine skyping who run windows and when I reboot and run windows 7 skype works fine. I will try starting without the video on and see how that goes. Last night however me and a friend got both my audio and video working on his end, but I couldn't see him. Its just one problem after another

---

### Post by penguinv on 2010-02-17
Does skype work on Ubuntu? Or not?

Are there any positive stories?

---

### Post by Cuba71 on 2010-02-17
> **penguinv said:**
> Does skype work on Ubuntu? Or not?

Are there any positive stories?

I have Skype working in Ubuntu 9.10 Karmic with a C-600 webcam from Logitech

---

### Post by Captain_tux on 2010-02-17
I haven't been able to get Skype to work on Ubuntu since Hardy... I installed it on openSUSE and it works like a charm.

---

### Post by bofak on 2010-02-18
> **Cuba71 said:**
> I have Skype working in Ubuntu 9.10 Karmic with a C-600 webcam from Logitech

Congratulations!  Could you please tell us how you did it?

At this point, what is infuriating me most about this Skype fiasco is the sheer amount of time I've wasted on it.  I'd be content just to get the mic working; forget about the luxuries of webcam.

Final plea:  Is there anyone out there with the technical expertise to give us a CLEARLY WRITTEN tutorial on how to do it?  No guesswork, just plain ol' expertise.

[Is my frustration beginning to show, or what?  :mad: ]

---

### Post by nishant.singh28 on 2010-02-18
I never ( yes, NEVER ) had an issue with skype. It worked with my notebook's integrated webcam and mic, out of the box. Try  unchecking the option "Let skype set mixer levels" or similar. The thing gave me headaches even in Vista.

---

### Post by mörgæs on 2010-02-18
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Running Ubuntu 8.10, and Skype works fine. Have not tried the webcam, though.

---

### Post by eumetaxas on 2010-02-19
the camera is fine after upgrading to 9.10 but i have serious sound issues.

---

### Post by mörgæs on 2010-02-19
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by bofak on 2010-02-20
> **mörgæs said:**
> [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Thanks, mörgæs, that is an excellent wiki.  Unfortunately it doesn't cover the microphone problem that so many of us are having.

---

### Post by mörgæs on 2010-02-21
Is the microphone completely dead, or is the sound from it just so weak that it appears to be? 

In Ubuntu 8.10 Alsamixer has some important settings for "capture", first of all a "+ 20 dB boost" switch for the microphone. If it is the same in 9.10 it might be worth a try.

---

### Post by bofak on 2010-02-21
[QUOTE=mörgæs;8859152]Is the microphone completely dead, or is the sound from it just so weak that it appears to be? 

The mic is completely dead.  It's a good mic -- it works fine on my wife's Windows computer.

---

### Post by laidback on 2010-02-21
This may help/be of interest

[http://ubuntuforums.org/showthread.php?t=1306561&highlight=skype](http://ubuntuforums.org/showthread.php?t=1306561&highlight=skype)

---

### Post by J V on 2010-02-21
> **nishant.singh28 said:**
> I never ( yes, NEVER ) had an issue with skype. It worked with my notebook's integrated webcam and mic, out of the box. Try  unchecking the option "Let skype set mixer levels" or similar. The thing gave me headaches even in Vista.
what he said... in karmic the only option is pulseaudio, and almost all webcams will work in linux... so it should just work...

Unless the problem is in the OS, but again, in karmic pulse is all thats left so settings are much easier... It depends on your system.

---

### Post by mörgæs on 2010-02-21
> **bofak said:**
> 
The mic is completely dead.  It's a good mic -- it works fine on my wife's Windows computer.

I meant: Is it also dead after you give microphone / 'capture device' full throttle in Alsamixer, including the + 20 dB switch?

---

### Post by bofak on 2010-02-22
Thanks, guys, for your continued attempts to help me.  That's what I like about the Linux world.

JV, I tried unchecking the option "Let skype set mixer levels", but it didn't help.

Laidback, thanks for bringing my attention to that other thread -- I wasn't aware of it.  It seems this crazy problem has been going on ever since the release of Karmic (just run a Google on "Skype in Ubuntu 9.10" to see the extent of it!)  I'll continue to play with the ideas in that thread, but it seems that many people (including me

---

### Post by bofak on 2010-02-22
Sorry -- my message somehow got posted when only half written!  Here it is in full:

Thanks, guys, for your continued attempts to help me.  That's what I like about the Linux world.

JV, I tried unchecking the option "Let skype set mixer levels", but it didn't help.

Laidback, thanks for bringing my attention to that other thread -- I wasn't aware of it. It seems this crazy problem has been going on ever since the release of Karmic (just run a Google on "Skype in Ubuntu 9.10" to see the extent of it!) I'll continue to play with the ideas in that thread, but it seems that many people (including me :sad: ) have already wasted too much time on it.  The best solution might be to wait for the appearance of new versions of Ubuntu and/or Skype -- the problem may then be fixed.

The short-term solution may be to borrow my wife's Winsows computer ;-)

---

### Post by ectospasm on 2010-02-22
I got Skype working on mine (Logitech webcam 3000, I think).  Didn't have to do much, but assign the webcam's mic as the pulseaudio source.  The current version of Skype I'm using ((beta)2.1.0.81) is only able to use the local pulse device, so assigning the source correctly was necessary.  Another thing about my mic, maxing out the gain (volume) on it has the effect of muting it, not just for Skype but for any audio.

Setting the PulseAudio devices is much easier if you install the PulseAudio Device Chooser (padevchooser).  Not sure if this is installed by Karmic by default, it may be leftover from my Intrepid install when I upgraded.  

Hope that helps!

---

### Post by mörgæs on 2010-02-25
> **bofak said:**
> The best solution might be to wait for the appearance of new versions of Ubuntu and/or Skype -- the problem may then be fixed.



10.04 is already here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is still in alpha, but surprisingly stable. I have not tried Skype on it, though.

---

### Post by ectospasm on 2010-03-02
I just verified my instructions with a new machine (same webcam).  To get the mic working, I did the following:

[LIST=1]
[*]Install padevchooser (it's not installed by default).  
```
$ sudo aptitude -y install padevchooser
```
[*]Run padevchooser and put it in the background
```
$ padevchooser &
```
[*]Notice the padevchooser icon in the taskbar (looks like a stereo 1/8" miniplug, plus a loop of wire)
[*]Click on the padevchooser icon and click "Manager".
[*]Click on the Devices tab.
[*]Under the Sources list, look for your microphone.  Select it and click "Properties".
[*]On the "Basic" tab, you'll see the full name of your mic.  Triple-click the text to the right of the "Name:" tag, and copy it to your clipboard (it's already in the select buffer--just put it where you can get to it easily).
[*]Close the source properties and the manager windows.
[*]Click on padevchooser again, and choose "Default Source/Other"
[*]In the resulting "Other Source" window, paste the text we grabbed from the "Manager/Source Properties" windows, and click OK.
[*]Go to the options for Skype, and choose "Sound Devices".  Make sure "Allow Skype to automatically adjust my mixer levels" is NOT checked.  I had a problem with Skype maximizing my mixer level for the mic, and this had the effect of muting it.
[*]Make a test call, see if it will record anything.  Be sure to wait long enough, if you stop too early you won't hear your playback.
[/LIST]

HTH

---

### Post by spiderbatdad on 2010-03-02
I use skype all the time on Karmic.
I do not use padevchooser
Instead I solved the microphone issue this way:
First, do not let skype adjust mixer levels...doing so will reset the following and mic will not work.
Next. Go to Applications>>Sound & Video>>PulseAudio Volume Control.
Choose the "input devices" tab
Click the shield or lock symbol to unlock the two sliders so they do not move together. Slide one completely off, leave the other at 100%.
This is what works for me.

---

### Post by Neezer on 2010-03-02
I am definitely going to try these last two posts this evening. I'm at work now. I will try them in 9.10 and 10.04 alpha. I can tell you that mine hasn't worked on 10.04A3 out of the box either.

---

### Post by Arijit_Kundu on 2010-03-02
I use skype in 9.10 without any problem. 
For microphone : try installing alsamixer (sudo apt-get install alsamixergui), run alsamixer in terminal, press left button and tab to browse through the devices, any mic / front mic you'll see, set them to 100. Press Esc to close it. It should work now.

---

### Post by scottro on 2010-03-18
An install of Lucid from the alpha 3 with all upgrades works. 

An install from the nightly build (318 build) doesn't.  

Odd.

EDIT:  

I just realized that I'm using different versions of Skype on the two.  On one, I used the binary from the Skype web site. On the other (the working one), the binary kept showing up as corrupted, so I used a solution from launchpad, adding a Debian version.  That might be the cause of the difference.  (They're two netbooks, both ASUS, one a 1000HE and the other 1005HA.

---

### Post by scottro on 2010-03-21
To add to this, using weemat's solution from [http://ubuntuforums.org/showthread.php?t=1316929](http://ubuntuforums.org/showthread.php?t=1316929) worked for me.   

In a nutshell, install pavdevchooser, then go to Applications, Sound and Video, Pulse Audio Volume Control.

Choose the Input tab. To the left of the green checkmark, there's an icon that looks meaningless, at least to me.  Click it and it unlinks left and right.  Slide one of them to the left and the other to the right--it doesn't seem to matter which.  They don't have to be fully right or left, simply unlinked and in different places.  

Then, the microphone worked for me in Skype.  Oddly enough, on the 1000HE, which seems to have the same hardware, I didn't have to do this, sound, including the mike in Skype, worked out of the box. (As per my above post, I had used a different version of Skype, but changing the version I was using didn't make a difference--the 1000HE works out of the box, the 1005HE requires this trick.)

---

### Post by xx58 on 2010-03-21
:rolleyes:OK, I think in this situation have many problems. If you use Ubuntu 9.10, then I recommended do next:
  	 	 	 	 	 	  Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!
 Only after that you can put work Skype.
If you have Skype Beta Version, then:
go to output volume control:
  	 	 	 	 	 	  Skype  
 

 
[LIST=1]
[*]Sound in
 	VoipVoice USB Phone (plughhw;phone,0)[COLOR=Red] (your microphone)[/COLOR]

[*]Sound Out
 	VoipVoice USB Phone (plughhw;phone,0)[COLOR=Red] (your headset)[/COLOR]

[*]Ringing
 	HDA Intel (hw;Intel,0)
[/LIST]
 

 Voice adjustment – Sound Preferences
 

 
[LIST=1]
[*]Hardware
 	V-654 Composite Device
 	1 Output / 1 Input
 	Analog Stereo Output + Analog Mono 	Input
[/LIST]
 

 Input
 

 
[LIST=1]
[*]V-654 Composite Device Analog Mono
[/LIST]
 

 Output
 

 1. V-654 Composite Device Analog Stereo Stereo


Only then go to Skype - option - sound Devices
I hope it was helpful

---

### Post by rs87424 on 2011-02-16
> **xx58 said:**
> :rolleyes:OK, I think in this situation have many problems. If you use Ubuntu 9.10, then I recommended do next:
  	 	 	 	 	 	  Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!
 Only after that you can put work Skype.
If you have Skype Beta Version, then:
go to output volume control:
  	 	 	 	 	 	  Skype  
 

 
[LIST=1]
[*]Sound in
 	VoipVoice USB Phone (plughhw;phone,0)[COLOR=Red] (your microphone)[/COLOR]

[*]Sound Out
 	VoipVoice USB Phone (plughhw;phone,0)[COLOR=Red] (your headset)[/COLOR]

[*]Ringing
 	HDA Intel (hw;Intel,0)
[/LIST]
 

 Voice adjustment – Sound Preferences
 

 
[LIST=1]
[*]Hardware
 	V-654 Composite Device
 	1 Output / 1 Input
 	Analog Stereo Output + Analog Mono 	Input
[/LIST]
 

 Input
 

 
[LIST=1]
[*]V-654 Composite Device Analog Mono
[/LIST]
 

 Output
 

 1. V-654 Composite Device Analog Stereo Stereo


Only then go to Skype - option - sound Devices
I hope it was helpful
I have Ubuntu 10.10 and my computer has a built in microphone would this work on my computer as well?

---

### Post by rs87424 on 2011-02-22
^ Yeah

I have done many of the methods mentioned before and I also have Maverick and I have an internal microphone for my computer (Acer Aspire)

I adjusted the sliders for the audio so that they don't move together and every time they somehow magically pop back together and I can't keep them from cancelling each other out and silencing my microphone.

---

### Post by rs87424 on 2011-02-28
I don't know if anyone else has had this happen to them or not, but I realize when I installed the google talk application a while back Skype refused to work properly no matter how hard I worked on it. 

My suggestion with Skype: Look at all applications and extensions including Google talk to analyze the problem.

---

### Post by brallan on 2011-02-28
i also had problems installing google-talk. were you using the skype beta or the old deb?

---

### Post by rs87424 on 2011-02-28
> **brallan said:**
> i also had problems installing google-talk. were you using the skype beta or the old deb?
I believe at the time it was the beta

---

### Post by Phelixfil on 2011-03-23
Did you get an answer to your Skype problem,  I am having similar problems and pretty lost.  Any ideas gratefully received.
Cheers,
P

---

### Post by rs87424 on 2011-03-23
Well it seems to work now that I don't have google talk installed anywhere on my system. But I feel that something will stop working again so I just use skype in Windows because I don't want to work on this faulty beta skype in Ubuntu anymore because apparently a newer version of Skype should come out that works.

---

### Post by PSBTornado on 2011-03-23
> **rs87424 said:**
>  because I don't want to work on this faulty beta skype in Ubuntu anymore because apparently a newer version of Skype should come out that works.
I went to install it this morning and it's gone. Perhaps the new version is imminent? What do you guys think?

---

