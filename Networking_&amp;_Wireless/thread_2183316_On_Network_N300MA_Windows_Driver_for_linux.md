---
title: "On Network N300MA Windows Driver for linux?"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by sean-hall412 on 2013-10-24
Hey,

I recently installed the latest version of Ubuntu, I have installed it in the past and everything went well, Ubuntu installed a compatible driver that worked with my old network adapter. However, this time around it does not recognize the adapter at all. I've looked around the internet (google) but the only thing that I found was this: Ndisgtk & Reaktek drivers.

Any help would be extremely appreciated.

---

### Post by sean-hall412 on 2013-10-25
Shameful bump. Is there no way to get it to work?

---

### Post by chili555 on 2013-10-25
With the device inserted, please open the terminal and run:```
sudo modprobe r8712u
```Now let's check the message logs for clues:```
dmesg | grep rtl
```Post the results and we'll proceed.

---

