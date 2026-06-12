---
title: "To install Realteck (?) wireless withoput progress"
date: 2021-04-24
forum: Networking &amp; Wireless
---

### Post by broadwaylion2 on 2021-04-24
I have installed this device countless times on Windows machines, but this is my first serious use of Linux. OK, the device has not loaded, I can understand, but where would I find it when and if I do get it loaded?
I am looking at Settings> Network> and find nothing about WiFi there. Will it appear if I get it to work, or will I look for it elsewhere?

I'd ask "How to Load It." but have already read what has been written on the forum without understanding it.
My plan is to ditch hard-wired connections at our facility and use exclusively WiFi Access Points.

Thanks, Elias (aka The Broadway LION)

---

### Post by morrownr on 2021-04-24
Elias,

Don't get frustrated. Let some of us that have been using Linux help you get to where you want to go. We can even have some fun getting there.

First, if you are using Realtek USB WiFi adapters, my guess based on what you said, then there is a lot of information for many Realtek drivers at this site:

[https://github.com/morrownr](https://github.com/morrownr)

To start helping, we need to know what chipset is in your adapter. A simple way to get this info is...

1. Press and hold the Ctrl and Alt keys, then press the "T" key. This will open a command line interface (or terminal if you prefer.)

2. Run the following in the terminal and post the results back here...

$ lsusb

A LOT of information about WiFi adapters is available at this site...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

