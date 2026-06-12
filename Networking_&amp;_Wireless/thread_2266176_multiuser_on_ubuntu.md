---
title: "multiuser on ubuntu"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by archimedes1981 on 2015-02-20
Hi, I set up a media centre with Ubuntu 14 and wish to access a remote user through the same network so as to have full desktop and sound in remote station while the media centre stays logged on a different user. Is this possible? I've been looking at nomachine, zero and thin clients, Ubuntu server and lots of other articles but it got me nowhere. Can someone please put me on the right track.
vnc is not a solution for me for 2 reasons:
1- I want to leave whoever is using the media centre unaffected.
2- I need sound and good video streaming like youtube etc on both main and client systems.
Ideally I keep the ubuntu 14 (not server version) installed.
The client is an old laptop and cannot handle the power anymore soI need the media centre which is a 3GHz decent system to take the load.
Please help.
Thanks

---

### Post by TheFu on 2015-02-20
No need for a remote desktop. Just install a DLNA server, like Plex Media Server ... then the local user continues and the remote user can stream audio/video/photos as necessary just using any DLNA client to any DLNA renderer.  Of course, if transcoding is needed for both video streams (or for 10 more) then the server will need the power to do that.  If, on the other hand, the clients can all play the format provided directly, then a very low powered Plex server can easily handle it.  For audio, pretty much any netbook CPU from the last 5 yrs can handle anything needed.

So - lets get exact.
* Plex Server ... mine is on a AMD E350 APU
* Local client running on the same machine is Kodi + Plexbmc and controlled with a cheap remote control
* Any web browser can access the Plex Media website from inside the LAN and stream video/audio/photos
* Any DLNA client - like XBMC or BubbleUPnP on Android can see the Plex server. Just point the "library" to Plex and the "Renderer" to whatever device you like on the network - that can be any android device running BubbleUPnp (or any other DLNA renderer)
* DLNA renders include ... smartTVs, bluray players, Roku, Chromecast, some TiVos ... you get the idea.

There is ZERO security with DLNA on the LAN.  However, it is possible to withhold access through firewall rules on the server based on client IP addresses.  I block DHCP addresses on the LAN here from accessing the Plex server. Better for my sanity.

Oh ... and remote desktops aren't good for video, but for audio on the same LAN, I can suggest x2go. It works and is fairly easy to setup. It rides on ssh - so get ssh working as you like, then install the x2go-server on the plex server and install the x2go-client on any client machines you like. ssh-keys can be used for automatic authentication.  I've run clementine through x2go remotely, but honestly, DLNA is cooler.

Or did I completely miss what you were asking?

---

### Post by archimedes1981 on 2015-02-22
I need the client to have a full desktop environment. I think LTSP might do the trick but I want to be sure that it will not disrupt the network system and my current media centre settings.
Does the LTSP server need to also be the network server? I have a static IP internet router and I think having 2 DHCP servers will leave me with a mess.

---

### Post by TheFu on 2015-02-22
If you need HQ video, then that can only work over a wired GigE LAN. Spice with KVM VMs is the only way I know to achieve this.. I don't think the spice drivers work without a virtual machine.

I think you need a hybrid solution - as described above.  DLNA clients and servers for media and x2go for remote desktops.

Check out [http://ubuntuforums.org/showthread.php?t=1013767](http://ubuntuforums.org/showthread.php?t=1013767) video just doesn't work without local decoding and playback. Remove streaming of video is needed - not remote decoding and local visualizing.

---

