---
title: "Long transfers hang"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by claco on 2007-09-06
I've had Feisty running on my laptop since it was released and I was very happy to finally have the wireless card (Dlink DWL-G650 hw/fw B5/2.54) JustWork against my G network with WPA. This card uses the Atheros drivers and for the most part it's been trouble free (other than poor connecton quality compared to running Windows).

My big problem now is that downloading or uploading files yields what I would call hangs/resets. For example, when uploading 1-2MB pictures to Flickr, they get about half way through 1 picture and just hangs. When downloading new software via Synaptic or the Update manager, sometimes it just hangs. Restarting the process usually succeed for downloads, and for uploads, it almost never works. I still to this day can't bulk upload photos on Feist, but don'w have any problems using the same tool under windows (jUploadr).

Even when doing apt*ing on the command line will just pause/hang doing dowloads. I've seen chatter in various forums about similiar problems, but nothing conclusive with a solution.

Ideas?

---

### Post by blugord on 2007-10-14
I have pretty much the same problem with my laptop + Ubuntu 7.04. 

I have wireless card D-Link DWL-610 with ndiswrapper + windows drivers.

In my case it seems that downloading files of any size works perfectly but uploading over about 100kB files makes it hang and files are transferred only partially. There is also a problem with SSH connection. For example, when I try to edit a text file on a server (nano + some.php)  through ssh connection, it totally hangs after 20s-1 min or so and the terminal must be forced to close.

Same functions on my desktop machines (Suse, Debian etc.) and also SSH connection between my home servers and laptop seems to work just fine, so I think there's no problem with home network or hardware. :confused:

Probably (and hopefully) this is resolved when 7.10 comes out... Any suggestions would be appreciated!

---

