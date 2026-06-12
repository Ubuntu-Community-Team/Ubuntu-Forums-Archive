---
title: "SD card issue"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Blue Sassley on 2009-05-25
I'm having issues with a new 16GB SDHC card on my Dell Mini 9. When I run the dmesg | tail command I see the following after inserting the card:

```
mmc0: error -84 whilst initialising SD card
```

Blue

---

### Post by Blue Sassley on 2009-05-28
Bump

---

### Post by Blue Sassley on 2009-05-30
Bump again

---

### Post by rustutzman on 2009-05-30
Have you tested the card elsewhere or tried any other cards in the reader?

---

### Post by Blue Sassley on 2009-05-30
I have tested the card reader with smaller SD cards and I have also tested the 16GB card in another laptop.

Thanks,
Blue

---

### Post by 73ckn797 on 2009-05-31
Can the computer read the SDHC card? Could be that the SDHC is too new to work. May want to find a USB adapter that would be for SDHC cards. I have the same issue but have not bothered with figuring it out yet. My Laptop will not read SDHC cards.

---

### Post by Blue Sassley on 2009-05-31
Well I just did some more testing and made a LiveCD USB flash drive of 8.04.2 Desktop and booted it and on the LiveCD I can see the 16GB SDHC card, so I guess my next test will be to grab 9.04 NBR again and make a LiveCD USB drive and see if it shows in that.

Blue

---

### Post by Blue Sassley on 2009-05-31
Well I just finished making and booting into 9.04 Desktop on a LiveCD USB and the SDHC card has gone missing so its something changed between 8.04.2 and 9.04.

Blue

---

### Post by ronacc on 2009-05-31
it could be that that particular card is a little marginal for some reason , on my eeepc 4g I have noticed a large varience in speed between cards of suposedly the same class and have a couple that get an unsatisfactory amount of errors , it dosen't seem to be related to brand but to the individual card .

---

