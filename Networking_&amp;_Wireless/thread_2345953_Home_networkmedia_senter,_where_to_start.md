---
title: "Home network/media senter, where to start?"
date: 2016-12-09
forum: Networking &amp; Wireless
---

### Post by LK_gandalf_ on 2016-12-09
Hi all, I have the following devices and I' like to learn how to set up a good integrated home network:
- one router asus RT-AC1200G+
- 2 laptop, 1 with ubuntu and 1 with kubuntu, connected via wireless (no cable in the room)
- one TV (Philips) with android (connected with ethernet to the router)
- one wireless speaker with bluetooth and wifi (and an ethernet connection) [Sony X77]("http://www.sony.com/electronics/wireless-speakers/srs-x77")

Now, spotify works on all devices, but for instance I'd like to be able to stream a video or watch pictures from one of the computers and watch them directly on the TV, and use the external speakers instead of the TV's speakers.

I have no experience with networks and I don't know what options I have, so I'd like to learn more. I hope there is a simple way to best setup this :) Thanks!

---

### Post by TheFu on 2016-12-09
Use the router to setup DHCP reservations for all devices so they get the same IP every time.  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain. I assume that expensive router can do it.

Now that every machine has a known IP, setup name resolution for the network. That can be using /etc/hosts files or DNS or settings in the router. Just depends.

I'd use a DLNA server, **Plex Media Server**, as the center piece of the home network.  It needs to be wired connected to serve HiDef video content.  Wifi just isn't sufficient for the video server.  You don't need a plex account.  Any DLNA client can access the Plex Server. There are clients for android, Windows, Linux.

Steaming audio isn't hard. Very little bandwidth. Dont knwo anything about it. I use clementine with NFS connections or just use the Plex web interface or Kodi interface into my audio collection.  Finding streaming audio over the internet just too much trouble.

You need to clearly say what software the clients can run.  Do they run Plex clients?  Kodi players?  Roku? Chromecast?  What content do you want to access?  Anything local?  Recorded TV?  Ripped music from CDs or ripped DVDs/BRs?

Really need a wired connection for the media server. If the content needs to be converted from broadcast format to what a weenie device like a chromecast can play, then you'll need a more powerful computer to "transcode" the media on-the-fly. I'm using a G3258 for this. It was $50 for the CPU and another $50 for a motherboard. Very powerful, cheap, server with GigE networking. Over the years, it has gotten more and more storage - about 20TB now. Watching some old Sliders episodes on a Raspberry Pi v2 running Kodi now, streamed from the Plex server.  My house is all wired.  I don't regret that at all.

If you want to record TV, that is a highly localized question and depends on what TV service you have available.  I use OTA recording with multiple antennas in the attic using HDHR network devices for tuners.  TV is free. Recording it is free, but schedule data for the TV is not free here.  I understand most parts of the world have free schedule data.

So, list all the content you want to play, all the clients supported by the playback devices and perhaps someone can make better suggestions?

---

