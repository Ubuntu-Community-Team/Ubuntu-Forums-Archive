---
title: "netgear wg511 monitor mode problem"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by cheese__monkey on 2007-06-08
Hi,

I can't seem to get this card to go into monitor mode on Feisty 7.04. It works fine on Knoppix 5.

Here's what I do :-

```
ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

```

Bringing the card up again results in "SIOCSIFFLAGS: Operation not permitted".

As far as I know the card is using the prism54pci driver. 

Any ideas? I'm not that familiar with Linux generally so please be gentle...

---

### Post by chili555 on 2007-06-08
Please try this sequence:```
sudo iwconfig wlan0 mode monitor
sudo iwconfig wlan0 mode managed
```Please post back and let the other prism54 fans know.

---

### Post by cheese__monkey on 2007-06-09
Sorry, I should have mentioned I was executing ifconfig, iwconfig as root before.

Doing this:
```
sudo iwconfig wlan0 mode monitor
sudo iwconfig wlan0 mode managed
```

...doesn't work, "device or resource busy". If I ifconfig down the interface first, then iwconfig works, but then I can't ifconfig the device back up again.

Hunting around the forums this appears to be a problem with the new prism54pci driver introduced with Feisty. 

With a little help from a friend I have installed the Edgy kernel and monitor mode now works fine with the prism54 driver, so my immediate problem is solved as long as I don't use the newer kernel.

---

