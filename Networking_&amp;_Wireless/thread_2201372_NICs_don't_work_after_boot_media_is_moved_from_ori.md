---
title: "NICs don't work after boot media is moved from original machine to identical"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by hantechbl on 2014-01-24
Hello,

So I have several 1U servers, and they are configured to boot off of USB drives, so instead of setting each one and moving the CD drive around, I just set all of the USBs up using 1 machine.  However as soon as I put the flash drive in the final computer, it does not connect, it boots fine, but ifconfig only puts up lo.  I remember when I previously used CloneZilla it said something about removing a MAC address file or something like that?  If that could cause issues, how would I go about correcting it?

Thanks

---

### Post by varunendra on 2014-01-26
What do these show -
```
sudo lshw -numeric -C network
cat /etc/udev/rules.d/70-persistent-net.rules
```

And just curious, what is the role of USB in booting if the OS resides on internal drives of these servers? Is it just for holding Grub or something more advanced?

---

