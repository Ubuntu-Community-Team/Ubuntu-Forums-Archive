---
title: "Stream audio from phone to computer speaker through bluetooth dongle -bluez-?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by jcol88 on 2009-05-02
Hello all,
     I dont know if this is possible, but I havent found anything posted about it. I have connected my LG Dare to my computer through a bluetooth dongle. I am attempting to stream music from the phone through my computer's speakers. In order to do that I think I have to make my computer look like a bluetooth headset to my phone. I dont know if you can actually do this :confused: but I would appreciate any help!!! 

Thank you!

---

### Post by 987poiuytrewq on 2009-05-02
I have done this with my computer before, so it is possible. Your bluetooth dongle needs to support Audio Sink or something similar sounding and your phone has to support A2DP. The way I did it was that in the music player, there was an option to play through bluetooth headphones, and picking the computer as the headphones made the sound come out of the computer speakers. It is probably different for every phone though.

---

### Post by jcol88 on 2009-05-02
The Dare supports A2DP, and I have a D-Link bluetooth adapter DBT-120, which I am pretty sure supports the audio sink according to some blogs I have looked at. I still cant find anything on making the phone send the audio stream through the dongle. When I play music on my phone it just comes out of my phone's speakers :( .   I have found a few blogs on how to make the computer stream audio to a bluetooth headset, I tried to do this with my phone, but I think my phone has some protocols that are blocking the stream. 

PC to headset: [http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers)

if anybody knows of a way to convert these instructions so it would go through a phone then that would be good enough for me.

Thanks again

---

### Post by HoodRobin on 2010-04-16
My phone (Motorola i856) has the option to play via bluetooth but won't recognize the computer as audio device, but I can send and receive files. I'm using Ubuntu 9.10. Any ideas how to get Ubuntu to be recognized as audio device?? Btw, this worked fine on Windows Vista, so it does work on some OS's

---

### Post by jackflap on 2010-06-17
Check this out: [http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/)

I haven't tested it yet, but it looks like what we're looking for. Please report back with results.

---

### Post by megamanexent on 2010-08-09
jackflap's link is what you are looking for, use this thread for help.
[http://ubuntuforums.org/showthread.php?t=1464189](http://ubuntuforums.org/showthread.php?t=1464189)

---

