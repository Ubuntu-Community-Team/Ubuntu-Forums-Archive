---
title: "Planning to create LAN with NAS for PLEX at home"
date: 2024-03-03
forum: Networking &amp; Wireless
---

### Post by AlyssaVS on 2024-03-03
Hi,

I am currently using Ubuntu 20.04 LTS dual partitioned with Windows 10 on two PCs and ready to update/upgrade my Linux Distro as needed. I have a QNAP NAS TS-453 Be and would like to set up a LAN in my home, with my PLEX server hosted on the NAS. 

This will be my first time setting up a LAN. I am looking for advice on the best Linux Distro for both the NAS and PLEX if there is a better one for this kind of setup. I want to be able to access and make changes from either of my PCs from the Linux side, and share my PLEX with family members. I'm comfortable with the OS installations, and the NAS is ready to go. I will need beginner level steps for the LAN setup though. 

Any help would be greatly appreciated.

Thanks!

---

### Post by TheFu on 2024-03-04
> **AlyssaVS said:**
> Hi,

I am currently using Ubuntu 20.04 LTS dual partitioned with Windows 10 on two PCs and ready to update/upgrade my Linux Distro as needed. I have a QNAP NAS TS-453 Be and would like to set up a LAN in my home, with my PLEX server hosted on the NAS. 

This will be my first time setting up a LAN. I am looking for advice on the best Linux Distro for both the NAS and PLEX if there is a better one for this kind of setup. I want to be able to access and make changes from either of my PCs from the Linux side, and share my PLEX with family members. I'm comfortable with the OS installations, and the NAS is ready to go. I will need beginner level steps for the LAN setup though. 

Any help would be greatly appreciated.

Thanks!

NAS are platform agnostic, provided they support both NFS (all Unix clients) and CIFS (MS-Windows only).
For streaming video around your home, you should choose to use NFS whenever possible.
Any "server", which is anything that other systems want to access either locally or remotely, need to be wired, ethernet connected with the fastest ethernet you have. The standard today is 1 Gbps (also called "GigE"), but there are faster versions of wired ethernet like 2.5 Gbps and 10 Gbps. You'll need/want a switch that can support those faster connections, if you want them.  GigE is more than fast enough to support moving lots of data around.

Always avoid wifi, especially for streaming video, since wifi may appear fast, but the computers see all the bandwidth ups and downs over streams that are more than a few minutes.

"Servers" need to have static IPs, so you need to set that up for both the media server and the NAS.  It also helps if you have a DNS for you LAN, though that can be gotten around by having a /etc/hosts file that you modify slightly for each client system - that includes phones, tablets, not just Windows and Linux and MacOS systems.  Those need it too.  Without DNS, you'll have to memories IP addresses and I know that Android really doesn't like it when we try to access websites on our own LANs.  Having a local DNS lets local LAN devices lookup your local machines just like they'd lookup maps.google.com.

There are 50 different ways to setup these things and your skill level will determine what is possible.  Nobody can answer that for you.
When you have a well-managed LAN, there are a few things that are helpful, even if not mandated.
[LIST]
[*]- LAN DNS
[*]- LAN DHCP
[*]- LAN NTP
[*]
[/LIST]
Then you add on storage servers that are accessible as required, but not open to everyone.  Your NAS shouldn't be available to delete everything when guests show up, right?  You certainly don't want to allow that through plex either.

Are you sure you want to use Plex?  They track every button pressed, every video, every music played, every show watched AND they expect you to pay for them to steal your data.  How much is that privacy worth to you?  Only you can decide.  When I used plex a few years ago, it was nearly as bad as a streaming roku device for phoning home about everything on my network.  Plex is full of compromises. All software is.  After running Plex because it would transcode videos as needed for my different devices, I've since switched to Jellyfin, which doesn't track what we watch and doesn't phone home at all.  Jellyfin handles the types of audio files we have, which plex never supported, while still having the ability to transcode videos during playback for each device.  

So, the first thing you need to understand is how IPv4 works, how simple routing works, then add on how DNS, and DHCP work.  You can add on NTP later, but if you need to compare log files, it is really helpful if each computer has exactly the same time source. It is also important for network security for all systems to have their clocks close to each other, if not correct with the rest of the world.

OTOH, lots of people just plug everything in and start using it.  Then when things break, usually because a DHCP lease expired or ZeroConf failed, they have to reconfigure everything again because all the systems have moved around.  If you turn off your systems, this is much, much, more likely to happen.  Or if you use static IPs and have a local DNS, it won't happen ... er ... well, DNS might die, but by that point, you'll understand the issue and 30 seconds on 1 computer will correct it.   Pay me now or pay me multiple times later, that's the choice.

If you notice stuttering in video playback, it is likely because you are using wifi or CIFS/Samba and not NFS with wired ethernet.  In theory, CIFS should work fine for streaming video inside a LAN, but in practice, there's something different and it doesn't work as well.

For playback of videos, I've standardized on Raspberry Pi v4 devices running OSMC.  Depending on your TV/Projector and audio setup, you may need to use some other devices to have HDR (Dobly Atmos) and high-end audio codec support.  The HDMI standards team has been pretty nasty to Linux and refused to allow AMD to distribute F/LOSS support for HDMI 2.1.  Also, they won't allow anyone not paying kickback money to have access to the HDMI specifications. That's extra nasty to F/LOSS.  I read today that nVidia is doing a firmware update to bring HDMI 2.1 +DRM support to Noveau drivers. I guess they already have it in their proprietary drivers, but IDK.  That's what my mind took away, here's the source articles:
[LIST]
[*][https://www.phoronix.com/news/NVIDIA-Firmware-Blobs-HDMI-2.1](https://www.phoronix.com/news/NVIDIA-Firmware-Blobs-HDMI-2.1)
[*][https://www.phoronix.com/news/HDMI-2.1-OSS-Rejected](https://www.phoronix.com/news/HDMI-2.1-OSS-Rejected)
[*]
[/LIST]

Because your question is very, very, wide, you'll need to break it down into 10 smaller questions to get help that is targeted.  There are guides for most of these things, but they aren't all in 1 place.  You can google as well as I.  The exact release of Ubuntu and whether it is a server or a desktop and which DE it has matters for some of the answers.

---

### Post by ian-weisser on 2024-03-04
If you have a router, then you already have a LAN.
Login to it and start looking at the settings.

The key setting is assigning consistent IP addresses to the media server (so you can find it) and to the NAS (so the media server can find it). Different routers have different names for doing that.
That's it. That's the whole required setup. Everything fancy after that is optional.

(I also ditched Plex years ago in favor of Jellyfin).

---

### Post by Morbius1 on 2024-03-05
Could you expand on this requirement:
> I am looking for advice on the best Linux Distro for both the NAS and PLEX if there is a better one for this kind of setup.
You want to replace the operating system on the NAS itself? Or are you planning to install PLEX on the NAS as it is? For example:: [URL="https://recoverit.wondershare.com/computer-tips/plex-for-qnap.html"]What Is Plex Media Server for QNAP and How to Use it?
[/URL]

---

### Post by TheFu on 2024-03-05
> **ian-weisser said:**
> If you have a router, then you already have a LAN.
Login to it and start looking at the settings.

The key setting is assigning consistent IP addresses to the media server (so you can find it) and to the NAS (so the media server can find it). Different routers have different names for doing that.
That's it. That's the whole required setup. Everything fancy after that is optional.

(I also ditched Plex years ago in favor of Jellyfin).

Exactly.  Most routers have something called "DHCP Reservations".  These are a way to reserve a static IP for specific devices and ensure those specific devices get the same IP, always.  15 yrs ago, doing that mapping was harder than it is today.  So, look up how to do that for your specific router.

Many current home routers provide all three of the services I listed.

I stand behind the "use wired ethernet" statement.  Servers just won't work well over wifi. Clients are usually fine (there are always exceptions).
Every OS works fine with static IPs or DHCP IPs.  Your NAS probably has a way to setup a static IP, but doing it via DHCP might be easier. Just make certain that you keep static IPs outside the range the router has for dynamic IP assignments.
I suggest you make random clients use a DHCP range above .200 .... so 192.168.1.200 - .254. 
And you place "reserved static IPs" as low as you like.  Use 192.168.1.2 - .20.  <---- see how those are in different ranges?  Never reuse the same IP, even on dual boot systems. Use a different IP for every OS install in the DHCP reservations.  BTW, it can be convenient to put all your non-portable devices under DHCP reservation control, so they always have the same IP on your LAN.  Of course, if your router dies or isn't working, your network is screwed.

As for NFS (or CIFS) and Synology, here's a thread about that on OSMC (same would apply to Plex) with images: [https://discourse.osmc.tv/t/no-access-to-nas-ever/96308/12](https://discourse.osmc.tv/t/no-access-to-nas-ever/96308/12)   of the Synology webgui and the OSMC (Kodi) webgui.  I use OSMC on my playback devices.

---

