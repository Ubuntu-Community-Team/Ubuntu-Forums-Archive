---
title: "Ubuntu as a Router--Setting up a UPnP Media Share"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by lighty14 on 2007-12-11
I've been working to set up ushare ([http://ushare.geexbox.org/](http://ushare.geexbox.org/)) on my Ubuntu machine in order to share media between it and my Xbox 360. I'm having difficulties connecting to my ushare from the Xbox, but I believe it is a routing issue, not an issue with ushare. Original thread of mine and many others working to get ushare up and running: [http://ubuntuforums.org/showthread.php?t=631213](http://ubuntuforums.org/showthread.php?t=631213)

My computer also acts as my network router, hosting DHCP for the Xbox. Internet connection sharing works flawlessly.

On the ushare website, the following is mentioned:
> 
At first you need to be sure that you have setup a multicast route for UPnP messages. If you don't but have a default route attributed, then this later will be used. Otherwise, simply declare a new route for UPnP multicasts (for example using eth0 interface) :

```
route add -net 239.0.0.0 netmask 255.0.0.0 eth0
```


I have followed this suggestion, as eth0 is the device corresponding to my local network. The command completes successfully, but I still have connection issues. I fired up Wireshark, which I am no expert with, to see if I could decipher anything. There are bad packets that are going to 239.255.255.250 when I'm trying to connect to ushare, originating from my Xbox.

How do I get these packets to properly route to my computer so ushare can host the files?

---

