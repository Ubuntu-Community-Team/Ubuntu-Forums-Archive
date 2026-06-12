---
title: "Another Attempt at Audacity"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by daniell59 on 2010-01-24
I have yet been able to use Audacity. I am trying to record streaming audio, but I have had no success with Audacity. I can hear it coming out of the speakers, but it will not record. If this is significant, I had no luck using Vista either.
I would like to make a fresh attempt.
I am using Ubuntu 9.10.

Thanks in advance

---

### Post by howefield on 2010-01-24
I got mine recording by following this post by "Stream Recorder"

[http://stream-recorder.com/forum/audacity-wont-record-streaming-audio-no-stereo-t5393.html?](http://stream-recorder.com/forum/audacity-wont-record-streaming-audio-no-stereo-t5393.html?)

> Install PulseAudio Volume Control by running the following in the Terminal:
sudo apt-get install pavucontrol
Run Audacity and Go to Preferences by pressing Ctrl+P (or select "Edit" -> "Preferences..." from the drop-down menu).
Click the "Devices" .
Change the Playback device to "pulse".
Change the Recording device to "pulse".
Open PulseAudio Volume Control ("Applications" -> "Sound & Video" -> "PulseAudio Volume Control") and leave it open. 
The first time you use a recording program you need to to edit the recording settings of PulseAudio Volume Control. It should remember your settings after rebooting.
Open Audacity and hit the "Record" button.
While Audacity is recording, open PulseAudio Volume Control and select the "Recording" tab. It will show "Alsa plug-in Audacity. Alsa capture from" and a combo-box. Choose the "Monitor of internal audio..." if you use an internal sound card.
Check Audacity, it should be recording now.

---

### Post by ankspo71 on 2010-01-24
Hi,

I don't know if everyone's sound card preferences are the same way, but I had to make a change in order for Audacity to pick up any sound. I believe this will help Sound Recorder too.

To see if this will help, go to System > Preferences > Sound and open it.
After it opens, click on the 'hardware' tab.
Towards the bottom you will see "Settings for Selected Device"
One by one, check your options to see if any will allow you to record any audio in Audacity.

Mine was originally set at Analog Stereo Duplex, and had to change it to Analog Stereo Output. 

I'm attaching a screenshot... (Ubuntu 9.10 and greater)
Hope this helps everyone who can't record.

---

### Post by Mariane on 2010-01-24
It could be better to use alsa rather than pulse audio for recording stream with audacity:

[http://forum.audacityteam.org/viewtopic.php?f=14&t=3541](http://forum.audacityteam.org/viewtopic.php?f=14&t=3541)

Mariane

---

### Post by daniell59 on 2010-01-24
> **ankspo71 said:**
> Hi,

I don't know if everyone's sound card preferences are the same way, but I had to make a change in order for Audacity to pick up any sound. I believe this will help Sound Recorder too.

To see if this will help, go to System > Preferences > Sound and open it.
After it opens, click on the 'hardware' tab.
Towards the bottom you will see "Settings for Selected Device"
One by one, check your options to see if any will allow you to record any audio in Audacity.

Mine was originally set at Analog Stereo Duplex, and had to change it to Analog Stereo Output. 

I'm attaching a screenshot... (Ubuntu 9.10 and greater)
Hope this helps everyone who can't record.

I tried that some time ago. It did not help.

Thanks

---

