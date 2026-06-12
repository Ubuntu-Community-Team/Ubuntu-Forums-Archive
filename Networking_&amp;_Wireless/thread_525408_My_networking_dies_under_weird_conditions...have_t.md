---
title: "My networking dies under weird conditions...have to reboot"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by reuben on 2007-08-14
Hope somebody can help me here.

1) Symptoms

* Wired networking (over 3com soho card that's worked flawlessly in various 'nix distros, including the last 4 ubuntus, for years) suddenly dies under certain conditions (see below)
* /etc/init.d/networking restart doesn't bring it back up
* /etc/init.d/dbus restart doesn't bring it back up either
* The device (eth0) is there (ifconfig shows it) but all transmits time out
* I have to reboot to get networking back up. This sucks... :confused::confused:

2) Cause?

It used to be that running torrent downloads at full speed for a few hours would cause the above (also, once doing an scp over the local network of a large number of files caused the same problem). I thought it was the router, and swapped it out with another one. Same problem. I tried lowering the torrent download speed, and the problem went away...for a while. However, I think the bandwidth was a total misdiagnosis - now I have 5 torrents lined up, and just minutes after starting them (using either Azureus or Deluge) the networking dies. 

So, I'm thiinking this is either a certain port or combination of ports, or a certain number of connections, that is causing the bug.

In case it was a card driver issue (although again, I don't see how it would be since the card's been solidly reliable for years) I tried plugging into my mobo's ethernet port. Unfortunately this port doesn't work (isn't recognized)...I'm sure it used to be, so I'm not sure what's going on there.


Please help me out here, as this is really driving me nuts.

Thanks

---

### Post by alphane on 2007-08-14
Does cycling the router power off/on again help?

This sounds just like my issue, and I can solve mine with a router restart (rather than full reboot).

When I hit problems (usually 2-3mins after closing Deluge) everything freezes.

Typing "route" shows that my default gateway is still my router, but I can't ping it or access any other IP...

Similar problem?

---

### Post by operator207 on 2007-08-15
Do you have another card laying around? We saw the same problem (though in freebsd and CentOS boxen) with some 3com ethernet cards at work. Replacing them with other cards, some even cheapo cards, fixed that problem.

Try replacing it with another card, ethernet cards are really cheap now.

---

