---
title: "Campus network help..."
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Adski13 on 2007-09-30
Hey guys,

I am still a relative newbie to Linux (using Feisty at the mo) but doing my best to learn as quickly as possible to try and leave the world of Windows behind me!

On to my issue...

I have recently arrived at the University of Kent.  I got into my room and was presented with my ethernet cable (I love freebies!) and the wallport.  Hooray thought I.  Nice and simple.  Unfortunately, upon reading the documentation provided, it seems there is no "official" support for Linux on site.  It helpfully informs me however that "some users sucessfully use various distributions of Linux every year!" which simply makes me feel stupid because i can't!!!

Anyhoo, i've read all the online documentation using my XP laptop (this luckily works so I'm not completely internet-less!) but all I've managed to glean is that to access network services I'll need Samba, and that I'll need to change my Samba NETBIOS name (although it doesn't specifically tell me what to change it to), but other than that, i've got little or no idea why i cant access the web.

The website I've been using as reference is:

[http://www.kent.ac.uk/is/computing/sbs/support/linux.html](http://www.kent.ac.uk/is/computing/sbs/support/linux.html)

The other info i do have is that if you're using a Windows or Mac OS then you need to name your PC using the format "PCSBSabc1" where abc1 is your username.  On Windows PC's, you also need to be part of the "SBS" workgroup although this is presumably simply to allow access to network services.  Also, they use DHCP to issue IP's.

I haven't yet been to the helpdesk to ask them (Freshers week and the start of my course has meant time is a little tight at the moment!) but i though it might be a good idea to check on here first as I'm not really sure what to ask them!  Is there any specific information I ought to get from them?  Also, is there the possibility I'm doing something blindingly obviously wrong?

I doubt it's a hardware issue as my PC was working fine at home on a standard router configuration.  I have been fiddling with my install quite a lot lately however and may have cocked something up (but again, I'm not convinced).  I'm thinking about doing a fresh Ubuntu install when gutsy comes out incase it is the install but regardless, I suspect I'll need a hand configuring that!

Any help would be greatly appreciated even if it's just giving me some hints on what questions to ask, as I hate using my woefully underpowered laptop for everything and I really don't want to have to re-build my Linux box with XP (and i don't really want to dual boot either).

If you need any more info (which no doubt you will) let me know and I'll do my best to find out and post it up here!

Cheers guys!

Adski13

---

### Post by RandomJoe on 2007-09-30
Reading over that help page, it doesn't sound like you need Samba except to get to file shares.  Getting online should only require using DHCP to get an IP address.  Ubuntu is set up for DHCP by default, perhaps you changed the ethernet port to a fixed IP at your last location?

Have you made sure the network cable is plugged in before booting the machine?  If you aren't using network-manager or it isn't working correctly, your system may only do a DHCP request when first starting.  Network-manager ought to see the cable get plugged in and request then, but I've had instances (at least on older versions, I'm still running Dapper) where it doesn't for some unknown reason.

I'm not well versed with Samba on the client side, I thought the /etc/samba/smb.conf was only for the server but you can change the workgroup name there.  I would certainly caution against running the server, unless you intend to share files from your computer - as their help page mentions, it's possible to configure samba in such a way as to disrupt their network.  IIRC, you just need to run 'smbclient' with the appropriate options to access a remote share.  Hopefully someone else will have something to say on this.

Not a huge amount of help, but perhaps it's something...

---

