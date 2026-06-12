---
title: "Deluge + nmap + port problems"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Max_Mackie on 2010-01-06
Okay, first of all, I'm having some port troubles which lead to torrent downloading problems. I want to download as many flavors of linux possible and archive them on a HDD.

First of all, I try downloading a torrent regularly, and it doesn't work. It just hangs and I have a little infinity sign in the ETA column.

Second, I try downloading (incoming and outgoing) from port 80 (because it technically has to be open if I'm surfing the web, right?). Doesn't work. 

Third, I tried seeing what ports WERE open by scanning my public IP with nmap (sudo nmap -sS IP). That told me that a couple ports WERE open (including 80) but they don't seem to work in Deluge.

Finally, I tried another bittorrent client and the same things happened to me.

Any help is appreciated.

---

### Post by cariboo on 2010-01-06
I know it is supposed to be evil, but I use UPnP. If you are behind a router, make sure you have UPnp enabled. Then open Deluge and go to Edit-->Preferences-->Network, and make sure random ports incoming and outgoing are selected, then click the **Test Active Ports** button.

---

