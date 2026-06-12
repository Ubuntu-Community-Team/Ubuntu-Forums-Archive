---
title: "expected unary operator when I try to reconnect automatically the connection"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by marietto2008 on 2013-11-17
Hello to everyone,I need help to fix this script,because when ping gives this error "ping: unknown host google.com", it does not work anymore,because this error happens : ./script.sh: riga 7: [: -eq: expected unary operator...after this error the script "thinks" that the host is up when really it's down. thanks.

#!/bin/bash
HOST="google.com"
while [ 1 ]
do
count=$(ping -c 10 $HOST | grep 'received' | awk -F',' '{ print $2 }' | awk '{print $1 }')
echo $count
if [ $count -eq 0 ]; then
echo "$HOST is down (ping failed) at $(date)"
else
echo "$HOST is up"
fi
done

---

### Post by steeldriver on 2013-11-17
There's really no need to use the ping *count *- you can just use the **return value** from the ping command (0 on success, non-zero otherwise)

```

ping -c1 "$host" >/dev/null 2>&1 || echo "Host is down"

```

---

