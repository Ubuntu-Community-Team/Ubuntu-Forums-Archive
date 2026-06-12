---
title: "Network and installation problems"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2007-04-21
Hmmm...I'm a bit at my wits end with this one. I've just built myself a dual core 64 bit machine. Everything seems to be working fine. I installed XP yesterday and it's been working brilliantly. So, then time came to install Kubuntu. I'm going to list everything that I've done in the hope that someone can see the problem and perhaps point it out to me.

I'd downloaded the 64 bit version of Edgy, so I thought I'd give that a go. Nothing. I chose to boot from the CD and got as far as the splash before it just seemed to freeze. Even the splash looked weird....kind of bad graphically. Anyway, I tried a few live distro's and they all seemed to come back with the acpi fault. So I tried again using "acpi=off" and the 64 bit version of Edgy did boot, but for some reason, when it booted up, it didn't recognizing my USB mouse so I couldn't do a great deal once there.

So I went back to 32 bit Dapper and tried to install that. It installed fine. But on reboot my machine just booted right back into XP. No GRUB at all. No warning that there was a problem. It was just as if GRUB hadn't been installed at all. So I reinstalled Dapper again in case something had gone wrong first time around. Same problem again. So I decided to try installing another distro. I chose Mepis and it installed fine. But on reboot, although GRUB was there, the paths were incorrect and no matter which option I chose I ended up with an error 22 message. So I tried to install Dapper 32 bit again. All went smoothly, and this time GRUB was there...I suspect left over from the Mepis install, but again the paths were incorrect. Anyway, I worked out what the paths should have been and edited the text file to reflect the true paths, and lo and behold I can now log into both XP and Kubuntu.

Now I have one SATA drive (XP partition 1, SWAP partition 2, Kubuntu Partition 3 and an as yet unpartitioned section at the end) and one PATA drive, all fat 32 and basically for music files and storage. But I can't work out why I'm having so much trouble when usually installing Dapper's such a cinch for me.

On top of all this, despite me being able to log into Dapper, I can't connect to the internet. When I ran the live distro of Dapper, before installing it onto my hard drive, I generally have to adjust the netowrk settings as I get the DNS problem because of my router (D-Link DSL-G624T). Usually I have to adjust Firefox too as the IPv6 problem gives me grief, and edit the resolv.conf file to resolve the DNS problem, both of which I did whilst running the live distro, and which corrected the problems nicely. Even without solving these problems however I could always connect through Konqueror. The problems I had were mainly to do with updating Kubuntu and using Firefox. However, after doing the HD install I can't even connect through Konqueror. I checked to make sure the DNS fix settings had carried through during the HD install and they have.

So I'm at a bit of a loss as to what's happened.

I should also point out that I re-tried the 64 bit live distro of Edgy again, this time with a PS/2 mouse, since it wasn't recognizing my USB one, and it worked fine this time....BUT....wouldn't connect to the net in exactly the same way, so I was loathe to try a HD install.

Any ideas folks? I'm a relative Noob to Linux so don't freak me out with any crazy tech talk. Stick drawings and simple sentences only please

Kind regards....mel

---

