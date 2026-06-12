---
title: "56k Connection Issues using gnome-ppp"
date: 2005-05-29
forum: Networking &amp; Wireless
---

### Post by jkndrkn on 2005-05-29
My computer currently connects to the internet using a usb wireless network adapter. I am trying to set up my external serial modem.

I've tried using the Networking gui, and it doesn't seem to handle the modem very well. Someone recommended I use gnome-ppp, and that gives me a much nicer interface and the ability to read about the connection status.

Here's the issue. I run sudo gnome-ppp from the command line and I can see that everything is going well. A connection is established and I get a bunch of messages from my ISP. IP and DNS servers are set, and everything is pretty.

However, unless I enter the Networking gui and deactive and uncheck "device is configured" on my wlan connection, firefox returns a "site cannot be found" message every time I try to navigate somewhere. Apt-get in the command line immediately fails.

When I *do* deactive the wireless device and uncheck "device is configured" for my wlan, firefox seems to be trying to navigate to the site but eventually times out. Same with apt-get in the command line.

Here's what I'm thinking. Ubuntu is convinced that the only route to the internet is via my wireless connection. I need to let Ubuntu know that there is another way out to the internet. However, I'm not sure where to go to make this happen.

Any observations or suggestions?

---

