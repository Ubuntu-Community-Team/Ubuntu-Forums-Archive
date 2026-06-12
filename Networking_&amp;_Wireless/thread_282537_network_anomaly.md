---
title: "network anomaly"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by HadroLepton on 2006-10-22
i have a problem with my network controller. i have had no luck searching for this problem in google or elsewhere because i don't know what terms to search for. i have attached a screenshot of system monitor showing the anomaly.

i will try to explain the problem.
the network throughput will drop to 0 every second. please take a look at the screenshot. every spike there is about 1 second. the screenshot shows a download process, during an upload the purple line goes zigzag.

i am using ubuntu 6.06 on an ibm thinkpad r50. i am using the builtin network controller. this behaviour only appears when using the wired network but not when using wlan. it does not matter where the traffic comes/goes to, internet or local network, samba or nfs, builtin harddisk or usb harddisk. no other machine in my local network has this problem, as far a i can tell. i have also tried using another cable.

during network activity everything seems to be in order, no process with 100% cpu, no process which hogs all the memory, no harddisk thrashing. the network also does not seem unbearably slow.

any suggestions? please help.

---

### Post by spd106 on 2006-10-23
What happens when you change the update interval?

---

### Post by HadroLepton on 2006-10-23
it doesn't do much difference.
default interval is at 1 second.
setting interval to 0.25 seconds will cause the spikes to be further apart.
setting interval to 2 seconds will cause the spikes to be averaged to a lower almost flat line.

i do not think the problem is in the interval setting. the system monitor is just a measurement tool.

---

### Post by HadroLepton on 2006-11-07
bump. anyone any idea?

---

