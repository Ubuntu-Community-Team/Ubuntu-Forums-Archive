---
title: "[WiFi] Setting outdoor/indoor environment only for AP"
date: 2017-06-05
forum: Networking &amp; Wireless
---

### Post by vasko1992 on 2017-06-05
As the title suggests I want to be able to specify whether my device is operating indoor or outdoor. Some countries for example Germany have restrictions for outdoor usage:
```

country DE: DFS-ETSI

        (2400 - 2483 @ 40), (N/A, 20), (N/A)
        (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
        (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
        (5470 - 5725 @ 80), (N/A, 26), (0 ms), DFS
        (57240 - 65880 @ 2160), (N/A, 40), (N/A), NO-OUTDOOR

```
However I can't figure out how to tell the kernel the device is going to operate outdoors. The only things I can think of are:
- To manually check and set only channels that are allowed outdoors via hostapd.
- To edit the regulatory.bin file, removing the channels that are disabled outdoors.

Is there a better way?

---

### Post by him610 on 2017-06-06
Hello vasko1992, and welcome to the forum.

I believe that applies to the frequency of your wireless router, for instance if want to have wireless communications indoors and outdoors in Deutschland, on your router select (2400 - 2483 @ 40), or (5470 - 5725 @ 80)

If you want a more detailed explanation, try [https://wireless.wiki.kernel.org/en/users/Documentation/iw]("https://wireless.wiki.kernel.org/en/users/Documentation/iw")

---

