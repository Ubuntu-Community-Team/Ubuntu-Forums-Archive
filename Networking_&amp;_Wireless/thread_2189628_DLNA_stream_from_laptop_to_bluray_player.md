---
title: "DLNA stream from laptop to bluray player"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by Old Newville on 2013-11-23
Hello,

I've got a laptop and a bluray player, both made by Sony, and I've succeeded in setting up a stream from my laptop to the bluray player for any content stored on the disk, i.e., music, video or photos.

Where I've fallen short is in figuring out how to get internet music sources (Spotify, etc.) that I play on the laptop to hop over to the bluray player, by way of my home network. I found [this]("http://chemicaloliver.net/linux/streaming-audio-from-ubuntu-linux-to-a-dlna-player-blu-ray-or-ps3/") guide to setting up Rygel and tried it. I got as far as getting the stream sources to show up on the bluray player. But when I attempt to play them, I get a message that the files are corrupted or not supported. The file format shows up as lpmc, which is listed in the owners manual as a supported format.

The bluray player is a Sony BDP-S590, and the laptop is a Sony VGN-BX760 running Ubuntu 12.04.3 LTS. I've tried Rygel and the above linked suggestion using Pulse Audio.

My bluray player is connected to my stereo as well as the TV, so that's where I'd like to direct the bulk of the content. This player doesn't have onboard support for Spotify, just Pandora. Any thoughts or suggestions would be appreciated!

---

### Post by Old Newville on 2013-11-24
Add this update... I experimented with Serviio and found the same result:  The device shows up on the player but it won't play the stream.

---

### Post by alfonsociologo on 2014-07-24
Check out this tutorial, it might help:

[http://community.linuxmint.com/tutorial/view/1506](http://community.linuxmint.com/tutorial/view/1506)

---

### Post by grj23 on 2015-03-28
@alfonsociologo, that was a great link.  But I had the same problem.  I guess I don't have the right codecs in the GST Launch?  But I can go onto the computer server from the blu-ray and play it that way.  Just not the other way of directing the sound through the bluray from Rhythmbox.

When I go into GST Launch from the bluray player it gives only one option with says WAV, and if I go there it just plays a long beep.

---

