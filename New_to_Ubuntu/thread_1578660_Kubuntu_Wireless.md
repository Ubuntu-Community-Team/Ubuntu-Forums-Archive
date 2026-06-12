---
title: "Kubuntu Wireless"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Sevenupkid on 2010-09-20
Hello, im a total N00b at linux right now and I need a little help. I have Kubuntu running off a CD on my laptop right now. I wanted to run it to make sure everything was compatible and stuff before I fully installed. I have an HP Pavilion ze4300 notebook and everything works fine. The wired internet works great, the wireless is a different story. I have plugged both in at the same time and it loads webpages but when i unplug the ethernet cord webpages fail to load. I have a link sys wireless g network adapter. I plug it in and it dosent work, nothing comes up or anything. When i go to System Settings - Network Connections there is a tab for wired and wireless lit up. I can click on ether one but no network shows up. When I unplug the adapter, the wireless tab goes away. This makes me think that i have to enable something or install drivers. Could i get some advice on what to do?

Thanks

PS The adapter indicates that it has established a link with my router, and flashes intermittently.

---

### Post by sandyd on 2010-09-20
> **Sevenupkid said:**
> Hello, im a total N00b at linux right now and I need a little help. I have Kubuntu running off a CD on my laptop right now. I wanted to run it to make sure everything was compatible and stuff before I fully installed. I have an HP Pavilion ze4300 notebook and everything works fine. The wired internet works great, the wireless is a different story. I have plugged both in at the same time and it loads webpages but when i unplug the ethernet cord webpages fail to load. I have a link sys wireless g network adapter. I plug it in and it dosent work, nothing comes up or anything. When i go to System Settings - Network Connections there is a tab for wired and wireless lit up. I can click on ether one but no network shows up. When I unplug the adapter, the wireless tab goes away. This makes me think that i have to enable something or install drivers. Could i get some advice on what to do?

Thanks

PS The adapter indicates that it has established a link with my router, and flashes intermittently.
post the output of
```

sudo ifconfig eth1 up
sudo ifconfig wlan0 up
sudo iwlist scan

```

---

### Post by Sevenupkid on 2010-09-20
sorry, where do i type that? is it in the run command thing or do i have to go someplace?

---

### Post by sandyd on 2010-09-20
> **Sevenupkid said:**
> sorry, where do i type that? is it in the run command thing or do i have to go someplace?
press alt + f2
type in "konsole"

---

### Post by Sevenupkid on 2010-09-20
For some reason its not working. i hit the keys and nothing happens. is there an alternate way?

---

### Post by sandyd on 2010-09-20
> **Sevenupkid said:**
> For some reason its not working. i hit the keys and nothing happens. is there an alternate way?
sorry for my legendary typos....

---

### Post by Sevenupkid on 2010-09-22
Sorry this took a while, school's a bitch.

sudi ifconfig eth1 up = eth1: ERROR while gettign interface flags: No such device.

sudo ifconfig wlan0 = nothing, just let me type another command. i did it twice because nothing happend...

sudo iwlist scan = lo interface dosent support scanning. 

eth0 interface dosent support scanning.

wlan scan completed:
Cell 01- Adress: 00:25:9c:28:76:bb
Channel 6
Frenquincy 2.37 GHz (channel 6)
Quaility=70/70 Signal level=- 28 dBm

and so on, i dont think you need the rest of that, just stuff about my network as far as i can see.

---

