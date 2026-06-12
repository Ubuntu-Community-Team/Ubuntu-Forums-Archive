---
title: "Upgrading to Koala wirelessly"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by brodiesel on 2010-02-02
hey all, i have a question thats got me rather confused.

currently i have a dual boot xp/intrepid system. the problem is that intrepid, when i installed it, had a bug in the wireless that affected very few laptops, but mine was one. so after months of trying to fix it (without access to a wired connection), i gave up.

i would now like to try upgrading to koala. the problem is that i still dont have a wired connection. should i try to erase the whole partition and reinstall from scratch? if so, how does one go about erasing the data on the partition while leaving it primed for installing a new version?

any help is appreciated.

---

### Post by ushills on 2010-02-02
If you chose to re-install the installer will guide you through clearing  and formatting the partition for you, no preperation is required.

I would check the live CD first though to check your wireless card is supported now.

---

### Post by ushills on 2010-02-02
You could also enable modules-backports as this will have the latest available wireless drivers.

---

### Post by samantha_ on 2010-02-02
> **brodiesel said:**
> hey all, i have a question thats got me rather confused.

currently i have a dual boot xp/intrepid system. the problem is that intrepid, when i installed it, had a bug in the wireless that affected very few laptops, but mine was one. so after months of trying to fix it (without access to a wired connection), i gave up.

i would now like to try upgrading to koala. the problem is that i still dont have a wired connection. should i try to erase the whole partition and reinstall from scratch? if so, how does one go about erasing the data on the partition while leaving it primed for installing a new version?

any help is appreciated.

just download the new cd, then burn it.
Boot up the new cd, and go to System -> Administration -> Gparted
Delete both the swap and the linux ext3 partition.
When using the ubuntu installer, use the option "use largest contineous block of free space"

Or you could simply use the format option in the Livecd, both really have the same effect...

---

### Post by brodiesel on 2010-02-02
i cant see to find any documentation about what cards are supported. can you explain that last part?

---

### Post by samantha_ on 2010-02-02
check if its in here
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by brodiesel on 2010-02-02
wow thats a difficult page to understand, but thanks for posting that, samantha. i've searched and not found my device (atheros AR5005g) on the list. i'm unclear if that means that it is not supported or if its just that no one has added it to the list. i spose i might try a live disc and just give it a go. 
if its not supported, any ideas for making it work? or is it better to just go back to hardy (which worked).

---

