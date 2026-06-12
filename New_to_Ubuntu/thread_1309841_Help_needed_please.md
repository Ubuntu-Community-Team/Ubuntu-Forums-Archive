---
title: "Help needed please"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by LSD89 on 2009-11-01
Now first off, i'd like to say hello everyone. I dabbled with Ubuntu before, Fiery...something or other a while ago, but it didn't support my USB modem without a patch so I gave up on that.

However, I have a netbook now, so decided to give the Netbook Remix a go, since I generally like the cleanness and aesthetics of Ubuntu. If it's relevant I have the new 9.10 version, duel booting with Windows XP (just incase anything went wrong). I tested it out after making a LiveUSB stick for it, liked it, everything worked fine and dandy. 

However, after a full installation, I have noticed one (well two, the second is irrelevant really) problem that I didn't have just testing it before installation, and that is that it will not pick up my SD card anymore. or any form of external media Now i'm sure you are sick of hearing about this problem as I did google before coming here, but only found problems, with no solutions. So I was wondering if someone had actually found a fix for it? It's not essential, but has all my music on, although I do have Spotify currently running through WINE. And also, just for kicks, does anyone know the reason it worked when running it off a USB but not after installation.

My sincerest thanks for anyone who can help and my sincerest apologies for those who've witnessed this thread about 20 times.

---

### Post by cariboo on 2009-11-01
I'm not sure why it worked using the Live image and not in the install, but we can do some trouble shooting to see what is happening. Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n20
```

after you plug your device in, the above command will tell us whether the device is detected properly. Please paste the output of the above command in your next post.

---

### Post by LSD89 on 2009-11-01
```
[   27.368251] CPU1 attaching sched-domain:
[   27.368261]  domain 0: span 0-1 level SIBLING
[   27.368273]   groups: 1 0
[   87.686012] Linking with NETGEAR: channel is 11
[   87.726526] Linking with NETGEAR: channel is 11
[   90.236153] Linking with NETGEAR: channel is 11
[   92.752769] Linking with NETGEAR: channel is 11
[   96.873052] Linking with NETGEAR: channel is 11
[   99.393239] Linking with NETGEAR: channel is 11
[   99.433737] Linking with NETGEAR: channel is 11
[  101.944143] Linking with NETGEAR: channel is 11
[  104.457685] Linking with NETGEAR: channel is 11
[  108.580154] Linking with NETGEAR: channel is 11
[  110.612155] Linking with NETGEAR: channel is 11
[  115.953263] Linking with NETGEAR: channel is 11
[  115.970231] Associated successfully
[  115.970245] Using G rates
[  115.984632] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.624054] wlan0: no IPv6 routers present
[ 1639.264938] Now traffic is busy, please try later!

```Goobledee-gook to me i'm afraid haha :p Although seems to be about my router...

---

### Post by LSD89 on 2009-11-02
Well i'm allowed one bump per 24 hours, so thought i'd make use of it :popcorn:

---

### Post by LSD89 on 2009-11-03
Another 24 hour bump.

Please, anyone?


EDIT: Actually the latest update seems to have fixed it. Good times.

---

