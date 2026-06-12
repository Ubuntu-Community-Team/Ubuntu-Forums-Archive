---
title: "internet connection problem"
date: 2016-04-10
forum: Networking &amp; Wireless
---

### Post by samir8 on 2016-04-10
hi there 
i am using Ubunto 14.04 on HP notebook 15-r107ne
i've been having a problem with my internet connection via wifi 
problem isn't with router as others devices seem to work well ,and the wifi connection icon on my top panel shows no problem at all, 
restarting my laptop helps but only for a few minutes then i lose connection again and restart again, 
been searching for a solution for hours but still couldn't solve it 
i really like using ubunto but this is really annyoing i hope you guys can help me , please keep in mind i am new to ubunto so go easy on me x.x

---

### Post by Hadaka on 2016-04-10
Hi please copy paste then post the output of..
```
lspci -n | grep 0280
lsmod | grep 80211
```
thanks.

---

### Post by samir8 on 2016-04-10
Wireless info
[ATTACH]268292[/ATTACH][ATTACH]268292[/ATTACH]

---

### Post by samir8 on 2016-04-10
lspci -n | grep 0280
0a:00.0 0280: 10ec:b723
lsmod | grep 80211
mac80211              720896  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              532480  2 mac80211,rtlwifi

---

### Post by Hadaka on 2016-04-10
Hi please try this link ..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
thanks.

---

### Post by samir8 on 2016-04-11
i'v tried it and it's looking good so far, thanks :)

---

### Post by Hadaka on 2016-04-11
Great ! glad that worked for you.
and thank you for marking your thread solved
it will help searchers.

---

