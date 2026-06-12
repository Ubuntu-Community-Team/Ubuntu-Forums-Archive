---
title: "Kill command in bash script"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by sohaikia1 on 2009-06-03
Hi,

I wrote a bash script that compiles a C source code and then kills any existing running process with same name as the executable, then executes the newly compiled file. Problem is the script stops running the next line after the 'kill' line. Can anyone tell me whether whats the cause of this problem?

```

#!/bin/bash
gcc tiny.c /usr/local/lib/libfcgi.a -o tiny
psid_to_delete=$(ps -A|awk '/tiny/ {print $1}')
kill -9 $psid_to_delete
spawn-fcgi -a 127.0.0.1 -p 1026 -f ./tiny
```

---

### Post by Mornedhel on 2009-06-03
Your awk command returns pids for all processes matching /tiny/, including for instance "thistiny" and "tinythat". If your shell script has tiny in the name, it may commit suicide if it's the only such process ; otherwise you get a list of newline-separated pids in $psid_to_delete. Try / tiny$/.

---

### Post by sohaikia1 on 2009-06-03
> **Mornedhel said:**
> Your awk command returns pids for all processes matching /tiny/, including for instance "thistiny" and "tinythat". If your shell script has tiny in the name, it may commit suicide if it's the only such process ; otherwise you get a list of newline-separated pids in $psid_to_delete. Try / tiny$/.

Thanks Mornedhel! I understand now, its because I named the script as tiny_script.sh, the kill command might have killed the shell script all the while.

---

