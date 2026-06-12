---
title: "I need detailed instrcutions to set up my Linksys WMP54G PCI adapter."
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by ungeek on 2008-07-02
My Aunt recently downloaded Ubuntu (the kind with gnome) to my computer. I have a Linksys WMP54G wireless PCI adapter that I've been trying to connect. I have never used anything other than Windows before and am not very tech savvy. I can however, follow directions very well. I would be very grateful if someone could give me step-by-step instructions to set up my card. If you need me to try to clarify my problem, just ask.

The internet is not conected to the computer with Ubuntu.
The card has been mounted in the computer.

---

### Post by ungeek on 2008-07-02
Even if all you do is give me a link you think may help, I'd be happy...

---

### Post by ungeek on 2008-07-02
Please help!!!

---

### Post by ungeek on 2008-07-02
I'd like to actually be able to experience ubuntu....but I can't do that without the internet... :[

---

### Post by ungeek on 2008-07-02
[-o< I'm only a kid! I need help!!!!

---

### Post by chili555 on 2008-07-03
Well, I'm older than your grandpa, so maybe we can make a good combination! As you can see here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) there are several versions of this card, all with different chipsets. Let's ask the computer which one you have. Open a terminal (Applications-Accessories-Terminal) and type:```
sudo lshw -C network
```After thinking a bit, the terminal will tell you about your network devices; skip the ethernet device and look at the chipset for the wireless device. The link I referred you to will give you clues as to how to proceed, but post back if you need a little more detailed help.

---

