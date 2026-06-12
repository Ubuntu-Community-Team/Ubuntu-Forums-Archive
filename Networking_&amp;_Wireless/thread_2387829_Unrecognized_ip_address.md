---
title: "Unrecognized ip address"
date: 2018-03-24
forum: Networking &amp; Wireless
---

### Post by offir on 2018-03-24
I wrote this command to identify the address of a device connected to my network
```
sudo netdiscover -S -f -i enp3s0
```
I found the address

But it found something else (For some reason when I do a copy and paste from the terminal out here it's not good - So I've included a picture)
Both televisions show ip 0.0.0.0
And the last address is what's strange
I do not know where it came from

It does not make any network problem
But I want to know where that address comes from

---

### Post by SeijiSensei on 2018-03-24
Maybe they just have active network interfaces but no IP address assigned?

Do they show up if you run "arp -a" from a connected Ubuntu host?

---

### Post by offir on 2018-03-24
> Do they show up if you run "arp -a" from a connected Ubuntu host
yes they show up


I'm more interested in what the last address is ?  10.36.187.2   (Television address is not problematic)

---

