---
title: "&quot;200: Command not found&quot; after running a bash one liner"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by LinuxChick on 2011-08-28
root# for ip in $(200 254); do echo 192.168.13.$ip;done > ips.txt
200: command not found


Not quite sure what the problem is. It should be straight forward.

---

### Post by snip3r8 on 2011-08-28
Try separate your commands to root out which one is causing the problem

---

### Post by LinuxChick on 2011-08-28
If I do just "for ip in $(200 254); do echo 192.168.13.$ip"

it seems to think I have more type? It goes to a new line with a > symbol, not sure what's going on.


root@bt:/pentest/enumeration/snmp/onesixtyone# for ip in $(200 254); do echo 192.168.13.$ip
>

---

### Post by LinuxChick on 2011-08-28
Solved


for ip in $(seq 200 254); do echo 192.168.13.$ip;done > ips.txt

is the proper command, i missed the seq

---

### Post by snip3r8 on 2011-08-28
That would explain why it didnt like the "200"

Don't forget to mark your thread as solved.

There is also a facility on the forum to display terminal code better by wrapping them in code tags (# in the text editor).

```
echo "just like this"
```

---

