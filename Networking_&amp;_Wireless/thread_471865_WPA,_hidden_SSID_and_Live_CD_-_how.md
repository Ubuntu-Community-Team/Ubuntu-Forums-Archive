---
title: "WPA, hidden SSID and Live CD - how?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by tiger's on 2007-06-12
Hello, team!

I've read a lot of docs about how to start WPA with hidden SSID, but I can't restart PC to remove "eth1" interface or some drivers because I run it from LiveCD and I don't have a place to store startup config (if it's possible, I don't know :) ). 

So, I've 6 distrs: Ubuntu DVD 6.06.01 LTS, Xubuntu 6.06.01, Kubuntu 6.06.01, and all of them 7.04.

My AP have hidden SSID and WPA1/WPA2 PSK support. 

Please, can you explain me, how I can start WiFi from LiveCD?

Thank you!

---

### Post by stchman on 2007-06-12
> **tiger's said:**
> Hello, team!

I've read a lot of docs about how to start WPA with hidden SSID, but I can't restart PC to remove "eth1" interface or some drivers because I run it from LiveCD and I don't have a place to store startup config (if it's possible, I don't know :) ). 

So, I've 6 distrs: Ubuntu DVD 6.06.01 LTS, Xubuntu 6.06.01, Kubuntu 6.06.01, and all of them 7.04.

My AP have hidden SSID and WPA1/WPA2 PSK support. 

Please, can you explain me, how I can start WiFi from LiveCD?

Thank you!

Hidden SSID is overrated.  You have WPA2 encryption, I would also institute MAC filtering.  THose two should be more than enough security.

---

### Post by wieman01 on 2007-06-13
> **stchman said:**
> Hidden SSID is overrated.
So is MAC filtering. :-) Adds no extra security at all as MAC addresses are easily cloned ("ifconfig hw addr"). 

The standard networking applet will do. Boot from Live CD (possibly Feisty), then right click on the networking applet and configure your network. You will have to do this every time you boot your computer, because as you have pointed out the Live CD does not permanently store any sort of data.

---

### Post by tiger's on 2007-06-13
> **wieman01 said:**
> The standard networking applet will do. Boot from Live CD (possibly Feisty), then right click on the networking applet and configure your network. You will have to do this every time you boot your computer, because as you have pointed out the Live CD does not permanently store any sort of data.

It was the first thing I did - I've right clicked on network applet. But it does not work. Sorry.

---

### Post by wieman01 on 2007-06-13
> **tiger's said:**
> It was the first thing I did - I've right clicked on network applet. But it does not work. Sorry.
What does not work? You don't have the WPA option? What card have you got then?

---

### Post by tiger's on 2007-06-16
> **wieman01 said:**
> What does not work? You don't have the WPA option? What card have you got then?

Yep, I don't have WPA option in Ubuntu and Xubuntu. WPA option in Kubuntu does not work with hidden SSID. And later I'd a chance to make sure that it does not work with not-hidden SSID too :-). I've got 2 laptops: one with Intel 2200 wireless card, other with some TexasInstruments wireless. Both seen as "eth1" ifaces and reports on *iwlist scan* command. 

Anyway, thanks for your answer :-) Right now I'm looking forward to install Fedora 7 to try. But I like Ubuntu for... I don't know what for, but I like it. I've got a home LAMP server on Ubuntu. It's a pity, that there are so many users, that has not success in wireless with Ubuntu (regarding that and some other forums). I'm sure, that if I spent 2-3 full days for reading forums and if reinstall distr 2-3 times, I would get functioning WiFi, but I don't have enough time and may be enough desire for that. 7-8 years ago there was the same situation with sound and video. Same situation, now and before MS is one step forward with compatibility.

---

