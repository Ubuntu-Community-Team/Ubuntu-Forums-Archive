---
title: "Ralink's craps again"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Ren McCourtey on 2007-02-12
Hi all.
I found local topics marked as solved but still full of users whom can't get these cards working. I'm one of them..I spent last week trying to make rt61 based card to work in openSUSE 10.2 and although I finally won, decided to left SUSE after years of using becouse of plenty of other problems (but who haven't them, right?). Of course I choosed only more popular distro and ended here.

But Ubuntu's problems with these chipsets goes much deeper, actually leads to kernel panic often. I followed [instructions]("http://ubuntuforums.org/showthread.php?t=296822") (I didn't downloaded kernel headers) on AMD64 with WPAPSK enabled, everything went flawlessly, I ifconfig ra0 up and oh no, what's going on, hardlock, reboot, analyse, it's a kernel panic! How it could be possible, this problem is almost year old, how it could still prevail?

Of course I would very appreciate help but much more I would like to know why are these cards widely recommended to buy for linux users? But I know why. It becouse drivers are opensourced. What You say, it doesn't work? It doesn't matter, it's opensource! You got my point? Opensource is realy great thing, but it's far second to functionality. And this piece of crappy code ralink calls a driver is useless, and make them OSed can't save it..:( :( :(

---

### Post by Metaljaz on 2007-02-13
Try These instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo)

try setting it up without the encryption. if you get it working, on to step 2: add the encryption.

with linux comes patience

---

### Post by Ren McCourtey on 2007-02-13
Thanks for help, I got it working yesterday already with last CVS build from serialmonkey. This post is much more cry for banishing ralink's card from Linux community than cry for help..:-) But thanks anyway, I'll keep your link for future reference. You last sentence, it's very accurate..And I need plenty of linux then..:-)

---

