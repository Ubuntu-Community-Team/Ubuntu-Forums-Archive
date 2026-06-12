---
title: "What I got goin on right now need suggestions"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by hokie88 on 2009-01-06
Right now I have my laptop dual booting, windows xp tablet edition, and Ubuntu 7.04, I also hooked up some computer I used to have from last decade up to DSL linux via live cd and boot floppy and duct tape, its got no harddrive at the moment I might do something about that. 

I have an ethernet cable running between the two and I know nothing about networking or how to connect the two or even what I can do if they were connected. 

See, I was thinking maybe about making the old junky desktop a file server but then I'm thinking whats the real difference between that and my 1tb external harddrive, unless the file server was hooked up to the internet or something and i could go on there wherever and get my files that would be awesome but I have no idea how to do that.

keep in mind i am dealing with 128mb ram 1.8ghz pent 4 and usb 1.1 ugh

So I guess what I am looking for is if someone has some good information on what I should do with my desktop running DSL let me know. I would also be interested on getting my hands on easy beginner guide to hooking pc's together or how i could put this computer online.

Thanks,

I'm very nastalgic for it it was my first cp this is more of a fun project some other ideas i had for it was grid computing for the aids research, or something like that where it would be useful or a server for ancient software idk i am rambling..

---

### Post by tuxxy on 2009-01-06
Sounds like you want to get a HD in that old machine and try out a server distro such as Ubuntu server and this can be then a web based file server :)

---

### Post by linux6994 on 2009-01-06
Easiest way for setting up 2 or more PCs is on a router with Ethernet cables going to each. Each PC whether or not Windoze or Linux needs to be in the same workgroup with a directory shared on each. This makes file sharing simple. Most routers are have ports both wired and wireless. All PC would connect to the LAN side of it and the WAN side would connect to your Internet whether it is DSL or Cable. Effectively your router will look like a PC and all connected devices will share that connection.

This is the most common configuration going and easy to set up. Please givr it a try and ask this forum for any additional help.

As far as accessing your files from the Internet a real easy and secure way is via FTP (File Transfer Protocol) Each Ethernet connection has many ports and using ports 21 and 22 for file transfer is easy to set up. We can help.

Good Luck!

[http://www.howstuffworks.com/home-network.htm](http://www.howstuffworks.com/home-network.htm)

---

### Post by handydan918 on 2009-01-06
> **hokie88 said:**
> 

keep in mind i am dealing with 128mb ram 1.8ghz pent 4 and usb 1.1 ugh



Wow. 
Your first computer was a P4? I AM getting old...
Seriously, just put some ram in that thing (along with a hard drive, obviously) and it will scream. Any P4 should be good for at least a gig of ram. Stuff that in there and you'll be able to use that thing for everyday use.

---

### Post by efexD on 2009-01-06
> **handydan918 said:**
> Wow. 
Your first computer was a P4? I AM getting old...
Seriously, just put some ram in that thing (along with a hard drive, obviously) and it will scream. Any P4 should be good for at least a gig of ram. Stuff that in there and you'll be able to use that thing for everyday use.

Don't feel too old my first computers OS was windows 3.1ish which is pretty old :P

---

### Post by -kg- on 2009-01-07
> **efeXor said:**
> 
 > Originally Posted by handydan918  View Post
Wow.
Your first computer was a P4? I AM getting old...
Seriously, just put some ram in that thing (along with a hard drive, obviously) and it will scream. Any P4 should be good for at least a gig of ram. Stuff that in there and you'll be able to use that thing for everyday use.

Don't feel too old my first computers OS was windows 3.1ish which is pretty old :P

Yeah, a little more RAM and a fair sized hard drive (doesn't have to be HUGE) and you should be good to go with a P-IV.

First OS was 3.1, eh?  My first *real* computer (discounting my RS PC (Pocket Computer)-II) was CPM based ***in ROM***, with major "software" built in to ROM as well.  64K of RAM (yes, *kilobytes*...but no one will ever have any use for over 640K of RAM, anyway!) and no internal drives of any kind.  It was a RS TRS-80 Model 100 laptop.

I then graduated to a desktop...a RS TRS-80 Model 2000 with an 80186 processor (once again, a ***'186,*** not a '286) with dual 5 1/4 floppy drives (true floppy disks) and 128K of RAM (though I put in a memory expansion card, upping me to 384K), running a hacked version of MSDOS (due to the differing architecture of the machine).

I basically stuck with DOS throughout the early Windows years (I remember seeing Windows 1.0 on the software shelves back in the '80s) up until Windows 95 came out.  Still have several of my old DOS computers...an IBM 8086 based machine with dual floppy drives and a Leading Edge '386-SX 16 Mhz that actually came with a 10 MB hard drive and 1 MB of RAM (Ooooo!)  :P  And, of course I still have my Model 2000.

But I know there is *someone* out there that can one-up me.  Any Altair users out there?  At least, Commodore?

---

### Post by hyper_ch on 2009-01-07
get a debian sarge cd, install it and then install samba, openssh-server and all other tools. Don't put an x server on it, just make it purely command line.

---

