---
title: "Wireless on Acer Ferrari 4000"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by robintw on 2008-10-25
Hi,

I've been browsing round the internet for ages trying to sort the wireless on my Acer Ferrari 4000. I have quite a bit of experience with Gentoo Linux, and actually thought that Ubuntu would automatically configure my wireless for me - but it doesn't seem to have.

Basically I can't get any lists of wireless networks from Network Manager. iwconfig lists an interface wlan0 that exists, but iwlist scan wlan0 doesn't give any results.

When running lsmod I have found that both ndiswrapper and b43 are loaded - should this be the case?

I think the problem may be that my wireless isn't switched on (Acer's seem to have some kind of soft-switch which turns wireless on and off) but I can't find out how to switch it on. Pressing the switch doesn't give any messages in dmesg, and doesn't seem to change anything anywhere. Looking on the internet there are a lot of references to acer_acpi, but that seems to be discontinued now in favour of acer_wmi - but I can't seem to get that to work either.

Any ideas anyone? As I said - I think most things might be working apart from actually switching the wireless on!

Cheers,

Robin

---

### Post by senorcool on 2009-02-27
I had your same problem and looked through the Internet. I found all these complicated methods to solve it and none of them worked. Actually, all you have to is just install the driver: Connect to the internet with an ethernet cable and install the wireless card by going System->Administration->Hardware Drivers-> Activate your card.

---

### Post by lucaD on 2009-03-05
Thank you very much, senorcool! Helped me alot! [right][[color=#FFFFFF]_ferrari 355_[/color]](ferrari-355.com)[/right]

---

