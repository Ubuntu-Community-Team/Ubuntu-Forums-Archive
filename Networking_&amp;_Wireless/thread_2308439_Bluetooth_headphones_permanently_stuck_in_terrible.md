---
title: "Bluetooth headphones permanently stuck in terrible-sound mode"
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by nickTaylor1181 on 2016-01-03
Hi all.

I'm having serious problems getting bluetooth headphones to work. After about 4 hours of bluetooth not working at all, I've managed to get them to connect - but they're now stuck in low-quality sound mode. 

The A2DP profile is available, but changing to it using the dropdown in the sound-manager does nothing. I've also tried using the pulse-audio-manager to change the profile. Again it's available, but doesn't make any difference, and next time I go back to it, it's gone back to low-quality mode again.


Any ideas?

---

### Post by Elishasmantle on 2016-01-03
Hello,

These links may help:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

I had some major issues as well getting BT Headset working and had to use this link as well. Some of the commands for tools and what-not are handy:
[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

---

### Post by nickTaylor1181 on 2016-01-03
Hiya - thanks for that.

Are those links really old? They look to me like they're for versions of ubuntu from ages ago. 

There's this page : 

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Which has long, involved instructions, which fail when I get to 

"[COLOR=#333333][FONT=UbuntuMono]pactl load-module module-alsa-sink device=btheadset[/FONT][/COLOR]"

Saying "module initialization failed".


Which pretty much leaves me high and dry - I have no idea what that means, or what to do about it, or even what I've just done to my system... by now I'm just typing random stuff into a CLI.

---

### Post by nickTaylor1181 on 2016-01-03
I don't suppose anyone can point me in the direction of something a bit more diagnostic? 

To see what is actually going on etc - so I can hopefully see what is missing and remedy it.

---

