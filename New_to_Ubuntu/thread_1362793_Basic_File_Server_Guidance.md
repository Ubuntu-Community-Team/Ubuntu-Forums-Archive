---
title: "Basic File Server Guidance"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ronbo613 on 2009-12-23
Hello everyone-I'm a rank first timer here; I wasn't sure if I should ask this question in the Server section or the Beginners section so I'll give it a try here.
I want to build a file server using Linux; not only for the server, but I want to learn as much as I can about Linux at the same time. I'm not looking for real specific information right now; just a little general advice to see if I'm getting off on the right foot.
I do a lot of video and graphics work and just built a smoking Quad-core computer; leaving me with a perfectly good Pentium IV 3.4G, 2G RAM on an Intel 875PBZ motherboard in a large Antec full tower case. I would like to turn this computer into a server. I understand it may be a little more power hungry than most servers; but I don't want to stick a perfectly good computer out in the garage.
This server will hook up to the Win7 64bit Quad core workstation, a Win7 64bit and XP Pro laptop. I would like to have a number of hard drives in a RAID array like a RAID 5 or RAID 10. I probably have 6-7TB of hard drives; mostly in external enclosures; it would be great to consolidate all these drives.
I've started checking out the Ubuntu Pocket guide and looking around Samba; which to my untrained eye seems like it might be a good way to go.
If any of you have any general advice or insight about this; I would really appreciate anything you have to say.
Thanks in advance-Ron B

---

### Post by Geoff918 on 2009-12-23
> **ronbo613 said:**
> Hello everyone-I'm a rank first timer here; I wasn't sure if I should ask this question in the Server section or the Beginners section so I'll give it a try here.
I want to build a file server using Linux; not only for the server, but I want to learn as much as I can about Linux at the same time. I'm not looking for real specific information right now; just a little general advice to see if I'm getting off on the right foot.
I do a lot of video and graphics work and just built a smoking Quad-core computer; leaving me with a perfectly good Pentium IV 3.4G, 2G RAM on an Intel 875PBZ motherboard in a large Antec full tower case. I would like to turn this computer into a server. I understand it may be a little more power hungry than most servers; but I don't want to stick a perfectly good computer out in the garage.
This server will hook up to the Win7 64bit Quad core workstation, a Win7 64bit and XP Pro laptop. I would like to have a number of hard drives in a RAID array like a RAID 5 or RAID 10. I probably have 6-7TB of hard drives; mostly in external enclosures; it would be great to consolidate all these drives.
I've started checking out the Ubuntu Pocket guide and looking around Samba; which to my untrained eye seems like it might be a good way to go.
If any of you have any general advice or insight about this; I would really appreciate anything you have to say.
Thanks in advance-Ron B

Sure, that all seems doable.

It's pretty easy. I never used Linux until January of this year. I've now set up dozens of systems, installed 4 servers, etc. And, it was tricky at first. But, once you get used to just reading what the system tells you to do--it's cake.

For instance, my first error message was "You need to run dpkg --configure". I was not sure what to do then. But, oddly what needed to be done was to execute "dpkg --configure".

Having been a PC/MS-DOS user and MS Windows user my whole life and being very good with computers I never realized how easy and powerful something like Linux can be. You'll be set. The forums are helpful, Google is helpful.

If you download and burn a Server CD you're already halfway there. Ubuntu comes pretty much stock configured. It probably doesn't even take much knowledge to have a working setup. Maybe none.

---

### Post by ronbo613 on 2009-12-23
That's very encouraging. I started out with FORTRAN and worked through all the MS concoctions as well so I'm thinking I can handle Linux.
I always have a cloned boot drive for my computers so even if I screw up; I can go back to Win XP if needed. I think I've had my fill of Windows though; I am hoping there is something else.

---

### Post by Paqman on 2009-12-23
So do you have any experience of running a server?

Ubuntu comes in two main versions: server and desktop. By default the server version has no GUI, since servers are normally run headless and administrated remotely via the command line. If you want something a little friendlier on the remote machine you can use tools like Webmin to make the whole thing a bit more point-and-click. If you want to be a bit more 1337 then you can just use something like PuTTY to get to the command line.

The other option is to give your server a GUI, which is as simple as installing a couple of packages. It's normally considered a bit superfluous to run a GUI on a server, but if you're not confident using the command line it's a valid option IMO.

---

### Post by ronbo613 on 2009-12-24
I wouldn't have a problem with command line operation. I've already spent too much time pointing and clicking my way through the last few Windows offerings.

---

### Post by 3rdalbum on 2009-12-25
Samba uses a text configuration file, that you manually edit in order to set up. If this sounds like too much work, you can install a GUI on your server (or use Ubuntu Desktop) and install the "system-config-samba" package. It makes it point-and-click to set up a server, and it's really worth it.

Samba is definitely what you want for file sharing cross-platform.

---

