---
title: "What is raw6 ?"
date: 2021-08-18
forum: Networking &amp; Wireless
---

### Post by thumper76 on 2021-08-18
Can anyone tell me what raw6 (with a foreign address of 7) is and why it's running on my machine?
```

sudo netstat -peanutw         
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name    
tcp        0      0 192.168.1.141:47106     34.209.200.8:443        ESTABLISHED 1000       54248      2666/firefox-esr    
tcp        0      0 192.168.1.141:38170     34.216.180.35:443       ESTABLISHED 1000       57910      2666/firefox-esr    
tcp        0      0 192.168.1.141:60956     35.186.227.140:443      ESTABLISHED 1000       57911      2666/firefox-esr    
udp        0      0 192.168.1.141:68        192.168.1.1:67          ESTABLISHED 0          19396      551/NetworkManager  
raw6       0      0 :::58                   :::*                    7           0          20899      551/NetworkManager  

```

---

### Post by QIII on 2021-08-18
It's a socket associated with IPV6.

You have, for instance TCP6, UDP6, RAW6, etc

You can find it with 

```
sudo cat /proc/net/sockstat6

```

---

