---
title: "nmap - taking ages"
date: 2020-11-06
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2020-11-06
Folks,

Occasionally I'll use nmap to scan my network, normally it completes quite quickly but on occasions it'll take an eternity.

My latest scan was as follows;

nmap 192.168.1.0/24

if you press the return key before it completes you get progress info, I got the following;

```
Starting Nmap 7.60 ( https://nmap.org ) at 2020-11-06 12:41 GMT

Stats: 0:00:19 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 91.94% done; ETC: 12:41 (0:00:01 remaining)

Stats: 0:00:30 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 92.26% done; ETC: 12:41 (0:00:02 remaining)

Stats: 0:00:49 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 92.79% done; ETC: 12:42 (0:00:04 remaining)

Stats: 0:02:06 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 93.23% done; ETC: 12:43 (0:00:09 remaining)

Stats: 0:02:55 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 93.37% done; ETC: 12:44 (0:00:12 remaining)

Stats: 0:03:18 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 93.47% done; ETC: 12:44 (0:00:14 remaining)

Stats: 0:04:20 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 93.59% done; ETC: 12:46 (0:00:18 remaining)

Stats: 0:07:10 elapsed; 245 hosts completed (11 up), 11 undergoing Connect Scan
Connect Scan Timing: About 93.39% done; ETC: 12:49 (0:00:30 remaining)
```

After 19 seconds it suggests 1 second remaining,  this gradually increases.

Between checks at 4:20 and 7:10 the percentage completed has actually gone backwards.

What causes this?

Geoff

---

### Post by SeijiSensei on 2020-11-06
It's usually best to choose a scanning method. For simple checks to see if there are open ports with listeners, you can run a TCP scan with 
```
sudo nmap -sT 192.168.1.0/24
```
By default it runs a "stealth" scan which can take longer to complete.  See "[man nmap]("https://linux.die.net/man/1/nmap")" for details.

---

