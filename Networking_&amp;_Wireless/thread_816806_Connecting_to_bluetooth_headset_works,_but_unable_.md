---
title: "Connecting to bluetooth headset works, but unable to use it"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by cghost on 2008-06-03
I'm able to load the Bluetooth Headset Manager and connect to my headset. Even though the device pairs with the headset, and connects, the headset still won't work.

When I try to play a sound on the command line, I get this:

```
[AO_ALSA] alsa-lib: pcm_bluetooth.c:1422:(bluetooth_parse_config) Unknown field default
[AO_ALSA] Playback open error: Invalid argument
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

When I try to use skype, I get the message "Problem with audio playback". If I set the playback to my PC speakers and change the audio input to my bluetooth device, I get "Problem with audio capture." In the sound inputs, there are three bluetooth devices listed:

* BT Headset (hw:Headset,0)
* BT Headset (plughw:Headset,0)
* bluetooth

I've tried them all, all give the same error of "Problem with audio playback."

Here's my ~/.asoundrc:

```
pcm.bluetooth {
  type bluetooth
  default 00:11:B1:07:BA:C2
}
```


Currently I am using...

* Ubuntu Hardy 8.04
* ASUS WL-BTD201M Bluetooth USB Dongle
* Samsung WEP-150 Bluetooth headset

I have both Ubuntu and Kubuntu installed, but the scenario is exactly the same under either desktop.

Any help is very much appreciated!

Thanks in advance.

---

### Post by gdebat on 2008-06-16
my first post here so bear with me :)


i am having exactly the same problem, with the same configuration described above. any help?

---

### Post by johnwilmes on 2008-07-10
try replacing "default" with "device"

```

pcm.bluetooth {
  type bluetooth
  device 00:11:B1:07:BA:C2
}

```

---

### Post by eargyropoulos on 2008-07-30
Hello
my asoundrc file is ok, I am able to connect to my bluetooth headset , an ericsson HBH-200 (a2dp), i can listen to music, but arecord does not capture anything from my BT microphone???
Do you have any idea?

---

