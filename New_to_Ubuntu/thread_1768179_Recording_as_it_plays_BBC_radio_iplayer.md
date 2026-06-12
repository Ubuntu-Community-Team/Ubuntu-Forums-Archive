---
title: "Recording as it plays BBC radio iplayer"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by cpcpcp on 2011-05-26
I want to record what I hear on the BBC Iplayer. In the past I could record a radio program onto a cassette as it was broadcast (or played back) . Now I would like to record straight to  an .ogg or .mp3 file what I can hear playing on the iplayer through my Hifi. Is this possible?
I am too wimpy to try it but I have considered connecting the output from the USB output device to the line-in socket of my on-board sound card but but did not want to blow something up.!
But then  I thought if sound is coming out surely I could just **record the sound stream as it was produced?**

Has such a simple thing been documented anywhere or can you give me some clever understandable suggestions that I would never dream off?

---

### Post by SteveDee on 2011-05-26
> **cpcpcp said:**
> ...I am too wimpy to try it...

...or you could try "get_iplayer" here: [http://linuxcentre.net/getiplayer](http://linuxcentre.net/getiplayer)

---

### Post by ajgreeny on 2011-05-26
I use mplayer to record live broadcasts of BBC radio, rather like using a tape recorder in days gone by.

I also use get-iplayer to download after the event.  It's an excellent application, but is command line only at the moment; dead easy to use, however, so do not fear the command line.

For mplayer I use shell scripts, which means I can use cron to time recordings without a problem.  All you need is the ULRs of the asx streams of BBC output for various radio stations which you can find at [http://faq.external.bbc.co.uk/questions/radio/online_radiohowto](http://faq.external.bbc.co.uk/questions/radio/online_radiohowto) and then use the command ```
/usr/bin/mplayer -cache 2048 -playlist <ulr> -vc null -vo null -ao pcm:fast:waveheader:file=/home/path/Radio/$(date +%F_%H-%M)-BBCR3.wav & sleep 152m; killall mplayer
``` which you can put into a shell script for cron, if you want, (hence the full pathway of mplayer, needed for cron to work).

You will also see I have a variable for the filename produced, which adds date and time to the name, and a sleep command run at the same time to kill mplayer after a time in minutes (sleep 152m being two and a half hours, plus two minutes for safety.

---

### Post by wildmanne39 on 2011-05-26
> **ajgreeny said:**
> I use mplayer to record live broadcasts of BBC radio, rather like using a tape recorder in days gone by.

I also use get-iplayer to download after the event.  It's an excellent application, but is command line only at the moment; dead easy to use, however, so do not fear the command line.

For mplayer I use shell scripts, which means I can use cron to time recordings without a problem.  All you need is the ULRs of the asx streams of BBC output for various radio stations which you can find at [http://faq.external.bbc.co.uk/questions/radio/online_radiohowto](http://faq.external.bbc.co.uk/questions/radio/online_radiohowto) and then use the command ```
/usr/bin/mplayer -cache 2048 -playlist <ulr> -vc null -vo null -ao pcm:fast:waveheader:file=/home/path/Radio/$(date +%F_%H-%M)-BBCR3.wav & sleep 152m; killall mplayer
``` which you can put into a shell script for cron, if you want, (hence the full pathway of mplayer, needed for cron to work).

You will also see I have a variable for the filename produced, which adds date and time to the name, and a sleep command run at the same time to kill mplayer after a time in minutes (sleep 152m being two and a half hours, plus two minutes for safety.
Hi, does mplayer only record the broadcast or does it also pick up the sound in the room?

---

### Post by SteveDee on 2011-05-27
> **ajgreeny said:**
> ...It's an excellent application, but is command line only at the moment....

There seem to be a few simple GUIs available, but I've yet to try any.

Example here: [http://linux.softpedia.com/get/Multimedia/Audio/get-iplayer-GUI-47503.shtml](http://linux.softpedia.com/get/Multimedia/Audio/get-iplayer-GUI-47503.shtml)

---

### Post by tea for one on 2011-05-27
> **cpcpcp said:**
> I want to record what I hear on the BBC Iplayer. In the past I could record a radio program onto a cassette as it was broadcast (or played back) . Now I would like to record straight to  an .ogg or .mp3 file what I can hear playing on the iplayer through my Hifi. Is this possible?
I am too wimpy to try it but I have considered connecting the output from the USB output device to the line-in socket of my on-board sound card but but did not want to blow something up.!
But then  I thought if sound is coming out surely I could just **record the sound stream as it was produced?**

Has such a simple thing been documented anywhere or can you give me some clever understandable suggestions that I would never dream off?

I hope that I have understood this correctly because I assume that you are listening to DAB radio on you HiFi and you want to record the sound to your PC?

Connect your Line out of you HiFi (or Dab radio) to Line In on your PC.

Doulbe check the input device in Sound preferences.

I use Audacity to record and edit the sound and then convert to mp3 format.

If you are going to do this regularly, I would suggest that you consider the purchase of a DAB radio with "timed" recording capabilities direct to your PC or to an SD card.

Here is a link to the radio that I use to record digital sound:-

[http://www.pure.com/products/product.asp?Product=VL-60954&Category=](http://www.pure.com/products/product.asp?Product=VL-60954&Category=)

There is also another solution. If you have ever recorded digital TV to your PC (e.g. using Kaffeine), you can also record the digital radio services bundled in with digital TV services.

You will need a DVB tuner such as an AVerTV Volar Black HD A850

Good luck with your endeavours

---

### Post by nerdy_kid on 2011-05-27
install pavucontrol (pulseaudio volume control), start it up.  Open up the GNOME sound recorder, hit record.  Go to the recording tab of the pulseaudio volume utility, hit the drop down list under "Sound Recorder" and select "Monitor of Internal Audio"  (or something like that)  Play any audio, and it will be recorded by GNOME sound recorder.

---

### Post by jre6 on 2011-05-27
> **wildmanne39 said:**
> Hi, does mplayer only record the broadcast or does it also pick up the sound in the room?
How can it possibly record the sound in your room?

---

### Post by ajgreeny on 2011-05-27
> **jre6 said:**
> How can it possibly record the sound in your room?
And why do you want it to record that?

It simply records the stream that mplayer (the cli version, not the gui version) is streaming.  You will not hear anything until you listen to the wav file.  I usually convert that to an mp3 for my player using ffmpeg.

---

### Post by wildmanne39 on 2011-05-27
> **jre6 said:**
> How can it possibly record the sound in your room?

Hi I used audaucious and it recorded the sound in the room too.

---

### Post by ajgreeny on 2011-05-27
> **wildmanne39 said:**
> Hi I used audaucious and it recorded the sound in the room too.
Audacious?

Do you mean audacity?

mplayer cli application will not record the room sounds.

---

