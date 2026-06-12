---
title: "Firestarter issues with 2 interfaces"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by subaru_wrx on 2005-09-06
Hello,
I'm using Ubuntu on my laptop. I use my wireless card when I can, and ethernet the other time.
However Firestarter seems to allow only one interface to go through?
I got some 
```
ping: sendmsg: Operation not permitted
``` 
output when inserted my wireless card and switched to it.

Is there way to make both interfaces operational without manually starting firestarter and changing the "Interned connected" interface each time?

Thanks!

---

### Post by ils_systems on 2005-11-07
I also have 2 interfaces on my laptop, eth0 and wlan0.  I wrote a script that runs in the background and checks which interface is currently active and changes firestarter configuration accordingly.  You could probably modify it to create something that works for you.

#!/bin/sh
while true; do
    ifconfig eth0 |grep -q "inet addr"
    if [ $? = 0 ];
      then
      sed -i 's/wlan0/\eth0/' /etc/firestarter/configuration
    else
      sed -i 's/eth0/\wlan0/' /etc/firestarter/configuration
    fi
    iptables -L |grep -q DROP
    if [ $? != 0 ];
      then  firestarter -s > /dev/null
    fi
  fi
  sleep 5

done

---

