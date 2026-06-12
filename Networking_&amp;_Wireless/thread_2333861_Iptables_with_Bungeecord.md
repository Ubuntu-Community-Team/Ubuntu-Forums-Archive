---
title: "Iptables with Bungeecord"
date: 2016-08-13
forum: Networking &amp; Wireless
---

### Post by leethetech on 2016-08-13
[COLOR=#2C2C2C][FONT=&quot]So I have two bungees and want to allow connecting from each one to a single port. I cant put:[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]iptables -I INPUT ! -s $BUNGEE_IP -p tcp --dport $SERVER_PORT -j DROP two times with each IP because one overrides the other. Any ideas?

For people who don't know what bungee is: [/FONT][/COLOR]https://www.spigotmc.org/threads/1-8-1-10-bungeecord.392/

---

