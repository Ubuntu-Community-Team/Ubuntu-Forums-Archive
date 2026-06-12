---
title: "how do i set up wireless with a belkin card"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by gnixon70 on 2006-07-21
Hello group:

I am fairly new to linux and have decided to install ubuntu on my compaq presario 2100.  I have a belkin wireless g network pc card in my notebook with a model number of fsd7010 version 4000.  My network uses a wep key(I know weak) and a mac filter which has already been preconfigured to accept my cards mac address.  will this work with ubuntu and if so, can someone explain or link me to a place where i can get step by step instructions on how to do this?  My knowledge of linux is not that great.  I know only the basic shell commands to get around the file system, and do minor things.

Thanks

Greg

---

### Post by spd106 on 2006-07-21
This is tricky, if your card is based on a broadcom chipset then there are two ways.
1. BCM43xx - included in Dapper, but you need to extract the firmware from your windows driver.  

2. NDISwrapper - simpler to setup, but is still a bit of a hack. Doesn't work well with other utilities ie Network-Manager.

Here is a good place to start [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

Make sure you check which kind of chipset it has. Some models have Ralink instead.

---

### Post by gnixon70 on 2006-07-21
Yes, I've looked at some of this as well as some other things.  It sounds like you have to convert a windows driver to a linux driver using an application that has to be compiled.  I've heard this will work spotty at best.  Actually what i'm leaning toward now is just purchasing a wireless card that works 100% with ubuntu out of the box and ebaying my belken off.  Any ideas what the best card would be in the say 30-50 dollar range?  I want to stay away from a usb card as it would not be a good thing with the way i work with my laptop and the position of the usb ports.

Thanks

Greg

---

