---
title: "Connecting ubuntu to windows via Bluetooth for Audio output"
date: 2020-04-08
forum: Networking &amp; Wireless
---

### Post by piperakos96 on 2020-04-08
Ubuntu 18.04.3 I want to connect to windows 10 with Bluetooth for  sending audio to a windows 10 machine. I manage to connect but i can  only send audio from windows 10 to ubuntu and not the other way around.  When i go to the sound settings at ubuntu i cant choose Bluetooth at  output devices its only in the input devices any ideas?

---

### Post by slickymaster on 2020-04-08
Thread moved to **Networking & Wireless** for a better fit

---

### Post by CelticWarrior on 2020-04-08
The "other way around" depends on Windows supporting Bluetooth audio sink, I doubt it can but it may depend on drivers and additional software to support Bluetooth, again, in Windows.

---

### Post by piperakos96 on 2020-04-09
what you said made me wonder so i did the following experiment. I put two computers with windows 10 and connect them with Bluetooth when i went to the sound of windows 10 settings both computers put the other computer in both Input and output devices. Computer 1 for example is shown to the sound playback of windows 10 in computer 2 as headset earphone and also in recording as Microphone. And the opposite for computer 2 so according to what i enable and what not both computers can send audio to each other. So you think this is still a windows driver issue?

---

### Post by CelticWarrior on 2020-04-09
Yes, definitely a Windows drivers issue. Reason:

Headset+Mic = HFP (mono audio + mic) -> This is for duplex voice communications, not music. 
Ubuntu only uses HiFi audio for music (same as Android or iOS) and that requires A2DP which Windows don't or can't provide. Windows may eventually provide it via third-party Bluetooth drivers / software stack.

---

