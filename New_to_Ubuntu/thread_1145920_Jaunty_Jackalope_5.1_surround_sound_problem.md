---
title: "Jaunty Jackalope 5.1 surround sound problem"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by JosephMarc on 2009-05-02
[SIZE=2]Hi,
I just recently did a fresh install of Ubuntu Jaunty final release and I tried to make my 5.1 altec lansing surround system work. I had a similar issue when I was under Intrepid, I could only hear the sound coming from 2 channels. So I followed the tutorial over here: [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

This worked for me on the previous release but now my problem persists, and I wasn't able to find help elsewhere.

Any help would be greatly appreciated
[/SIZE]

---

### Post by JosephMarc on 2009-05-02
[SIZE=2]Anyone?[/SIZE]

---

### Post by JosephMarc on 2009-05-03
[SIZE=2]Maybe I should give more details, first I edited [/SIZE][SIZE=2]/etc/pulse/[/SIZE][B]daemon.conf , [SIZE=2]changed

[/SIZE][/B]```
 ; default-sample-channels = 2
```[B]
to
[/B]```
default-sample-channels = 6
```[SIZE=2]I then unmuted master, front, surround, center and LFE in volume control in the device:HDA Intel (Alsa mixer) and rebooted. What is really strange is that these steps worked perfectly when I was on 8.10 but now after doing a clean install of 9.04 they don't seem to have any effect. In sound preferences I have all sound playbacks set to Autodect, and even if I change this I still get a 2 channel sound, except in one case:HDA Intel STAC92xx Analog (ALSA)  which yields me an error messge :[/SIZE] 
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```[SIZE=2]Maybe that is my problem? I also have Default Mixer Tracks [/SIZE]
[SIZE=2]set to HDA Intel (Alsa mixer).

Can anyone help?
[/SIZE]

---

### Post by JosephMarc on 2009-05-03
[SIZE=2]No one has an insight? At least tell me that my case is desperate so I can stop posting to myself. Please?[/SIZE]

---

### Post by fooman on 2009-05-03
try left-click on the speaker/volume icon in the top panel.  then click the "volume control" button.  when the alsa-mixer opens up,  click on the "preferences" button.  scroll through the "volume control preferences" box that pops up and put a check next to "surround jack mode" and "channel mode".  close that box.

back in alsamixer,  click the "options" tab and make sure the channel mode is set to "6ch"

does that work?  ...if not,  under the same options tab,   try switching between "shared" and "independent"...see if that makes any difference.

hope that helps.

---

### Post by JosephMarc on 2009-05-03
[SIZE=1]Thank you for your reply, but I am sorry I didn't find any of the "surround jack mode" or "channel mode", all I get is Master, PCM, Front, Surround...
And where is "alsamixer" with the "option" tab you referred to? I wasn't able to find it. I apologize again for my ignorance, I used to be a long time Windows user before I shifted to 8.04.
[/SIZE]

---

### Post by fooman on 2009-05-03
i will try to explain best i can...

click the speaker/volume icon in the top panel,  then click the button that says volume control.

that should open the alsamixer where you will see the sliders for master, pcm, front, etc...(make sure they are all unmuted and the sliders turned up all the way)

look in the bottom of that box and you should see a button that says "preferences"....click on that.

that should open up another box for "volume control preferences"....scroll down through the list and put a check next to "surround jack mode" and "channel mode".  then click the close button.

that should bring you back to the alsamixer....look along the top and click on the tab for "options".  

you should see an option for channel mode....choose 6ch and see if that helps.

---

### Post by fooman on 2009-05-03
> **JosephMarc said:**
> [SIZE=1]
And where is "alsamixer" with the "option" tab you referred to? I wasn't able to find it. 
[/SIZE]

when you click the volume icon in the panel,  then click the "volume control"...

that* is *the alsamixer that pops up.  :)

---

### Post by JosephMarc on 2009-05-03
[SIZE=2]I am confused, I opened exactly the box you mentioned, but I didn't find any trace of [/SIZE]"[SIZE=2]surround jack mode" and "channel mode", nor did I find the option box in alsamixer, on top I just have "HDA Intel..." . Maybe you are describing the how to on 8.10? I don't know maybe there's something that went wrong with my installation(although it was a clean install), is it possible that it led to a corrupted alsamixer?
[/SIZE]

---

### Post by uclaevo on 2009-05-03
sorry to thread-jack, but i have a similar problem:

after editing the daemon.conf (to add 6 channels), the vol control tracks (to add surround), and the surround jack (to shared), i now have surround by doing a speaker test.  however, when i try to play media either streaming from firefox or from an avi, i only get sound out of the front 2 speakers.  what can i do to get everything surround?

---

### Post by fooman on 2009-05-03
> **uclaevo said:**
> sorry to thread-jack, but i have a similar problem:

after editing the daemon.conf (to add 6 channels), the vol control tracks (to add surround), and the surround jack (to shared), i now have surround by doing a speaker test.  however, when i try to play media either streaming from firefox or from an avi, i only get sound out of the front 2 speakers.  what can i do to get everything surround?

what player are you using to play the avi?  check in the settings/preferences of the player.  there should be something there for audio output...stereo, 4.0, 5.1, etc.

---

### Post by JosephMarc on 2009-05-04
> the surround jack (to shared)

[SIZE=2]How do I do that?[/SIZE]

---

### Post by JosephMarc on 2009-05-05
[SIZE=2]It doesn't seem I'm getting the solution to my problem here so I'm moving this thread to a more appropriate subforum. Mods feel free to delete this if you wish.[/SIZE]

---

### Post by sagara on 2009-06-07
Hey Joseph, after my fresh jaunty install I followed the steps in this guide: [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/comment-page-1/#comment-826](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/comment-page-1/#comment-826)

It did the trick for me.

Do you hear sound from all your speakers when you run this command:

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

---

### Post by JosephMarc on 2009-06-07
[SIZE=2]Thank you people for your help, but I figured it out. First I used this command after editing the config files:  [/SIZE]
```
killall -9 pulseaudio
```

[SIZE=2]After this I went to my sound preferences and changed everything to ALSA.
Now what was really the problem is that I had no idea I had to enable "Line as Output" and "Mic as Output" in the switches subpanel in volume control. Now I have flawless surround sound.

I hope this helps some people out.[/SIZE]

---

