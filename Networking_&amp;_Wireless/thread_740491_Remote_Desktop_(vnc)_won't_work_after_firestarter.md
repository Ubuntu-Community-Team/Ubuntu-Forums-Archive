---
title: "Remote Desktop (vnc) won't work after firestarter"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by stringkarma on 2008-03-30
Hello,

I was playing with firestarter to get my desktop to share internet to my laptop. I finally decided that it wouldn't work and removed firestarter. Since then I cannot connect to the desktop via remote desktop (using the ubuntu standard programs on each comp.) which had always worked flawlessly.

I can connect to the desktop via SSH and can ping it too.
I have seen some threads about reseting iptables and though it seems that I accomplished that, still no vnc!

Thanks for any help!

---

### Post by The Cog on 2008-03-31
The command ```
sudo iptables -nvL
``` will show you if there are still any firewall rules in your box. If there aren't then you will get three heading lines with no rules under them, and in that case, whatever your problem is it's not down to firestarter.

Also, the command ```
netstat -ltn
``` will show you what ports are being listened to. VNC will be on 5800 and 5900 if it is listening at all.

---

### Post by stringkarma on 2008-03-31
Ok I guess its the listening ports thing. IPtables seems clear, but I get this from netstat -ltn:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:45769           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:113             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:1234            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN 
```

So how do I get the computer to listen on vnc's ports?
Thanks again.

---

### Post by The Cog on 2008-03-31
Go System->Preferences->Remote Desktop. Then check the box to allow users to view the desktop. This opens port 5900 (not 5800).

---

