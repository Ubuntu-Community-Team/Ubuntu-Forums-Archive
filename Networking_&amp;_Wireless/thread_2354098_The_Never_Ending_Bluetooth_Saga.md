---
title: "The Never Ending Bluetooth Saga"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by nickTaylor1181 on 2017-02-28
High All.


I don't suppose anyone knows why Bluetooth is such a nightmare to get working?

This is the 4th laptop in a row that doesn't work properly, with various bluetooth devices, mainly a UE Boom and a technics (I think) headphones.

I'm using Ubuntu Studio 16.04 ... it shows the same symptoms with Ubuntu 12.04 and Mint.


It is a real hassle to connect... need to repeatedly turn devices on and off again... use Blueman to try to connect it as an Audiosink (it never wants to do this... usually I have to switch to phone-quality audio, restart the bluetooth connection again, then connect as Audio-sink).

It also seems to clash with Wifi... wifi will lock up... then as soon as I disconnect bluetooth, wifi starts working again.

With various previous laptops, there have been serious stuttering and lagging problems.

Ubuntu before about 12.04 worked fine. Various incarnations of windows work fine with all the bluetooth devices.

I've been asking about this for years now. I can't believe it only happens to me.


Does anyone have any idea what to do about this? 



Thanks in advance,



Nick

---

### Post by teknodude2 on 2017-03-11
same here buddy.  After reading online forums and trying various things, bluetooth just does not work smoothly. For audio, I constantly get weak signal strength and audiosink issues. I've given up bluetooth on ubuntu 16.04 for the dell xps 13.

---

### Post by nickTaylor1181 on 2017-03-11
Yea - I've had this for years, across multiple devices. I can't believe that it isn't a major issue.



Right now, to connect bluetooth headphones I have to:




1) switch headphones off then on again


(then on a laptop)


2) set the device to Audio-sink 


This will connect it... no sound will come out, and wifi will lock up completely.


3) set the device to low-fi sound


Audio will come through, wifi will start again.


4) disconnect the device


5) reconnect the device


6) switch the sound to audio-sink.




After that it will work properly. If the laptop goes out of range of the headphones (like it does every day), the above needs to be repeated.


So it works - but really, that does kindof suck.  I've got one of those UE Boom things - for the first laptop it was great... now (4 laptops later), it's in a box in a cupboard somewhere, because bluetooth doesn't work properly, and I've yet to find anyone who can help.

---

### Post by jeremy31 on 2017-03-11
I can't say I have no bluetooth issues but not anything close to the issues the other posters in this thread have.  I have a Sony MDR-ZX770BT headset and I can use wifi to watch youtube videos while using the bluetooth headset.

After disconnecting from the headset I use a2dp.py from a [bluetooth bug report](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) to reconnect the headset and have it switch to A2DP without messing with Blueman.  I think some issues could be caused by wifi access points messing with the bluetooth/wifi as the only wifi access point I have around is my own, my closest neighbor is 400 meters away.

Seems there are a few people with the UE Boom(2) and they struggle with them

---

### Post by ktat on 2017-06-27
I have 17.04 and also have difficulty connecting to a Bose bluetooth speaker.  It will pair, but always fails when I try to connect to audio sink.  Very frustrating that bluetooth is so unreliable.

I am willing to do research to solve problems that come up time to time - but never have I been able to find a simple answer to this one.

---

### Post by jeremy31 on 2017-06-27
You can check
```
pactl list short | grep blue
```
To see if module-bluetooth-discover is loaded, if it isn't
```
pactl load-module module-bluetooth-discover
```

Then connect with the device.  I have been using Blueman and usually have to connect to the device, switch audio profile to off, disconnect, reconnect and switch audio to A2DP and then the headset will show in Sound Settings and can be used

---

### Post by nickTaylor1181 on 2017-06-27
The module (module-bluetooth-discover) appears to be loaded -  but I'm basically using the workaround you describe. A fair bit of fannying about, for something that used to work perfectly straight out of the box.

---

### Post by ktat on 2017-06-30
I don't know exactly what has just happened, but my Bose SoundLink connected successfully this time.

Simply turned the speaker on and waited for it to say "ready to pair", then added it to my devices (without trying to connect to audio sink).  I then opened up Sound Settings and the speaker was already listed amongst the devices to play sound through.  I selected it, tested it and voila it worked :)

---

