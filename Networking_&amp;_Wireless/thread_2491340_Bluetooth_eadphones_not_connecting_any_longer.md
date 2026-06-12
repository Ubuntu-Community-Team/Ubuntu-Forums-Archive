---
title: "Bluetooth eadphones not connecting any longer"
date: 2023-10-04
forum: Networking &amp; Wireless
---

### Post by spiv13 on 2023-10-04
Hello,
I have a Lenovo Ideapad Flex5 running Kubuntu 22.04 fully upgraded.
A few days ago I could not get any sound out of Brave, while I could out of Firefox, VLC etc.
I searched Ubuntu forums and got Brave to work by following this:
  	 	 	 	   To have a look at everything using your audio control, type:

 [COLOR=#000000][SIZE=2]pacmd list-sink-inputs[/SIZE][/COLOR] pay attention to the values "muted:", "index:" and "volume:".
  You might have had volume in the application and it could still be muted or on zero volume!
  To fix a muted application, type (replace application_index with the index number you found in "index:"):
 [COLOR=#000000][SIZE=2]pacmd set-sink-input-mute application_index [/SIZE][/COLOR][COLOR=#ff0000][SIZE=2]false[/SIZE][/COLOR]  Then I had some other audio problems and following other Ubuntu forum suggestions I ended up installing Pipewire from this link:[INDENT][https://pipewire-debian.github.io/pipewire-debian/](https://pipewire-debian.github.io/pipewire-debian/)
[/INDENT]

Today I cannot connect any of my Bluetooth headphones, they are visible, discoverable, but as soon as I try to connect I get an error:[INDENT]"Connection to this device failed"[/INDENT]

Forgetting the device and re-pairing returns the same error.

I followed the instruction on the sticky for this forum and installed 'pastebinit', 
then run the wireless info script and saved it in pastebinit 
This (I hope) is the link to it:
[https://pastebin.com/SLsVFgYJ](https://pastebin.com/SLsVFgYJ)

Thank you for helping me

---

### Post by spiv13 on 2023-10-20
Unfortunately, I still cannot connect any of my paired Bluetooth audio device to my laptop, they all "fail to connect".
Since nobody on this forum can help me, can you recommend another place where I can get help?

---

