---
title: "Netgear WG511v3"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by alastair lewis on 2005-05-25
Cross posted from Warty fourm.
I was getting nowhere with Ndiswrapper and a Netgear WG511v3 with Warty. Ndiswrapper -l  returned 'hardware present, fuzzy' & dmesg showed it was going to be a complete non-runner.


I upgraded to Hoary and reinstalled ndiswrapper and the .inf files. Now ndiswrapper -l shows that card and driver are installed (no recurrance of the fuzzy problem).

modprobe ndiswrapper does not return any errors
dmesg shows card and drivers are present and correct

BUT.. no lights come on on the card.

I have tried reinserting the card, deactivating eth0 (the 10/100 card) and rebooting with neither card in and then inserting the wifi card. No lights with any of these and iwconfig gives card NOT READY in the first line.

I have not or disabled anything (eg. prism54) because I don't know how, or installed the kernal headers.

Loving linux (Ubuntu in particular) but still at the bottom end of the learning curve. I would dearly like to crack this.

Have I missed a key step.

---

### Post by ssam on 2005-05-25
have you tried the card with out using ndiswrapper? i have the V2.0 and it works ok. there was just an issue with the via epia bios that made it take a little work (see [http://www.ubuntulinux.org/wiki/NetgearWG511AndViaEpiaMIIHowto)](http://www.ubuntulinux.org/wiki/NetgearWG511AndViaEpiaMIIHowto)).

sam

---

### Post by alastair lewis on 2005-05-25
The v3 (Made in China card)  is a stripped down vesrion of the v2 card and will not work with the prism54 drivers included in recent kernals.

According to various fora and the ndiswrapper site, this card will only work with ndiswrapper.

---

