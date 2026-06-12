---
title: "Something is rfkilling my WiFi card on boot."
date: 2017-10-24
forum: Networking &amp; Wireless
---

### Post by Manaan on 2017-10-24
The 17.04 -> 17.10 upgrade broke a few things that I'm stumped on how to fix, so I guess I'm going to post about them one at a time until they're all solved. Hey speaking of which, is it normal to have upgrades break stuff? That's pretty annoying if so. I may have to stick with LTS if I'm going to have to manually fix things for every update. :/

So my system is set up a little bit strangely. I'm using i3 on Xubuntu, and my network manager is wicd instead of NetworkManager.

The problem I've been having is that when I first boot, my WiFi and ethernet are both rfkilled automatically. And I have to go into a terminal and manually un-rfkill them. Hey speaking of which, why does rfkill exist, anyway? Isn't "rfkill block <foo>" a fancier version of "ifconfig <foo> down"? It seems redundant, and the manpage isn't much help.

But anyway, I'm trying to figure out what's doing the rfkilling so I can disable it. I *could* just have an autorun script to "rfkill unblock" everything for me, but that seems like it'd come back to bite me at some point.

As soon as I "rfkill unblock" everything, it's fine until the computer turns off again. I'm *preeeetty* sure that logging out and back in again won't trigger another rfkill. I might test that after I'm done with this post.

I looked through the settings on wicd-client and there wasn't anything that seemed helpful there.

Also, I checked just to make sure that NetworkManager isn't installed, and it's not:

```

$ sudo apt remove network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'network-manager' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Here's my wireless-info: [https://paste.ubuntu.com/25810049/](https://paste.ubuntu.com/25810049/)

I'd really love some pointers on what to try next. Thanks in advance for the help!

Edit: The problem just kind of... went away on its own. Huh. Solved?

---

