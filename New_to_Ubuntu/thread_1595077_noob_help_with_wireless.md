---
title: "noob help with wireless"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Nicgou on 2010-10-12
im a brand new user with ubuntu and any linux based system.  i installed ubuntu 10.10 netbook on my hp mini 1000 netbook 2 days ago and have been having problems with connecting to the internet with both my ethernet and wireless...  it says that the firmware is missing for the wireless and when i go into terminal and find out the network information with "sudo lshw -C network"[FONT=Verdana] it says that it is disabled but my internet card is turned on.  thanks  for the help[/FONT]

---

### Post by ubudog on 2010-10-13
So, did you install any drivers yet or no?

---

### Post by PaulReaver on 2010-10-13
once you get your ethernet cable connection figured out, go into synaptic and install 'broadcom-sta-common'

I think that's the driver for broadcom wifi cards

---

### Post by anewguy on 2010-10-13
How about you post the output of the below back here so we know for sure what adapter you have?

lspci

lsusb

lshw -C network

ifconfig

iwconfig


Dave ;)

---

### Post by ubudog on 2010-10-13
> **PaulReaver said:**
> once you get your ethernet cable connection figured out, go into synaptic and install 'broadcom-sta-common'

I think that's the driver for broadcom wifi cards

That, or in System>Admin>Restricted Drivers, or did you already try that?

---

