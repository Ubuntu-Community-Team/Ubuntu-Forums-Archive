---
title: "can only connect to G networks"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by skydiver|goose on 2008-03-14
I have a BCM4306 wireless built into my Pavilion ZV5000 laptop.

I use wifiradar to connect to wireless networks.

I messed around with my wireless card to be able to use aircrack-ng, and now I can only connect to G-only networks in Ubuntu. So when I go to a coffee shop that has a B/G Network, have to boot in windows instead of Ubuntu to connect to it.

Does anyone know how I can fix this?

---

### Post by kevdog on 2008-03-14
Have you tried doing this:

sudo iwconfig wlan0 rate auto

---

### Post by skydiver|goose on 2008-03-14
no, but I'm gonna have to restart and load Ubuntu to try this.

---

### Post by kevdog on 2008-03-14
If that doesnt work try this:
sudo iwconfig wlan0 rate 11M

Assuming your wireless device is wlan0 (substitute whatever is appropriate)

---

### Post by skydiver|goose on 2008-03-14
didn't work. what else can I try?

---

