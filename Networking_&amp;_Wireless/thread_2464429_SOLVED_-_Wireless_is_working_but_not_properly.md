---
title: "SOLVED - Wireless is working but not properly?"
date: 2021-07-01
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2021-07-01
I have recently started using Steam remote play from my Windows desktop which is connected to my LAN via ethernet. The Xubuntu remote is over a 150mbit wifi adapter. TPlink, 12 bucks on Amazon or so. Amazingly the stream works great. I didn't expect it but totally usable and playable.

The problem happens when I use it, then leave it for an hour or two. When I come back Steam can see the remote computer, it can see the remote game available and the list of my other games. But it will error out saying it cannot connect to the remote computer. If I manually disconnect then reconnect the wireless on the Xubuntu box it works flawlessly. Before the disconnect / reconnect my network works fine. Kodi pulls from my server just fine. Browsing works just fine.

My solution at this point is to run a wire. I'd rather not although this being a modular home I can get underneath and it isn't the end of the world. I'm more curious as to why this is happening just because it's so damn ridiculous. I'm also curious how to trace it down. I think it may be an issue my wife has with Minecraft on that box as well. First thing in the morning when it is turned on Minecraft loads near instant. Later in the day 2-3 minutes at least before it is ready to run.

I wasn't sure if this was Networking or Gaming. Since it appears to be multiple games? I'm thinking it's an underlying issue with the wifi? I don't know though. It's a vanilla netplan file just using Network Manager. Wifi is connected in the XFCE menus.

I did try manually adding the wireless dongle to the netplan file but it fails to start up with an error about not being able to negotiate or something. I'll have to retry that one.

Ideas? Suggestions? Give it up and just run the damn wire?

EDIT - solved this by giving the machine a static ip on it instead of relying on the dhcp server to assign it a static ip. I don't understand why this works but it does. Reasearch led me to networking. That combined with it working when reconnecting wireless and its good now.

---

