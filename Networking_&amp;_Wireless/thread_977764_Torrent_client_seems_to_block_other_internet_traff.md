---
title: "Torrent client seems to block other internet traffic"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by RadicalRaid on 2008-11-10
When I'm downloading using Transmission ( also tried Vuze ) on my desktop, my laptop can't connect to the Internet. Although I am connected to the router ( a Linksys wrt160n ) it seems as if no internet traffic is allowed. I can ping the desktop from my laptop and also use remote desktop viewer.
I should mention that the desktop is wired ( as is my Playstation 3, which also can't seem to use the internet when my desktop is downloading ). My laptop is connected wireless. I did try using a wired connection on my laptop also, but no success..

On my laptop as on my desktop I am using Intrepid Ibex.

I hope anyone has a suggestion.. Every opinion is appreciated!

---

### Post by cariboo on 2008-11-10
You have to set upload and download speed limits. In transmission go to Edit-->Preferences-->Network, and set the upload and download speeds that allow you to use your network connection while downloading torrents.

Jim

---

### Post by RadicalRaid on 2008-11-10
I did. Limited upload to 30 kbs, I should have 150 available, but nothing seems to be left.
Are there any other settings I should look out for?

---

### Post by RadicalRaid on 2008-11-10
Bump for great justice!

---

### Post by RadicalRaid on 2008-11-11
I've found out that Linksys routers don't seem to play nice with torrent clients if you have a lot of peers connected. So it seems like multiple connections may make it so slow for other computers, that it's unusable.
I've just flashed the firmware to dd-wrt in hope of better results, but no luck yet. Also the Copperjet 1616-2p could have something to do with it..

---

### Post by RadicalRaid on 2008-11-17
To whom it may concern: The problem was the 1616-2P modem. It gets can get frozen on one connection and no other traffic seems to be allowed. The simplest sollution is to simply reboot it, or unplug it for 5 seconds ( the latter will make you lose custom settings like port forwarding, so watch out for that! ). Now I just need to find something to fix having to reboot my modem several times a week. But that's not the worst problem in the world.

---

