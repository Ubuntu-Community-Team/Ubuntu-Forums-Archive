---
title: "Unable to maintain internet connection without restarting router"
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by mckempt2 on 2016-12-07
Hello,

Ubuntu 16.04 with crappy AT&T U-verse internet and AT&T brand router. I don't pay the bills here.

Originally I had a problem getting kicked off the internet until I connected my desktop to my Google account under 'Online Accounts' in settings. Everything worked great for a little while. (I use Chrome)

Recently, I've been having an issue with my wireless maintaining an internet connected to the router. My wireless access card picks up the wireless network (I can see it under the network settings...) but fails to automatically connect despite it having checked to 'automatically connect at startup'. Regardless, when I manually select the wireless connection, it will always fail to connect until I actually get up and manually restart my router.

Is there a way around this? I've been checking through all sorts of network settings and don't see why it just randomly fails to connect and maintain a connection. My Chromebook and phone do not have this issue (They're always on the internet - it's just my Ubuntu desktop)

I'm willing to reinstall Ubuntu in case but since I'm  building a new Ubuntu computer in a month I'd like to not have to go through all those steps.

Thanks for any insight

---

### Post by TheFu on 2016-12-07
Find the **wifi-info** script referenced in these forums. Run it. Post the output back here. Just a guess, but suspect a driver issue or a driver setting needs to be tweaked.  Also, would be good to know if this issue happens when you are near the wifi-access point or only when far away, in a different room.

---

