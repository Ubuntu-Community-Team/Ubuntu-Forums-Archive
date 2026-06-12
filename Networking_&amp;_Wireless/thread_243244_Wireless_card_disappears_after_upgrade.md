---
title: "Wireless card disappears after upgrade"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by redpants on 2006-08-24
Hi, I'm totally new to ubuntu and almost totally new to linux in general.

I managed to install ubuntu with pretty much no problems whatsoever, but then I decided to run all the available updates indicated by the icon in the top bar.  Everything went fine, with one exception...before the upgrade my wireless card worked fine, afterwards, the wireless connection disappeared from my network settings.  Now all that is there is my Ethernet connection and my modem connection.

I didn't figure it would help, but I tried switching to the 686 kernel because I read that it was better for modern CPU support, but it didn't make any difference.

Like I said, I'm totally new to this, so I don't even know where to start...could someone give me some dummy instructions as to what to try?

I'm running a Dell Inspiron 6400 with Intel Pro Wireless card.   Core Duo T2300E Processor, 1GB RAM, 100GB HDD.  Dual booting Ubuntu 6.06 LTS and Windows Media Center Edition.

---

### Post by SFDD on 2006-08-24
Same thing basically happened to me, though I'm on a Dell Inspiron 8500 that uses a TrueMobile 1300 card. So, perhaps it's nothing specific to our cards. I'm hoping there's an easy way to tell Ubunutu to "start over" with regard to going back to the state in which it could find the cards. but so far, no one has replied to my post either.

EDIT: I just uninstalled ndiswrapper, rebooted, and now the card is visible again. Go figya. ;)

---

### Post by redpants on 2006-08-24
:( Just tried your fix...no joy.  I read the help files about adding a network device but the networking interface is a different version apparently...the version in the help files says there is an "add" button for connections, but I don't have that on mine.

---

### Post by redpants on 2006-08-25
I decided to boot into my original 386 kernel and just see what would happen and, go figure, the wireless card is there and works fine.  So why would booting to a different kernel have anything to do with whether or not my card is recognized?

---

### Post by jlsheehan on 2006-09-08
I have the identical problem.  I have a Dell Inspiron 6400 with Intel Centrino dual core.

When I boot the 686 SMP kernel I have 2 processors but the wireless device disappears, switch back to the 386 and I have a wireless device again.

Any gurus know the answer to this one?

Jeff

---

### Post by jlsheehan on 2006-09-08
Ok, the answer was: installing the linux-restriced-modules-686 makes all the pain go away. :)

Jeff

---

