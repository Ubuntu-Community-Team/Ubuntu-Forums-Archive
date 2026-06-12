---
title: "Discovering ip connections for a traceroute"
date: 2021-03-22
forum: Networking &amp; Wireless
---

### Post by joaocrespo on 2021-03-22
Hello World.

This might look like a weird question (networks are not my specialty).

I´m having troubles with high ping playing CS:GO, and so i´&#7743; trying (trying is the keyword) to do a traceroute so my ISP can try to fix it.

Well for running traceroute I need an IP, and after googling a while i discovered i can get the server IP by running the command status in the game console, which gets me something like this:

Connected to =[A:1:1986619394:16851]:0
hostname: Valve CS:GO Spain Server (srcds062.195.14)

After googling a bit more ([https://gaming.stackexchange.com/questions/376199/unable-to-get-the-server-ip-address-via-csgo-status-command-in-linux](https://gaming.stackexchange.com/questions/376199/unable-to-get-the-server-ip-address-via-csgo-status-command-in-linux)) I discovered that Valve deliberate hides the IP (for security reasons it seems).

My guess is well the server still needs to to send/receive info to me during gameplay, so my computer must KNOW the server real IP at some point (the same principle behind why DRM does not work), so is there a way to know to which IP´s i´m send/receiving data at a certain time???

Thanks in advance.

---

### Post by The Cog on 2021-03-22
This command will list all your current connections:
```
ss -ntp
```

---

### Post by joaocrespo on 2021-03-22
That worked.

Thanks for the tip :)

---

