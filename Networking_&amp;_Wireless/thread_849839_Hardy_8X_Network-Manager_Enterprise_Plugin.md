---
title: "Hardy 8X Network-Manager Enterprise Plugin"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by metallica1973 on 2008-07-04
I was reading this article 

[http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html]("http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html")

And notice that there is a WPA-Enterprise option when choosing to set stuff up on your wireless network using network-manager. What would be the name of the plugin for network-manager for WPA-Enterprise support.(PEAP,TTLS,TLS)?

---

### Post by spd106 on 2008-07-05
You will have to ask the network administrator which type you should be using and any other settings or certificates that you will need. Network-Manager supports most EAP methods.

[http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol](http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol)



If you're after VPN support then you'll want to install the extra plugins via Synaptic or some other package manager.

See [https://help.ubuntu.com/community/NetworkManager#VPN%20support](https://help.ubuntu.com/community/NetworkManager#VPN%20support)

---

### Post by metallica1973 on 2008-07-05
I have setup my own FreeRadius Server and am using EAP-PEAP/MSCHAPV2. I have hardy on my laptop and do not have any option for WPA-Enterprise as a choice for wireless. The highest it goes it WPA-Personal. thanks

---

