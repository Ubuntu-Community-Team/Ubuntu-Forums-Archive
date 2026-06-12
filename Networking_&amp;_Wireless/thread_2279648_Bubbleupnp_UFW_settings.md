---
title: "Bubbleupnp UFW settings"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by Jon_Messenger on 2015-05-25
I have installed Plex and BubbleUpnp to allow streaming to a Chromecast device.

This works with no firewall switched on. The server is only used to stream video, allow printer sharing throughout the house and work BOINC Projects. I have tried setting up a Firewall with UFW and can allow everything to connect except the BubbleUpnp server. This is not detected by the Android device and will not transcode any video for chromecast. Any video that does not require transcoding will still play via chromecast correctly with UFW enabled.


I have followed all instructions I could find to allow a connection but still it only works with the firewall switched off.  Can anyone confirm whether this is normal behaviour for the software? Whether a firewall is ultimately required for my setup or have a similar setup that works with UFW and can share their UFW settings for BubbleUpnp server.

I am a Ubuntu / Linux newbie so please be patient if requesting further information.

---

### Post by SeijiSensei on 2015-05-25
Is this server is in your home or office and behind a router?  If so, there's no need for a firewall unless you don't trust the people you live with not to attack the server.

---

