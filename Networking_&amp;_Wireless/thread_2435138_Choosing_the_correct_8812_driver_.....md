---
title: "Choosing the correct 8812 driver ...."
date: 2020-01-16
forum: Networking &amp; Wireless
---

### Post by bobsuncle on 2020-01-16
There are quite a few smart people on this website.  Unfortunately I am not one of them. :p;)  I have one of the myriad of USB WiFi devices that are based upon the 8812 RealTek chip.  I quickly discovered that I would need a kernel module to make it function.  Here are some of the options that I have been able to find ...

```
apt install rtl8812au-dkms package
```

Pro:  Part of the official Ubuntu repository.
Con:  Looks to be based upon a 2014 version of the driver.  It may or may not work on your device.  It does not work with mine.

```
https://github.com/aircrack-ng/rtl8812au
```

Pro:  Often recommended on this and other websites, most recently by one of the forum moderators earlier today.  Seems to be a rather active repository and is currently being maintained.
Con:  Brought to you by the same folks that develop tools to crack WiFi networks.

```
https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
```

Pro:  Seems to work well and is based upon a more recent version of the driver from RealTek.
Con:  The author puts this *Fair Warning* statement on his driver:[INDENT]> I found the original source for this driver on Dropbox linked by the seller on an Amazon listing.   Don't you love how reputable these driver bundles are?  Nothing say  "no one tampered with this after it left the OEM" like downloading from  Dropbox / Baidu / etc.Hard to argue with his logic.:neutral:[/INDENT]

```
https://github.com/gordboy/rtl8812au
```

Pro:  Seems to work well.
Con:  Not maintained as often.  There are newer updates available.




> &#8220;But choose wisely, for while the true Grail will bring you life, the false Grail will take it from you.&#8221;&#8211;Grail Knight from *The Last Crusade*
YMMV

---

