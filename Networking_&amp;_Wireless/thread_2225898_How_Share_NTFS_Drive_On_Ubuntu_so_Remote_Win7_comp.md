---
title: "How Share NTFS Drive On Ubuntu so Remote Win7 computer Can Access It?"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by mysubs on 2014-05-24
Been raised on Windows and now I have a Win7/Ubuntu 14.04 dualboot.
The rest of the computers on my home network are running Windows.
My dualboot (which is also my media computer) has all my media stored on an NTFS formatted drive (from when the computer was Win7-only).  I know how to access the drive remotely from my other computers when I'm booted into Windows 7.  

How do I share the NTFS drive with the other computers, when I'm booted into Ubuntu?

---

### Post by TheFu on 2014-05-24
I'm only able to guess - don't use desktops much ...

Open Nautilus, right click on the folder, select sharing ...  There is probably a "share permanently" option. Don't know if this works well/at all/ with NTFS. Sorry.

However, you can also use samba if more control over the permissions is desired
or
load a full DLNA server like Plex if you want to have an AWESOME media center server ... that will work with almost any DLNA client like Android, smart-TVs, bluRay players, most media player devices, XBMC, and chromecast.  I've been using Plex about 8 months, but doing the media center stuff for years.  I honestly wish I'd switched to plex sooner.  Plex has a server (no GUI), then different clients will connect to view the media. The main server-config interface is through the web.

So, you have a few options.

---

### Post by mysubs on 2014-06-04
I've had a degree of luck now that I've installed Samba and the associated GUI.  Now Windows will see my Ubuntu computer name, but it won't see any of the shares.
Could there be a possible complication because my Ubuntu box is a dualboot with Windows 7 (not the same W7 I've been trying to network with Ubuntu)?  Both Ubuntu and W7 share the same IP address, presumably because my AT&T router is basing the DHCP lease on the MAC address.  I don't know if that's a factor or not, but I wanted to add that information.

For clarity, names are: "U-dual" (dualboot linux), W7-dual (dualboot Windows 7), W7-single (Windows 7 on completely different computer which is trying to see the shares on U-dual)

U-dual can see W7-single on the network and access its shares.
My W7-single can only see U-dual's computer name.
W7-single can see W7-dual on the network and access its shares
All computers share the same Workgroup
W7-single and W7-dual are in a Windows Homegroup
U-dual and W7-dual have the same IP address

---

### Post by TheFu on 2014-06-05
Doesn't "Homegroup" involve some Microsoft-only security techniques?

I don't think [valid hostnames are allowed to have underscores]("https://en.wikipedia.org/wiki/Hostname#Restrictions_on_valid_host_names").  Dashes, yes. The is in the DNS specifications used world-wide.  This may or may not be an issue.

Have you tried accessing the shares by IP address?  smb://192.xxx.xxx.xxx/ into the URL.

How do you know they are all in the same Workgroup? Did you setup something in Samba?

And ... I wouldn't worry about the MAC address/DHCP thing too much - the worst it should do it cause delays in seeing the new hostname between reboots.

---

### Post by mysubs on 2014-06-05
Sorry, the "U-Dual" name (etc) was used as an example for the purpose of the forum thread.  The actual names are either single words or involve dashes, I'm just not sure what the names are off hand since I'm not at home while posting, at the moment (** I forgot about that "_" naming convention, so I've edited my earlier post to remove that confusion).

I know the Windows computers are within the workgroup "Workgroup", because that's the default and I haven't changed them.  I haven't explicitly specified anything pertaining to "Workgroup" in Ubuntu, but I did see the "Workgroup" value within the Samba Server Configuration **Server Settings**.

[IMG]http://i.imgur.com/jVdxnii.png[/IMG]

Homegroup is a Windows-only network configuration, as far as I'm aware.  It sucks, it interferes with "normal" networking between other Windows systems.  Networking with XP was so much easier.  But establishing it was necessary to connect W7-single with W7-dual (back before W7-dual was a dualboot).  So I'm not sure if that Homegroup setting may be interfering with W7-single's ability to connect with Ubuntu.

Last night as an experiment, I tried to access the W7-single shares from U-dual, but oddly enough they weren't there; I couldn't even see the W7-single computer on the network from U-dual.  Could it be a firewall setting?  It seems like what I'm trying to do should be pretty straight forward and pretty common.  I know there's got to be something simple I haven't noticed.

---

