---
title: "no wireless"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by mett demon on 2010-04-07
Hi All;
I am a total noob to anything linux so don't quite grasp the hacking bit, yet. I have a Compaq 615 notebook which runs kubuntu fine with the exception of the wireless function. (same prob when I installed Ubuntu 9.10 and netbook remix) I don,t even get the option to set up a wireless network as it is greyed out. I have checked (left Click networkmanager) and wireless is enabled. Am I missing some drivers or similar???? if so I would appreciate anyones help in getting me to enjoy the wonders of kubuntu wirelessly.
Kind Regards

---

### Post by manoriax on 2010-04-07
As far as I know there are hardware drivers available for this card. Just click on System -> Administration -> Hardware Drivers.

In case there's nothing to selected, try this one:
Plug in a network cable, so that you are able to install packages from the Ubuntu repository.
```
sudo apt-get install linux-backports-modules-karmic
``````
sudo apt-get install b43-fwcutter
```Restart and try again to find a WLAN.

---

### Post by IndyGunFreak on 2010-04-07
> **manoriax said:**
> As far as I know there are hardware drivers available for this card. Just click on System -> Administration -> Hardware Drivers.

In case there's nothing to selected, try this one:
Plug in a network cable, so that you are able to install packages from the Ubuntu repository.
```
sudo apt-get install linux-backports-modules-karmic
``````
sudo apt-get install b43-fwcutter
```Restart and try again to find a WLAN.

Are you sure its a broadcom card?  It's very possible its a Ralink.

OP... Open a terminal and type "lspci" no quotes, hit enter, and post the output here..

IGF

---

