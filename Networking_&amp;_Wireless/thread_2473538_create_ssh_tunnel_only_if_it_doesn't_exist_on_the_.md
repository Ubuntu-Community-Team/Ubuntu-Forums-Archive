---
title: "create ssh tunnel only if it doesn't exist on the port yet"
date: 2022-04-07
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2022-04-07
Hi all, 

I'm looking for a way to create ssh tunnel only in case it doesn't exist on particular port yet. 

This is how I would check if the tunnel exists:           

```
nc -z 127.0.0.1 9521 || echo "no tunnel open"
```

And this is how I would create the tunnel:         

```
ssh user1@example.com -D9521 -C -N -q
```

Now how do I combine those two or maybe there is another more robust way?... The thing is that I'm not able to install additional software on the system; also I'm not able to copy some pre-compiled executable into the filesystem -- the instance is re-created from scratch every session. I would rather need just to combine those two commands above using bash. 

Please advise.

---

### Post by TheFu on 2022-04-07
```
# Only start SOCKS proxy if necessary

if  [ $(/bin/ps -eaf |/bin/grep ssh |/bin/grep -c $PORT ) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   /usr/bin/ssh  -f -C -D $PORT  $SSH_SRV  -NT &
fi 
```

is how I do it.

---

