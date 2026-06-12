---
title: "Help with network audio broadcasting, Icecast2?"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by Geonovast on 2014-03-20
Hello!  My name is Correy, and I'm new to Ubuntu, Linux, and the forum.  I recently installed Ubuntu 14.04 LTS onto an older Dell Optiplex GX-620, and it runs pretty nicely.  Taking a bit of getting used to, but I like it.  I set this up mainly to run as my network's DHCP and DNS servers, as well as a local webserver for when I get around to playing with Apache.

However, I would also like to broadcast my own radio station, but limited to my private network.  I do not want it to broadcast to the internet like every Google search result thinks is the plan.  I found I should be able to do this with Icecast2, but after following serveral online guides, nothing worked.

All the music is on a Linksys NAS 200.  The folder it's in has been mounted as a network share.
I want to stream the music to a Linksys WMLS11B, which tunes in by URL/IP and port number.

There are 3 NICs in this machine.
eth0 (onboard) is static to 192.168.1.40, and set to primary.
eth1 (PCI card) is static to 192.168.1.41 for DHCP
eth2 (PCI card) is static to 192.168.1.42 for DNS

The first guide got me as far as installing Icecast, with nothing beyond that telling me how to actually play the music.  Next one got me to playing with a music player, and Icecast would broadcast going off of the output from my sound card.  Well, that didn't work, so I found yet another guide that insisted I needed to install yet another program to swap the mic input and speaker output as Icecast would play off of the mic.

At this point I decided to remove everything I'd installed, and ask the pros.  I'm pretty intuitive, I can figure out how to do quite a bit on unknown programs... with a gui.  The absence of guesswork in command line kind of throws my learning curve out of whack.  Didn't have much trouble with isc-dhcp-server or bind9, though.

What really confused me, however, was after I removed the programs and killed the services, I tried the station again on my radio to see if I was still getting the same error message... and it played 10 seconds of a song, then quit and the said the connection was down.  *After everything was off.*

Thanks in advance!

---

