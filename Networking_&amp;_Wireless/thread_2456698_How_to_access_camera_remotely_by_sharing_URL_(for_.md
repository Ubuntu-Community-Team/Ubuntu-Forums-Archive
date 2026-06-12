---
title: "How to access camera remotely by sharing URL (for a Raspberry Pi Cam &amp; Octoprint)"
date: 2021-01-17
forum: Networking &amp; Wireless
---

### Post by freeflyjohn on 2021-01-17
Is there a secure and safe way I can access a camera URL remotely over the internet ?

I have a 3D printer hooked up to a Raspberry Pi running Octoprint, the Pi also has a camera attached.

The Raspberry Pi control panel can be accessed via a browser, using the URL [http://octopi.local/?#control](http://octopi.local/?#control)

The webcam can be be accessed independently using the URL [http://octopi.local/webcam/?action=stream](http://octopi.local/webcam/?action=stream)

I do not want to port forward the Raspberry Pi because it is dangerous to allow internet access to the 3D printer, especially as it allows control of the heaters on the 3D printer so if someone got access they could potentially burn the house down !

I have a server running Ubuntu 16.04 (on a Dell T30 Poweredge) which can access the Raspberry Pi as its on the same internal network.

As the camera has a different URL to the control panel, is there a way I can use my server to allow access to the webcam _only_ ?

I don't tend to leave the 3D printer unattended, but sometimes I might have to pop out whilst its printing and I would like to be able to monitor the print via the camera.

Ideally it would also be useful to control the printer remotely, but this would have to be 100% secure and safe.

Camera:

[https://thepihut.com/collections/raspberry-pi-camera/products/raspberry-pi-camera-module](https://thepihut.com/collections/raspberry-pi-camera/products/raspberry-pi-camera-module)

Rapsberry Pi 3+:
[https://thepihut.com/collections/raspberry-pi/products/raspberry-pi-3-model-b-plus](https://thepihut.com/collections/raspberry-pi/products/raspberry-pi-3-model-b-plus)

Octoprint:
[https://octoprint.org/](https://octoprint.org/)

---

### Post by TheFu on 2021-01-17
100% secure and safe. No.

99% secure perhaps using either ssh as a socks proxy or connecting through a self-hosted VPN.  From android, te VPN wold b easier.  From a Linux desktop, ssh with a socks proxy is 100x easier.
This needs all sorts of network configuration, like your LAN subnets aren't any of the popular subnets. No 192.168.0.x or 192.168.1.x or 10.0.0.x or 10.1.1.x.  Routing is important.

Also, your router needs monthly security patching and some basic capabilities.
Your "lan server" must have a static LAN IP.  It wold help if your internet was static too, but you can use a ddns service. I think some are free, with a few hassles.  The r-pi probably should too.  zeroconf doesn't work over wan connections.

Anyone with a r-pi can figure this stuff out.

Watch out for cloudy services claiming and providing access to stuff on a LAN. IP cameras often provide this, but don't really have stellar security histories. Beware.

---

### Post by freeflyjohn on 2021-01-17
Thanks TheFu

I already have SSH running on the server, I use this to SSH into the server using terminal and can explorer files using Filezilla etc (both can be done remotely)

I also use a PGP public and private key for SSH and have also changed the default port from 22.

I don't know what a socks proxy is though ?

I already have a static IP address, so thats not an issue.

My router is a Fritzbox 3490 (the ISP is Zen internet)

There are services which make Octoprint available remotely, but you have to pay a subscription:

[https://www.thespaghettidetective.com/](https://www.thespaghettidetective.com/)

[https://octoeverywhere.com/](https://octoeverywhere.com/)

---

### Post by TheFu on 2021-01-17
> **freeflyjohn said:**
>  
I don't know what a socks proxy is though ?

Search these forums for "socks localhost ssh"?
[https://ubuntuforums.org/showthread.php?t=2452922&highlight=socks+localhost+ssh](https://ubuntuforums.org/showthread.php?t=2452922&highlight=socks+localhost+ssh)

---

