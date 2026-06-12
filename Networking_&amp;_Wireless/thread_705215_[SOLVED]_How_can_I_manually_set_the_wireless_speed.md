---
title: "[SOLVED] How can I manually set the wireless speed to 54Mb/s to get the right speed"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by holihue on 2008-02-23
I have a intel 3945ABG wireless card, and everything looks like it is working.


Yesterday I set up a accsesspoint in my house (on side of my house).
And when I sit next to it I have a quality on 80%, and I restart my pc and connect.
Now the connection speed is on 54Mb/s (from when I right click on nm-applet and click Connection Information)
I run a speedtest (at speedtest.net) and get 10000 Kb/s down and 9842 Kb/s up.
And then I walk (with my laptop) to my workplace (on the other side of my house) and on the connection speed it is still 54 Mb/s
I run the same speedtest, and I get the same resault.
I can now browse without a problem.


But, when I restart my pc (on my workplace, on the other side of my house from the accesspoint) (the quality is around 50%) after connecting to the accesspoint, the speed in Connection Information shows me 24Mb/s.
And when I run the speedtest I get only ca. 1000Kb/s down and ca. 3000Kb/s up.


How can I set the speed to 54Mb/s when I connect to my accesspoint from my workspace.
I think that is the problem.


EDIT:

```
sudo iwconfig eth1 rate 54M
``` 
did the job.

---

