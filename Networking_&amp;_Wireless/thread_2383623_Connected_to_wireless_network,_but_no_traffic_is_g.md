---
title: "Connected to wireless network, but no traffic is getting through."
date: 2018-01-27
forum: Networking &amp; Wireless
---

### Post by jimnms on 2018-01-27
My Ubuntu 16.04 notebook will not stay connected to my wireless network after a kernel update installed yesterday.  It still shows it connected, but no traffic is getting through.  I open a terminal window and ping the router, it shows Destination Host Unreachable.  If I disconnect and re-connect, it starts to get a reply, but will begin getting Destination Host Unreachable again in as little as 3 seconds up to several minutes.

Sometimes after a clean boot or restarting, it doesn't even detect any wireless networks at all, and I have to keep rebooting until it does.  Just now I had to reboot 3 times before it would detect networks and connect.  I was able to stay connected long enough to get the wireless-info script.  I ran it and this is the result:
[https://pastebin.ubuntu.com/26472378/](https://pastebin.ubuntu.com/26472378/)

A few minutes later it started reporting Destination Host Unreachable so I ran the script again and this is what I got:
[https://pastebin.ubuntu.com/26472385/](https://pastebin.ubuntu.com/26472385/)

After I re-connected so many times, it completely stopped seeing wireless networks.  I ran the script and this is what I got:
[https://pastebin.ubuntu.com/26472399/](https://pastebin.ubuntu.com/26472399/)

Before the 4.13 kernel update it would stay connected with no problems for days.  This occasionally happened, but disconnecting and re-connecting would fix it.  After the initial 4.13 kernel update, this happened more frequently.  After it installed a kernel update yesterday, it seems to be happening every few minutes.

---

### Post by praseodym on 2018-01-27
Same ESSID in 2,4 and 5 GHz region. Add the MAC address of the stronger AP in the **BSSID** section of the networking profile and reconnect.

---

### Post by jimnms on 2018-01-29
I don't see how that will fix the problem when it sometimes doesn't see any networks at all.  My network equipment and setup has been the same for years, and this just started happening right after the kernel 4.13 update was applied.  I do use the same SSID on both the 2.4GHz and  5GHz frequencies, as I understand this is needed for clients that support connecting simultaneously to both for increased speed.  After I posted this I restarted the notebook and it was not seeing any networks at all.  Rather than rebooting until it did, because it's an old, slow notebook, I tried restarting the networking and Network-Manager services as well as physically turning off and on the adapter.  I don't know which combination worked, but it finally detected networks, connected to mine and has stayed connected since.

Just now, I went ahead and set the MAC address of the 5GHz radio in the BSSID to see if it makes it more stable, but if wont this prevent it from automatically switch to 2.4GHz if it moves out of range of the 5GHz signal?

---

### Post by jimnms on 2018-01-31
It didn't work.  When I set the MAC a MAC address (either one) in the BSSID, when I re-connect it creates a new network profile without the BSSID MAC address and prompts me for the network's password.

---

