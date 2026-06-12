---
title: "Automated Audio Recording"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by zer010 on 2010-09-30
I had been wondering how to set up an automatic scheduled recording of my favorite radio talk show.  I was even more encouraged when I found it streaming live on the net. So I started looking for a way to do this when I came across this thread: [http://ubuntuforums.org/showthread.php?t=305858](http://ubuntuforums.org/showthread.php?t=305858) .  It is just what I had been looking for!  I set it up as per the instructions. 
   Today was my first test run of this task.  Everything seemed to be going great. Firefox opened up to the correct link and I could hear the audio, next a new file appeared on my desktop as I was expecting/hoping.  Well, the show ended and Firefox shutdown and the file on my desktop had been renamed as per the script. I was ecstatic! 
   So I went to check out the quality of the audio and was disappointed to find that no audio was playing as far as I could tell. I checked the files properties to find that it was a hefty 477.9 MB. About right for what I set up. So then I opened it in Audacity to check the waveform and it looked like the image provided!  What could've gone wrong? Maybe the instructions I found are too outdated? Any help is GREATLY appreciated!

---

### Post by zer010 on 2010-09-30
This is my settings for this task;

crontab is setup as so:
# m h  dom mon dow   command
#Record the radio show everyday
#Open firefox and load the audio stream
03 11 * * 1,2,3,4,5 export DISPLAY=:0 && firefox [http://player.streamtheworld.com/_players/citadel/?sid=826&nid=2920](http://player.streamtheworld.com/_players/citadel/?sid=826&nid=2920)
#Record every day from 11:06am for 2 hours and 54 minutes
05 11 * * 1,2,3,4,5 arecord -d10440 -r24000 -c2 /home/zer0/Desktop/radio-show.wav
#Rename the audio file by placing a time stamp on it
01 14 * * 1,2,3,4,5 /home/zer0/rename-radio-file
#close all instances of firefox
01 14 * * 1,2,3,4,5 killall -q firefox-bin

The bash script is:
#!/bin/bash
#Program to rename a file with a date stamp.

mv /home/zer0/Desktop/radio-show.wav /home/zer0/Desktop/rshlmbgh-$(date +%Y%m%d).wav

---

### Post by zer010 on 2010-09-30
Once I can get the audio issues worked out, I would like to have it automatically convert the .wav file to a .mp3. 
 Also, I'd like the shutdown of Firefox to be more specific instead of killing ALL instances of FF.
Again, any assistance is greatly appreciated!

---

### Post by zer010 on 2010-10-01
I just tried to amplify the track to see if that would help, but all I get is faint crackling sounds. I guess arecord is not accessing the sound being run to my speakers?  Any suggestions? Is there another tool besides arecord that can do this from the command line?

---

### Post by robert shearer on 2010-10-01
I looked at your link and it all seems excessively convoluted.

Why not just set Audacity up to do it ??

Using Audacity go to 'Transport' then select 'Timer Record'

---

### Post by zer010 on 2010-10-01
"...excessively convoluted." :lolflag:
Ok, I guess I'll try that. I wasn't sure if Audacity could be setup to record streaming audio.
I'd still like to get the cli way working though.  Thanks for the tip! *thumbs up*

(Not sure how to insert my own emoticon from my collection)

---

### Post by zer010 on 2010-10-01
Ok, just as I thought I remembered. Audacity's timer recording options are extremely limited.  Start date/time, end date/time.  
This must be why the link came to it's conclusion.  Apparently, Audacity is not sufficient to do this job. As I stated, everything worked except  that the audio doesn't appear to have been recorded. 
What options do I have for audio troubleshooting?  arecord is an ALSA tool. Maybe i don't have ALSA? I'm grasping at straws now.

---

### Post by zer010 on 2010-10-08
I just can't seem to figure this thing out. Maybe the site itself is not allowing the audio to be recorded? It's just pretty frustrating that everything seems to work like a charm, until playback. :cry:

---

