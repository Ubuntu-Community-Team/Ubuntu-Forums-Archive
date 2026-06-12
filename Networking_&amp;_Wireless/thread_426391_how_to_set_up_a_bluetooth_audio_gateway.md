---
title: "how to set up a bluetooth audio gateway?"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by williamwade on 2007-04-28
i was woundering how to set up an audio gate way so i could play music from my phone (nokia 6233) on my pc (xubuntu) speakers?

---

### Post by ondrejhome on 2008-04-15
Hi, From Ubuntu 8.04 it is possible to connect to your phone using bluetooth manager and browse file in your phone so also playing music files is possible.

---

### Post by dseater on 2008-05-29
I think what he was asking is how to use the PC as a "headset" for listening to music using the phone's media player. I spent some time looking for this on Hardy 8.04 last night with no success.

The audio flow would look like this:
Phone Media Player -> PC Bluetooth Adapter-> PC speakers

The Bluetooth stack on my Windows PC has a service called "My Headset" that does exactly this. The description of it is:
[INDENT]**Headset**
This service (if enabled) is provided by this computer to remote Bluetooth devices. It allows a remote Bluetooth device to use this computer's speakers and microphone.
[/INDENT]

Based on the sound quality it is using A2DP when playing music.

Is there something similar in Hardy that I overlooked? Maybe a different Bluetooth manager than the default?

---

