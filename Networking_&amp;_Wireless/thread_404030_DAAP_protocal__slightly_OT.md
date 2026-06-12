---
title: "DAAP protocal / slightly OT"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by linuxaz on 2007-04-07
Hello,
While testing the latest version of Ubuntu, I ran Rhythmbox and noticed
some strange choices in my "library" section.  There was a computer name
showing up as a DAAP share in the new version of Rythymnbox!  From clicking
through the details of the individual shared songs, I saw that the file
name was indeed an IP on the cox network.

Now, I have not used DAAP before on my local lan, but have been doing some
reading about it now...cool stuff, and I'm able to share my wifes I-tunes
songs to my various Linux boxes on my local Lan.

Now to my question:
Why is these other peoples DAAP shares, I've counted 5 so far, keep
appearing and dropping out?  why the heck are they there at all?  I'm
running a hardware firewall/router here, and do not have DAAP sharing
enabled now.  Why was I see these other machines?  I would think that their
router (if the have one) would be blocking access to that port?

I know there are other Linux users out there, so if you don't mind....chime
in on this.

Regards,

linuxaz

---

### Post by spd106 on 2007-04-08
The DNS-SD protocol used to advertise these DAAP shares should not be able to tranverse beyond the local network, unless you have enabled remote sharing on the router. As far as I am aware only Apple's newer routers such as the extreme can do this. I haven't used one so I've no idea how you would check.

It uses port 5353 by default, so I suppose you could check that it isn't being forwarded anywhere.

As you join other networks you will see other users with DAAP sharing enabled, that's the beauty of Bonjour/Zeroconf/Avahi.

---

### Post by linuxaz on 2007-04-08
spd106,
The only port I have forwarded on my router is for bittorrent...  I know that I am not sharing my music, and should NOT be seeing them beyond my local lan.  But as of last night, there was another.
The test site grc.com says all is stealth here on my end.
linuxaz

---

