---
title: "Thunderbird not responding"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-09
Running Ubuntu 10.04 LTS.

When I go to Applications > Internet > Thunderbird I am given an error message that tells me Thunderbird is already running but is not responding.

I went into the terminal and tried:

```
kill thunderbird
```

Tells me it has to be done using a job id

```
ps
```

To try and see the running processes an find that job id. It only lists "bash" and "ps" in the results.

```
stop thunderbird
```

Tells me thunderbird is an unknown command.

```
restart thunderbird
```

Tells me thunderbird is an unknown command.


I'm have my web browser open with some tabs at key sites for research right now. I don't want to deal with closing it so I can restart the computer.

Is there another way?

---

### Post by centaurusa on 2011-07-09
In a Terminal window, type:

pgrep thunderbird

This will return a process number (e.g. 3934)

Using the actual process number displayed on your system, now type:

kill 3934

This should shut Thunderbird down.

---

### Post by ClientAlive on 2011-07-09
> **centaurusa said:**
> In a Terminal window, type:

pgrep thunderbird

This will return a process number (e.g. 3934)

Using the actual process number displayed on your system, now type:

kill 3934

This should shut Thunderbird down.


Worked like a charm. Thank you.

This thing was rapped out to the max too. As soon as I shut it down I could hear the whole machine slow down.

---

### Post by centaurusa on 2011-07-09
Pleased to be of assistance.  Now, you should mark this thread as SOLVED.

---

