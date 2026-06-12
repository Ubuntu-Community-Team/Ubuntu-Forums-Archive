---
title: "Wifi connected, can't access any sites"
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by felix42 on 2016-05-28
So... this is so frustrating.

I can use the Internet until it disconnects, like if i close the lid for a while or take my laptop for the day, and then it will give server not found errors upon reconnecting. Then it may take anywhere from an hour to a day to let me access sites again even tho wifi reconnects instantly. Switching ipv4 to Google dns worked once. Then once the wifi was disconnected, it ceased to work. Same with open dns. No other dns servers for ipv4 have since worked, however. Same with ignoring ipv6.  Worked once, not again. Same with forgetting the network. Manually shutting off interfaces (wlp2s0) also worked for about 15 seconds and then the same fix stopped working when repeated. It's like the problem is an AI adapting to my solutions.

All other devices connect fine. My laptop cannot even connect to the router. No pings work. Sites always stick on resolving host...

---

### Post by praseodym on 2016-05-28
Please run the wireless-script from the sticky thread and show the outputs. Does LAN work?

---

### Post by felix42 on 2016-05-28
Alright, I tried to run the wireless script (.txt) thing by copying it to my desktop with a USB, but it didn't even work. I followed the instructions provided to a T, but all it outputs is the title line: "WIRELESS INFO START" and says nothing underneath. I deleted/tried again, gave it a few minutes after hitting run, same result. Same result if I run it in the terminal. The terminal will appear for only a fraction of a second.

---

### Post by felix42 on 2016-05-28
Nevermind, I was able to get it to work (the script, not the wifi). Here are the results.

[http://pastebin.com/raw/6HzUHJCB](http://pastebin.com/raw/6HzUHJCB)

[ATTACH]269342[/ATTACH]

---

