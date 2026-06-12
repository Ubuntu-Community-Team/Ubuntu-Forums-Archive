---
title: "How do I save a network location profile in Xubuntu?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Belathor on 2007-05-11
Hi,

I have Xubuntu 7.10 on my X41 laptop and wireless isn't a problem. However, I would like to be able to at least manually select my location profile in the Network Settings dialog. It appears that when I click the "Save current network configuration as location" button, nothing is added to the list of locations. I search the forums and all I found was a guy lamenting that they couldn't set their profiles either on Dapper Drake. Can other people set Network Locations, or is this a bug in the software?

Thanks!

---

### Post by febrile on 2007-05-17
Yep, I've just run into the same problem on Xubuntu feisty: the network location save dialog appears ok but doesn't do anything. I can see that the current network config settings appear directly in /etc/network/interfaces, but I'm still too n00b to shed any useful light on how saved location configs are/should be handled, Hopefully bumping your post like this might catch the eye of some wise folk.

---

### Post by Belathor on 2007-05-20
Hi febrile,

I was able to save a network profile by going to a different tab. However, I ended up installing network-manager and network-manager-gnome and using that instead.

---

### Post by febrile on 2007-05-20
Different tab in the standard Xubuntu network settings dialog, you mean? doesn't work for me. I think the default network settings dialog in Ubuntu is the same, and that one saves locations ok. So I'd guess it ought to be fairly straightforward to get it to save locations in Xubuntu. If I was more familiar with the workings I'd have a go.

I agree network-manager's the best bet at the moment for folks who use >1 fixed IP location - probably includes you. I'll hold off for now as I'm only switching between 1 fixed IP location & 1 DHCP. When I switch to the DHCP one, the network settings dialog holds onto the fixed IP etc (it stays in etc/network/interfaces but is overridden by DHCP setting).

---

