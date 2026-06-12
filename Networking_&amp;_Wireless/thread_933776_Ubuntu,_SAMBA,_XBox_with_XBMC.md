---
title: "Ubuntu, SAMBA, XBox with XBMC"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Clappy on 2008-09-29
Hey everyone,

I have been trying to get a nightmare setup working and I think I have. I'll explain myself a bit but I am only going to add the last step that got it working because there are other threads pertaining to the rest.

Firstly, this is how I was connecting my XBox running XBMC to my Ubuntu machine:

Xbox <--ethernet-->  Airport Express <--wireless--> Linksys WRT54G v6(running DD-WRT) <--ethernet--> UBUNTU

It was a nightmare every step of the way, if you need help with getting the Airport Express to work in WDS mode, or how to install the DD-WRT software, or how to get Samba working properly, I can point you to the threads/sites I found the info from, but I'm going to omit those points for now.

After I had everything working but the samba shares on XBMC, I noticed something strange. When I created the samba shares in Nautilus (right click folder, sharing options), I renamed them to remove spaces, shorten their names, and remove capitalization (just for safety's sake). They were as follows:

dirname        smbname
TV Shows       tvshows
Movies         movies
Documentaries  docs
torrents       torrents
Music          music

Once I figured out that I needed to add everything to UserData/sources.xml (xbmc's samba config file), the only one that would work was "torrents". The rest, although correct in that file, would give a "could not find network" error or something like that. The only thing that fixed it was literally renaming Movies to Film, TV Shows to TV, and Music to Tunes (and using full Documentaries name), sharing them in nautilus with their exact folder names, then editing the sources.xml file accordingly on the XBox.

No other method worked, and I figured it was obscure enough to mention that "Movies", "TV Shows" and "Music" are somehow "reserved" names that the XBOX will not accept as Samba shares, and also that the Samba share name in Nautilus MUST match the folder's name.

Strange, but true. I hope to god this helps someone else who is thinking of setting up their old xbox to run media from.


Good day!

---

