---
title: "about start-stop-daemon"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by node2network on 2010-09-07
hi, i have some questions about start-stop-daemon.

i just did 2 steps.

step 1. start choochoo.sh as daemon process
*$ sudo start-stop-daemon --start --pidfile /home/node2network/experiment/foo2.pid --make-pidfile --exec /home/node2network/experiment/choochoo.sh --background*

step 2. stop the daemon process
[I]$ sudo start-stop-daemon --stop --pidfile /home/node2network/experiment/foo2.pid -x /home/node2network/experiment/choochoo.sh
[/I]
when i did the command in step 2, it didn't stop the daemon process with error logs.
[I]No /home/node2network/experiment/choochoo.sh found running; none killed.
[/I]

but i tryed another command, step 2'

step 2'
[I]$ sudo start-stop-daemon --stop --pidfile /home/node2network/experiment/foo2.pid            
[/I]
the command in step2' stopped daemon process as expected.

why step 2 didn't work as expected ?

*choochoo.sh*
```

#!/bin/sh

while(true) do

  sleep 5
done

```

---

### Post by gzarkadas on 2010-09-07
Maybe because the process that runs is your /bin/sh (the interpreter of the script) and not the script itself; so the names do not match (but the numeric pid does). To find out, do the following:

1. Start your test daemon.

2. Once started, look inside the pid file to get the process pid (either with```
cat */home/node2network/experiment/foo2.pid*
``` inside a terminal or by opening it with an editor such as gedit). Write down the number that shows.

3. In a terminal window, type:
```
ps -A | grep <pidnumber>
```
Put the number you read at step 2 instead of <pidnumber>.

4. At the output of previous command, read the process name shown beside <pidnumber>.

---

### Post by node2network on 2010-09-08
Thank you for answering my question.

> 
4. At the output of previous command, read the process name shown beside <pidnumber>.

result is below.

11435 ?        00:00:00 choochoo.sh

and more, 

```
ps aux | grep choochoo.sh
```

result is below.

```
root     11435  0.0  0.0   1832   524 ?        S    13:45   0:00 /bin/sh //home/node2network/experiment/choochoo.sh

```
is "/bin/sh" the cause of thie question?

is there any ideas to avoid this?

---

### Post by gzarkadas on 2010-09-08
Repeat again steps 1 & 2 (start daemon and read contents of pid file) and then execute:

```

ls -l /proc/<pid-number>/exe
cat /proc/<pid-number>/stat

```

Replace <pid-number> with the pid number that you read at step 2. The first command will show a link to the executable of your daemon process (the one to use with the -x switch). The second will show [it is a string within parentheses in the output; discard the rest] the name of your daemon process (the one to use with the -n switch).

You can then try to use start-stop-daemon -x ... and/or start-stop-daemon -n ... with these values to see if they work.

---

