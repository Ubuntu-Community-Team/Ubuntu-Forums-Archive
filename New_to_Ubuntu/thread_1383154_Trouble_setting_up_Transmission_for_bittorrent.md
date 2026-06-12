---
title: "Trouble setting up Transmission for bittorrent"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by japhyr on 2010-01-16
Hello,

I am trying to use a torrent for the first time to download a few Linux iso files.  I am trying to set up Transmission.  I have been able to start the download, and I have downloaded 100+MB, but I am not sharing any of the files with anyone else (my ratio is 0 right now).

I have a wireless router (Linksys WRT160n), which is attached to a DSL modem.  Automatic port forwarding was not working, and I verified that upnp was allowed and dmz was disabled on the wireless router.

I tried to set port forwarding up manually, but it did not seem to work.  I found the ip address listed in network manager (under Connection Information).  In the router settings, I set single port forwarding to forward port 58392, protocol both, to the ip address I got from the connection information, and enabled it.  I tested the port at canyouseeme.org, which failed.  I noticed that the "Your IP" reported at canyouseeme.org is different than the ip I get from my network manager.

Can anyone tell me where I am going wrong?

---

### Post by mkvnmtr on 2010-01-16
All you have to do is double click on the torrent file. It will open in Transmission and start downloading. Probably no one else is trying to download the same ISO.Quite often the only time I can upload a Linux ISO is when a new release is out. I think some folks are uploading on a very fast rate and some of us slower guys just get dropped. I have never had to set up port fowarding on a linux system to get my max speed on both download and upload.

---

### Post by sandyd on 2010-01-16
> **japhyr said:**
> Hello,

I am trying to use a torrent for the first time to download a few Linux iso files.  I am trying to set up Transmission.  I have been able to start the download, and I have downloaded 100+MB, but I am not sharing any of the files with anyone else (my ratio is 0 right now).

I have a wireless router (Linksys WRT160n), which is attached to a DSL modem.  Automatic port forwarding was not working, and I verified that upnp was allowed and dmz was disabled on the wireless router.

I tried to set port forwarding up manually, but it did not seem to work.  I found the ip address listed in network manager (under Connection Information).  In the router settings, I set single port forwarding to forward port 58392, protocol both, to the ip address I got from the connection information, and enabled it.  I tested the port at canyouseeme.org, which failed.  I noticed that the "Your IP" reported at canyouseeme.org is different than the ip I get from my network manager.

Can anyone tell me where I am going wrong?
the network manager only reports your local IP address. which, is commonly 192.168.0.xxx

---

### Post by MarkC502 on 2010-01-16
You can download with Transmission without port fowarding setup but speed may suffer. 

To properly setup a port foward you need to go into your router and set a port foward rule. To do this you need to specify a Port # to foward , Type of traffic ( TCP, UDP or both ) and the machine IP address you want to foward to on your network ( I.E. the IP of the PC you are running Transmission on).

For Example PORT 20000 | Type BOTH | 192.168.0.3

this would open up the PC with Ip address 192.168.0.3 to receive both TCP & UDP packets from the Internet on port 20000. So if I then set Transmissions port to 20000 on this PC I would be in business.


So you need to know what IP your PC is using, here is the command to run in a terminal to find out easily.

ifconfig

Look in the output for inet addr: and it will show what your local IP address is for the PC you run it on. That is the IP you will need to foward the port to in your router.

And the other things are easy like just pick a random port between 10000 and 60000 and use it as your port number, and you can select both for type of packet in your routers port foward rules.

Lastly remember that this is only good as long as the PC keeps the same local IP address , this can change just because you reboot PC's in your house etc but may stay the same foreever as it is totally dependant on all the hardware in use and not very predictable without knowledge of all the hardware in play.

EDIT - I re-read over your question and saw DSL modem and router in play, you may find that to get your DSL modem to work with the router and port fowarding you will need to bridge your router to your DSL modem ( sounds much harder than it is ). When bridged your DSL modem no longer performs any routing functions and behaves as only a modem letting your router do all the routing so to speak. I used to install CCTV video servers and I would have to bridge customers DSL modems when port fowarding failed to work for remote viewing/control purposes. You can probably find a good guide on the Net for your exact ISP and modem etc as bridging a modem to your router is pretty common thing to want to do even for home setups.

---

### Post by lovinglinux on 2010-01-17
[BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by japhyr on 2010-01-17
Thanks for all the help, and the link.  I think it was a matter of no one else trying to download for a while.  I left it on overnight and saw in the morning that my download had finished, but I was uploading to 1 connected peer.

I am likely to use torrents to download linux iso's a few times a year, but no videos or anything else on a regular basis.  Should I disable the port forwarding when I am not actively using a torrent?

---

### Post by lovinglinux on 2010-01-17
> **japhyr said:**
> Thanks for all the help, and the link.  I think it was a matter of no one else trying to download for a while.  I left it on overnight and saw in the morning that my download had finished, but I was uploading to 1 connected peer.

I am likely to use torrents to download linux iso's a few times a year, but no videos or anything else on a regular basis.  Should I disable the port forwarding when I am not actively using a torrent?

When you are not using Transmission the port is closed, even if you forward it from the router. Nevertheless, it won't hurt to close it on the router too.

---

### Post by japhyr on 2010-01-17
Thanks everyone.  I am teaching students at my high school about Ubuntu and linux in general, and this will make it much easier to help students explore different versions of Ubuntu and other flavors of Linux as well.

---

