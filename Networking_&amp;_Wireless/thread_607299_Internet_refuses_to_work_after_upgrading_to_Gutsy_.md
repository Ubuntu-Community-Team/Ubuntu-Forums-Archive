---
title: "Internet refuses to work after upgrading to Gutsy even though WICD says I'm connected"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2007-11-08
I don't know what to do. Gutsy is supposed to have less wireless problems not more. But I just upgraded my desktop two days ago and was only able to get internet working twice for like no more than 30 minutes after hours and hours of trying.

WICD says I'm connected. "iwconfig" says I'm connected. Both even give me the signal strengths. But my browsers, instant messaging, IRC clients ... NOTHING is actually connected. I refresh WICD, disconnect and reconnect. I restart my computer. I use "sudo /etc/init.d/networking restart" to restart my wireless, but it doesn't work. And it's frustrating. My desktop uses a TEW-424UB wireless card and the signal strength is sometimes really low, but still goes up to about 40% at times which has proved to be sufficient with Feisty. I have a laptop that works fine with the same wireless network.

I must be missing something. Just what is it? What can I do? Please just anything. This is really frustrating.

---

### Post by mpierce on 2007-11-08
When I upgraded, Gutsy mangled my wireless setting. Look in /etc/network/interfaces to see if the info is there. You should have how its managed, essid and of course your WEP key.

Hope this helps...

---

### Post by mahasmb on 2007-11-08
It's not helping. All I have in that file are:

auto eth0
autho eth1
auto wlan0

wlan0 is my wireless connection.

---

### Post by mpierce on 2007-11-08
Do a search on posts under my name as I described this in detail. 

AND, eth1 is the your wireless card. 

You'll uncomment out wlan0.

---

### Post by mahasmb on 2007-11-08
My wireless card definitely uses wlan0 though... and I use WPA encryption. It won't work with your setup.

---

