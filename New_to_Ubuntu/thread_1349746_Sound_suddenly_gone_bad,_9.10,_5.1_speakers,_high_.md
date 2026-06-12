---
title: "Sound suddenly gone bad, 9.10, 5.1 speakers, high pitched screech"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by jotto! on 2009-12-08
What have I done now?
Whilst helping a friend with a laptop sound issue, I downloaded alsa mixer and then uninstalled it. My friend had issues with sound being played through speakers whilst headphones plugged in. Anyway, solved that for him with said alsamixer but now my sounds have gone mad...can hear music playing but it is distorted with a high pitched screech!

Any ideas what I might have done? :confused:

---

### Post by jotto! on 2009-12-08
ok, have found that sound gets better just for a second or less if I close an app or browser window....
Any ideas? Any command I can type in to terminal to check what drivers etc Im using?

---

### Post by jotto! on 2009-12-09
I know sound has been an issue but any ideas???

---

### Post by SteveNorman on 2009-12-09
you is alsamixer installed or not right now?

print the output of

```
aplay -l
```

and what happens when you do

```
speaker-test
```?

---

### Post by jotto! on 2009-12-09
Alsa mixer is not installed at the moment.


output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

And from speaker test I get
speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.189892
 0 - Front Left
Time per period = 11.171179
 0 - Front Left
Time per period = 11.156625
 0 - Front Left
Time per period = 11.158452
 0 - Front Left
Time per period = 11.144964
 0 - Front Left
Time per period = 11.175777
 0 - Front Left
Time per period = 11.188185
 0 - Front Left
Time per period = 11.163227
 0 - Front Left
Time per period = 11.165164
 0 - Front Left
Time per period = 11.125367
 0 - Front Left
Time per period = 11.172646
 0 - Front Left
Time per period = 11.216457
 0 - Front Left
Time per period = 11.204365
 0 - Front Left
Time per period = 11.201596
 0 - Front Left
Time per period = 11.234093
 0 - Front Left
Time per period = 11.121252
 0 - Front Left
Time per period = 11.210258
 0 - Front Left

I get noise from each of my speakers although the rear speakers are louder than the fronts.
Running a 5.1 speaker system.
And it would keep going if I didnt close the terminal.

What do the speaker test results show, ie what do the numbers mean?

---

### Post by jotto! on 2009-12-09
OK, so this is getting weird.

I put a CD in the drive ( music ) and it played pefectly! Tried games and the sound was good. Thought it must just have been a glitch and it had cleared itself.
Re-booted and sound was bad again. Tried playing CD and now it wont even read the cd.

Tried another CD and it played first time but with screech.

Tried changing the speaker configuration. Weird, sound is gone on every config APART from 5.1!!!!!

Can use stereo, 4.0, 4.1, 5.0 but not 5.1....what is going on here!!!!!!

---

### Post by SteveNorman on 2009-12-09
Sorry, had to get some sleep. The speaker test is just to show that they work. Try this one as well,

```
speaker-test -c2 -l1 -twav

```


It should speak through each speaker. You may have to alter your alsa config file to include modules for your the surround sound, effect. Let me dig and Ill look.

also in the meantime if you could post the output of
```
asoundconf list
```

---

### Post by SteveNorman on 2009-12-09
Found it, 

This worked for a friend of mine,

If you have a .asoundrc file add the following to the bottom. If you dont have one this will create one. I dont think you need to add permissions to config files, but if it doesnt work I would try that afterwards.

```
sudo gedit ~/.asoundrc
```




paste this in to the bottom


```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

---

### Post by jotto! on 2009-12-10
Ok, I changed the c2 to c6 in the first piece of code and the spoken voice was heard through all speakers.

Here is where it gets weird again!
I tried varying the volume and balance through the speakers and that seems to help.

Tried the 2nd command and it wasnt found so will install it as you suggest.

Is it easy enough to uninstall if it doesnt help?
Thanks for your patience!

---

### Post by jotto! on 2009-12-10
right,
When I typed in command asoundconf list
I get command not found.

I didnt have an .asoundrc file so I typed in the command 
sudo gedit ~/.asoundrc

And pasted the code 
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
in to what essentialy was an empty file. This code is now all that is in the .asoundrc file.

What do I do next? Im still having the same issues.

I thought when I first installed ubuntu it was working fine so I decided to just boot from the cd and see what happened. Same problem.

Perhaps its a code fault within ubuntu?

Its weired how the sound dissappears if I select any other speaker arrangement.

---

### Post by SteveNorman on 2009-12-10
Its most likely a driver issue. I am used to dealing with alsa, and I am pretty sure 9.10 uses pulse. I will read up on pulse audio fixes and get back to you. You may want to post this in multimedia and video as well. They are a little more specialized there.

BTW its not uncommon to have an empty sound config file, so  your good on that end.

---

### Post by jotto! on 2009-12-10
Thanks for the help Steve.

Here is an interesting thing to add to the mix.

If I open a sound file in rhythmbox and then open another one in totem the distortion goes! If I mute one of the applications, the sound remains perfect.
As soon as I close one of the running applications down it gets distorted again.

---

### Post by SteveNorman on 2009-12-10
If your gonna use pulse you may want to read through this. Personally I have had so many problems with Pulse I stopped using it and went 100% alsa. No problems since. I dont think that is advice I really feel comfortable giving though, as others seem to like Pulse, and seem to have no problems with it. With all things computers, you millage may vary. I will be back on tonight and will try to be more helpful.

---

### Post by l-x-l on 2009-12-11
> **SteveNorman said:**
> If your gonna use pulse you may want to read through this. Personally I have had so many problems with Pulse I stopped using it and went 100% alsa. No problems since. I dont think that is advice I really feel comfortable giving though, as others seem to like Pulse, and seem to have no problems with it. With all things computers, you millage may vary. I will be back on tonight and will try to be more helpful.

How did you go 100% alsa? I'd like to do the same because I hate pulse.

---

### Post by SteveNorman on 2009-12-11
I just removed via synaptic pulse-audio and all things pulse, then completed the process using the technique I posted above, locate and updatedb the remove it all. I am using crunch-bang now as my primary distro, its alsa only. I believe the last few ubuntu releases have an option in your settings to choose which app to use, either alsa or pulse, not sure about 9.10 yet. Upgraded my ubuntu partition but havnt really played with it yet.

5.1 speakers are still a problem with both pulse and alsa, the most success stories I have seen involve a stock pulse working out of the box, or adding the entry to the ~/.asoundrc file (creating it if necessary) then rebooting and checking theoption which should then appear in whatever manager they are using, either alsamixer or pulseaudio manager.

---

### Post by jotto! on 2009-12-11
I found a thread on how to uninstall pulse and install alsa but it also removed the speaker icon. It did install alsamixer as a volume control.

If I do the speaker test, I only hear the 2 front speakers.
I found a test that added a command dplug 5.1 or something similar and got sound from each speaker.

How do I now set alsa to 5.1 without it just copying front to back and 50% of Rand L to make Centre.

---

### Post by SteveNorman on 2009-12-12
do you still have the ~/.asoundrc with that block added in? that worked for me before after a reboot. On crunchbang they use gnome-volume-manager
Typing that in a terminal should either open or tell you the install command for it. It has options that will be made available in alsa by checking switches and channels. there is also a gui for alsa mixer: gnome-alsamixer should be in synaptic if it is not installed by default.

you may want to read through this as well

[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)

---

### Post by jotto! on 2009-12-12
I seem to have gone backwards....

I removed all of pulse and went to alsa. 
No matter what I tried I couldnt get 5.1.

SO

reinstalled pulse and at first I thought it was working like a dream...5.1 clear as a bell. Then when I closed down firefox it all went wierd again.
I the re opened all tabs I was browsing, played some music an it was good again. Checked in the sound properties under applications and saw totem being listed as well as [B]ALSA plug-in [firefox]

[/B]So, now my question is, how do I invoke the ALSA plug-in to start at boot? **OR** what simple command can I type in to make an ALSA only system default to 5.1 instead of stereo?

---

### Post by SR_ELPIRATA on 2009-12-12
jotto: I think I'm in the same boat as you do :( I have this awful sound as you describe and my only way out (after getting help on launchpad) was to return to 9.04 :(

I have an Asus M3A78-T and Im using the analog 5.1 plugs for my home theather. The sound would disappear at some points when raising the volume, and sometimes while playing with the volume controls, but at some point or a restart they would return again to my displeasure.

I would love to use 9.10 but sounds is very important, and that noise.... is horrible.

ELP

PS: Far as I could tell, 9.10 uses the hda-intel driver, whereas 9.04 and earlier used the HDA-ATI-SB Alsa mixer with flawless sound.

---

### Post by SteveNorman on 2009-12-13
Im out of ideas, If what was in my last post didnt help I would post in multimedia if you haven't already.

---

### Post by SR_ELPIRATA on 2009-12-14
You could try the launchpad too, and if they find a solution for you, please keep me in mind so that I can try it too.

ELP

---

### Post by strange_cathect on 2009-12-15
I was having this problem and resolved it by changing my sound hardware in the Volume Control.

I was using the 5.1 sound profile (which I have). But when I selected the Analog Surround 7.1 output, the screech went away (and my sound works perfectly).

Go to Applications | Sound and Audio | Volume control. Select the Hardware tab. And then select the 7.1 output profile from the drop box.

---

### Post by luckykip on 2009-12-23
Hey @strange_cathect

I had the same problem. A horrible screeching that seemed to get worse/better when fiddling with the individual speaker volumes. Now I've selected 7.1 instead of 5.1 the problem has disappeared!

Thank you so much - I thought my ears would eventually start to bleed...

---

### Post by SR_ELPIRATA on 2009-12-24
Interesting, thanks for the suggestion, will try and set another harddrive for that test. It kind of makes sense, the hardware is after all... 7.1, I only set it as 5.1 because that's what I use.

Lets see if it works for me!!!!

ELP

---

### Post by EricBelcastro on 2010-01-06
After updating to Karmic I have the high pitched squealing sound in my speakers as well - and any audio that is played is severely distorted. Alsa mixer levels seem normal. I don't have any 7.1 option under the hardware tab - Why might that be so?

---

### Post by SR_ELPIRATA on 2010-01-11
Same here Eric, I was hoping that strange's and Lucky's moving to 7.1 would help me as well, but I have no 7.1 option. I'm at the moment downloading a lot of updates so hopefully one of them will be that.... hopefully.

It would be nice if any of them could say what audio chipset they have.

ELP

---

### Post by StardustLuna on 2012-08-13
I've had the same problem. My sound will be working perfectly fine, then it turns into a garbled, pitchy mess. Usually closing the program and re-starting it works but sometimes it doesn't.

---

### Post by coffeecat on 2012-08-13
Old thread closed.

This thread is about an obsolete version of Ubuntu. If anyone needs help with a current version, please start a new thread.

---

