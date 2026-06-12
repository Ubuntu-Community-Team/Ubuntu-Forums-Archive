---
title: "Music and vids not working! plz help!!"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2009-01-31
ok, here it goes, iv been frantically searching the nets for some1 with a simaler problem, no dice. so i decide to post it here. first of all thank you for reading thiz. k, i have a dell insperon 1525 w/ 3gigs of ram, preloaded with vista XD anyway i got rid of vista and installed ubuntu 8.10 32bit, i then relized that my comp is 64bit! so i get the 64bit of ubuntu and install it, works fine un till i tried to listen 2 some music, XD. i downloaded the coders b4 i tryed the mp3's from add/remove, and now when i open ANY music player to play any mp3 or vid the window turns a shade of black, and i click the X and it asks me 2 force quit. not only is it not working, but ooo's slide shows where lagging alot! compiz works vary nicely, and i tryed to install java 6 to hopefully fix ooo, it didn't, but then aftor the comp being on 4 about 3 days, my mp3's worked! i was so happy and i restarted just to make sure, but when i restarted a whole bunch of words came up on the screen after the upsplach, i got worried, but then the log on came back on, i log in to find that my mp3's don't work again! =( i got really pissed and searched the nets 4 an answer, and here i am, plz help!!!

Update: restarted, lines did not show up, but, no dice, it music and vids still do not work
Update 2: reinstalled coders for mp3, not working so far, can some1 help me?
Update 3: ok, i got it to work, but only when i restart x untill the sond works, this is not a problom with the sond drivers, cuz sometimes the sond works but music dont, can some1 help me out? thx
up 4 : nvm, it dont work any more, idk how it worked last time, just my luck, can some1 help me plz? PLZ I DONT WANT TO W8 4 9.4!!!!!!!!
up 5: im updateing to ubuntu studio now fallowing this gide [http://ubuntuforums.org/showthread.php?t=1005130](http://ubuntuforums.org/showthread.php?t=1005130)
im hopeing this fixes it!!

---

### Post by stderr on 2009-01-31
Hi. Well I have no idea regarding your specific problem. However it may help me and others if you post theo utput of the following terminal commands:

aplay -l
lsmod | grep snd

also what graphics card do you have?
Cheers

---

### Post by SchindlerShadow on 2009-01-31
> **stderr said:**
> Hi. Well I have no idea regarding your specific problem. However it may help me and others if you post theo utput of the following terminal commands:

aplay -l
lsmod | grep snd

also what graphics card do you have?
Cheers
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Red"]Linux-laptop:~$ lsmod | grep snd[/COLOR]
snd_hda_intel         492336  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm



and thx for replying! and its a dell insperon 1525 laptop 3 gigs of ram

---

### Post by stderr on 2009-01-31
To be honest quite pissed right now but I'll look into this tomorrow! When you go to System->preferences->sound is pulseaudio selected or Alsa?

---

### Post by SchindlerShadow on 2009-01-31
> **stderr said:**
> To be honest quite pissed right now but I'll look into this tomorrow! When you go to System->preferences->sound is pulseaudio selected or Alsa?

ALSA PCM, is that good?

ok i tryed test but it froz w/ an errer ;(

gconfaudiosrc ! audiocovert ! audiosample !
gconfaudiosink profile=chat: Failed to connect stream: invalid argument

(had 2 type it cuz it froz, and got the same w/ pulseadio)

---

### Post by SchindlerShadow on 2009-01-31
> **SchindlerShadow said:**
> ALSA PCM, is that good?

ok i tryed test but it froz w/ an errer ;(

gconfaudiosrc ! audiocovert ! audiosample !
gconfaudiosink profile=chat: Failed to connect stream: invalid argument

(had 2 type it cuz it froz, and got the same w/ pulseadio)

updated to ubuntu studeo, music and vids still dont work, but it looks cool!

---

### Post by hansdown on 2009-01-31
Hi SchindlerShadow.

This site is one of the best for setting up ubuntu.

[http://www.stchman.com/](http://www.stchman.com/)

---

### Post by SchindlerShadow on 2009-01-31
> **hansdown said:**
> Hi SchindlerShadow.

This site is one of the best for setting up ubuntu.

[http://www.stchman.com/](http://www.stchman.com/)

thx 4 the suggestion but this dosent help me, its not about setting up ubuntu, the programs crash when i try 2 listen to music or wach vids. thx anyway!

---

### Post by SchindlerShadow on 2009-02-01
bump? i need music and vids! whats the use of ubuntu studio w/o music and vids? :(

---

### Post by XanTrax on 2009-02-01
> **SchindlerShadow said:**
> bump? i need music and vids! whats the use of ubuntu studio w/o music and vids? :(

Hi, please run this command:

```

sudo lshw -C sound

```

and post the output. Thank you.

---

### Post by oregonbob on 2009-02-01
Pardon me, I had to chuckle reading your post as I am having all the same problems.

I have read many times, "If your system is 64 bit then you should install 64bit software". But what that does right away is 1) some vendors don't have 64bit version yet 2) 64bit don't work at all on so-so software, on and on.

Music and sound is one area of Ubuntu that needs user-friendly real bad. If I aramok it works then stops, if I Hydrogen it works unless before it I ran software A, but forgot to start daemon B, but if I want to use application C there is a major conflict with driver D that comes with daemon C, but not with E which can be downloaded from site F, 500MB at 2k/sec.

I am going to read the long tutorial,
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
And pass along any success.

Good luck, you are not alone. Just wait till you want to play with midi, synthesizers, recorders, above two dimensional problem becomes 4 dimensional.

---

### Post by SchindlerShadow on 2009-02-01
> **XanTrax said:**
> Hi, please run this command:

```

sudo lshw -C sound

```

and post the output. Thank you.

 sudo lshw -C sound
[sudo] password for: 
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

thx 4 helpin

---

### Post by SchindlerShadow on 2009-02-01
> **oregonbob said:**
> Pardon me, I had to chuckle reading your post as I am having all the same problems.

I have read many times, "If your system is 64 bit then you should install 64bit software". But what that does right away is 1) some vendors don't have 64bit version yet 2) 64bit don't work at all on so-so software, on and on.

Music and sound is one area of Ubuntu that needs user-friendly real bad. If I aramok it works then stops, if I Hydrogen it works unless before it I ran software A, but forgot to start daemon B, but if I want to use application C there is a major conflict with driver D that comes with daemon C, but not with E which can be downloaded from site F, 500MB at 2k/sec.

I am going to read the long tutorial,
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
And pass along any success.

Good luck, you are not alone. Just wait till you want to play with midi, synthesizers, recorders, above two dimensional problem becomes 4 dimensional.

thx XD

---

### Post by XanTrax on 2009-02-01
> **SchindlerShadow said:**
> sudo lshw -C sound
[sudo] password for: 
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

thx 4 helpin

Please go to 

System -> Preferences -> Sound

And where it says 

-**Sound Events**
-- Sound Playback: Autodetect

Please change autodetect to

"HDA <some text> ( ALSA )"

And then press test.

---

### Post by SchindlerShadow on 2009-02-01
> **XanTrax said:**
> Please go to 

System -> Preferences -> Sound

And where it says 

-**Sound Events**
-- Sound Playback: Autodetect

Please change autodetect to

"HDA <some text> ( ALSA )"

And then press test.

ok, their is 2 diff ones, one that says hdmi, and another with analog, analod gives the same errer i said in the other post, and hdmi show that its testing, but i dont hear anything, i think its the sond that comes out of the hdmi (i have an hdmi port on my laptop) ima try it when i find time, thx

edit: omg i got it to work i tryed the 1st hda <something> analog (oss) ima try restarting the comp.

---

### Post by XanTrax on 2009-02-01
> **SchindlerShadow said:**
> ok, their is 2 diff ones, one that says hdmi, and another with analog, analod gives the same errer i said in the other post, and hdmi show that its testing, but i dont hear anything, i think its the sond that comes out of the hdmi (i have an hdmi port on my laptop) ima try it when i find time, thx

edit: omg i got it to work i tryed the 1st hda <something> analog (oss) ima try restarting the comp.

I was going to say if ALSA didnt work to try OSS.  OSS is open sound system so I figured it would have worked.

---

### Post by SchindlerShadow on 2009-02-02
> **XanTrax said:**
> I was going to say if ALSA didnt work to try OSS.  OSS is open sound system so I figured it would have worked.

thx! and how do i mark the thread as solved? lol

---

