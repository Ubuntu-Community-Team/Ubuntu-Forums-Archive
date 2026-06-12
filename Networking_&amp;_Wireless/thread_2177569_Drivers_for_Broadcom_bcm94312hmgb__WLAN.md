---
title: "Drivers for Broadcom bcm94312hmgb  WLAN"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by m7il on 2013-09-29
I'm new to linux.
I have HP mini - 210-1085TU it has a Broadcom bcm94312hmgb  WLAN. I just installed Ubuntu 13.04 on it. I have not been able to connect to my wifi router wirelessly, ethernet cable doesn't seem to be working either. The only way i seem to be able to connect to the internet is to use a wireless 3g internet usb dongle. Can anyone tell me where i can get the drivers for my WLAN card and how to install them. I would like to download them from another laptop using windows, upload the drivers onto a pendrive and then download them from the pendrive onto ubuntu. 
Thank for all your help.

---

### Post by varunendra on 2013-10-02
> **m7il said:**
> ....it has a Broadcom **bcm94312hmgb**  WLAN....

Hello m7il, Welcome to the forums !

Sorry to see you didn't get any responses yet. Most probably because you seem to have mentioned the 'label' name of the card, which is not really the same as the actual model name. To give us the actual model name of the card/chip, please post back the output of -
```
lspci -nnk | grep -iA2 net
```

---

