---
title: "Can't turn on &quot;Media Sharing&quot;"
date: 2022-10-22
forum: Networking &amp; Wireless
---

### Post by asubscriber on 2022-10-22
Given:
Ubuntu 22.04

I try to sharing Media. But I can't press switch button. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291158&stc=1[/IMG]

---

### Post by TheFu on 2022-10-22
Google found this: [https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html](https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html)
Did that not work?
BTW, Rygel is a DLNA **server**, so you'll need a DLNA **renderer** and **controller** to make use of it. Those 3 things can be on 3 different devices or all on a single device or any mix of devices.  

I've used Rygel on prior systems, but found it didn't fit my needs and tried minidlna, plex server and jellyfin.  I'm using JellyFin today as it fits my needs and privacy more than the others.

So, my DLNA server is Jellyfin.  The controller is an android tablet and the renderer is a raspberry pi running OSMC connected to a projector and audio receiver.  The OSMC also uses an MCE remote control, so it can be the DLNA controller and renderer.

Sometimes, I'll use a webbrowser to connect to Jellyfin to listen to music or watch a TV episode while I'm traveling.  In this case, Jellyfin is the DLNA server, renderer and controller sending the video and audio over http to my client over a VPN connection (or ssh tunnel).

For music, I prefer mpd and use mpd-clients (ncmpc) to control playback of the different mpd serves in my network.  MPD plays audio files on the system where the mpd server is running, not on the client.  The client is a remote controller to handle playback and playlists.  Most of the time, I use MALP on Android (phone and tablet) to control mpd in my home office, bedroom or den.  Most other mpd clients only expect 1 mpd server, so MALP supporting many is good for my needs.

DLNA is an entertainment industry standard and has been around 15 yrs.  Many TVs work with DLNA, but I don't think Rygen will transcode at all.  Jellyfin can transcode to the required video and audio formats needed by different client devices.  If your clients are computers, say using vlc, then no transcoding of audio or video should be required, but if the client is a 5 yr old Chromecast, Firestick, or Roku, then the video must be h.264 and the audio probably needs to be either mp3 or aac.  For example, my roku will not play mpeg2 video with DTS audio which is what the TV stations here broadcast.  I have to transcode to h.264/aac in either an mp4 or mkv container to play on the Roku.  Of course, other devices support mpeg2/DTS just fine.  There isn't really and mandated, 100% supported, video/audio codecs that just work on all devices, but h.264/aac/mp4 is about as well supported as I've ever seen.  
Of course, web browsers want vp8/vorbis streams, thanks to Google's dominance of that market and because those video/audio streams are patent free.  h.265 (also VP9 or AVC1) often require too much CPU in the decoding to work on older or lower-end devices.

Hope this is all clearer than mud.

---

