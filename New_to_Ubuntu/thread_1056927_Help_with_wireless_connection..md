---
title: "Help with wireless connection."
date: 2009-02-01
forum: New to Ubuntu
---

### Post by famous3warriors on 2009-02-01
I have a up notebook dv9205 and my os is ubuntu 8.10.  In my computer my blue light is on and it does state that I do have connection but when I try to surf the web I am unable to connect.  How can I fix this problem.  I am out of town and trying to connect to a free wifi spot and it is just not working.  Thanks for help in advance.  I really do appreciate your help.

---

### Post by ugm6hr on 2009-02-01
More detail would be useful...

See the Wifi help link in my signature below.

Also - has your wifi ever worked?

---

### Post by famous3warriors on 2009-02-01
The driver I installed is a broadcom b43 wireless driver.  Yes I did have this working at home.  This is the first time I tried to use it out of my house.  I also did a iwconfig and this is what I got 
lo no wireless extensions.
eth0 no wireless extentions.
wmaster. no wireless extension

Wlan0  IEEE 802.11bg. ESSID:"linksys"
             Mode:Managed.  Frequency:2.437 ghz. Access point:00:00:00:00:00:00
             Bit rate=54 mb/s. Tx- power=27dBm
             Retry min limit:7. Rts thr:off. Fragment. Thr=2352.  B
             Powermanagement=off
             Link quality=90/100.  Signal level:-19 dbm. Noise level= -69 dbm
             Rx invalid nwid:0   Rx invalid crypt:0    Rx invalid drag:0
             Tx excessive retries:0. Invalid mic:  missed beacon:0


I hope this helps.

---

### Post by ugm6hr on 2009-02-01
Do you have an IP?

Check with "ifconfig"

If yes - try pinging:
```
ping -c 3 www.google.com
ping -c 3 216.239.59.147
```

---

### Post by famous3warriors on 2009-02-01
Ok I got an ip address pings the ip adress and it worked find but when I tried to ping [www.google.com](www.google.com) it came back as unknown host

---

### Post by ugm6hr on 2009-02-01
This is a DNS issue - perhaps related to ipv6.

I will try and find the workaround - you can try searching for "disable ipv6" too

---

### Post by ugm6hr on 2009-02-01
[http://ubuntuforums.org/showthread.php?p=6028515#post6028515](http://ubuntuforums.org/showthread.php?p=6028515#post6028515)

---

### Post by famous3warriors on 2009-02-02
Hello ugm6hr I really do have to apologize for this situation.  I feel really dumb at this point.  The Internet connection was not paid for so no connection to the outside world.  I feel really dumb at this point.  I am out of town but staying at a friends house.  When I took the time to calm down relax have a few brews I connected directly to my friends router but to no avail no connection still.  turned on his computer and no connection. WOW so thanks for you help and everything is good to go.  I really do appreciate your help.

---

### Post by ugm6hr on 2009-02-02
No worries.

Glad it's all sorted - crisis averted!

---

