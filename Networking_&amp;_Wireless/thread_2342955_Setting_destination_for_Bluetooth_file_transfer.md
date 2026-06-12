---
title: "Setting destination for Bluetooth file transfer?"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by eezacque on 2016-11-11
So, I am finally able to push files from my mobile through Bluetooth to my ubuntu box. However, although I checked 'Receive files in Downloads folder' on Personal File Sharing Prefs, the files land in ~/.cache/obexd.  Any clue?

---

### Post by jeremy31 on 2016-11-11
Try using Blueman ```
sudo apt-get install blueman
```
It will show in Dash as Bluetooth Manager and you should see a new icon in the notification area, right click and choose Local Services and then you should be able to change the location.
I have looked many times for the file where that info should be saved and come up with no results

---

### Post by eezacque on 2016-11-12
> **jeremy31 said:**
> Try using Blueman ```
sudo apt-get install blueman
```
It will show in Dash as Bluetooth Manager and you should see a new icon in the notification area, right click and choose Local Services and then you should be able to change the location.
I have looked many times for the file where that info should be saved and come up with no results

I don't think Blueman adds any functionality other than a fancy gui.
Anyways, like Personal File Sharing, Blueman allows me to select a destination, which is ignored.

---

