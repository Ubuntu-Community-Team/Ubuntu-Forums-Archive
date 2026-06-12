---
title: "Gnome network manager problems"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by jbaerbock on 2007-06-18
I have used Mint (basicaly ubuntu) for around a month now and loved it. However recenlty I went over to PCLinuxOS 2007. Only one reason for it, for some reason it can detect my wireless networks around me (that have very low signals) and connect to them everytime. Mint's default monitor in Gnome only sometimes sees some of them and when it does and I click to connect it sits there trying and maybe 1/100 tries it finaly connects, same thing happens in Ubuntu (same network manager). My thought was the default network monitor sucks, PCLinux has its own set of tools. Any ideas on what other programs I can try out for Mint to get wireless connecting up to par? I'd prefer them to be full .mint or .deb or easily installable without an internet connection.

---

### Post by jimrz on 2007-06-18
> **jbaerbock said:**
> I have used Mint (basicaly ubuntu) for around a month now and loved it. However recenlty I went over to PCLinuxOS 2007. Only one reason for it, for some reason it can detect my wireless networks around me (that have very low signals) and connect to them everytime. Mint's default monitor in Gnome only sometimes sees some of them and when it does and I click to connect it sits there trying and maybe 1/100 tries it finaly connects, same thing happens in Ubuntu (same network manager). My thought was the default network monitor sucks, PCLinux has its own set of tools. Any ideas on what other programs I can try out for Mint to get wireless connecting up to par? I'd prefer them to be full .mint or .deb or easily installable without an internet connection.

you you might try wifi radar, available from synaptic in the universe repository

---

### Post by jbaerbock on 2007-06-18
Ok I'll give it a shot thanks!

---

### Post by jbaerbock on 2007-06-19
It kind of works better but both connections i think confuse the fact that there are two connections named linksys, one with encryption, and one without. I need to connect to the one without. On WiFi Radar it detects one then flashes between both, so still a flaky system, anyone know what is used in PCLinuxOS or another program or some settings I could change?

---

### Post by jimrz on 2007-06-19
> **jbaerbock said:**
> It kind of works better but both connections i think confuse the fact that there are two connections named linksys, one with encryption, and one without. I need to connect to the one without. On WiFi Radar it detects one then flashes between both, so still a flaky system, anyone know what is used in PCLinuxOS or another program or some settings I could change?

if you have access, why not simlpy go into the router and change your essid to someting other than "linksys' or any other AP that is in range? you may determine if that is, in fact, the issue and, if so, solve it in one move

---

### Post by jbaerbock on 2007-06-19
I would but this signal is a shared building wide signal, which I am not the admin of, there is someone else who has their own and also named theirs linksys, and they do have a key required, so wifi radar confuses them. Anything I can do in settings or terminal to correct it?

---

### Post by jimrz on 2007-06-20
> **jbaerbock said:**
> I would but this signal is a shared building wide signal, which I am not the admin of, there is someone else who has their own and also named theirs linksys, and they do have a key required, so wifi radar confuses them. Anything I can do in settings or terminal to correct it?

ooops...if you could find out who has the 2nd linksys, maybe ask them to change. no idea what you could change on your box to ease the issue. if there is a way to specify an AP as primary by mac address or something or than essid, i am not aware of it. might be worth some research.

---

### Post by jbaerbock on 2007-06-24
Well i know it works perfectly in PCLinusOS but that OS is very flaky on my system. Sadly I was forced to go back to windows XP for the time being because it works decently here too. So if someone could figure out how to put on Ubuntu whatever PCLOS uses for their network management I would love to switch back to linux since it is obviously so much better.

---

