---
title: "Using options with &quot;time&quot; command"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by protargol on 2009-03-09
I'm having trouble running the 'time' command and getting it to use options.  For instance, this is what I get:
```
#time -o out acroread
bash: -o: command not found

real	0m0.135s
user	0m0.108s
sys	0m0.024s

```

It's mistaking the '-o' option as a command.  How can I overcome this?  Thanks.

---

### Post by kanikilu on 2009-03-09
I think in bash you have to use the full path: ```
/usr/bin/time -o out acroread
```

At least, according to the man page ;) ```
man time
```

---

### Post by mcla0203 on 2009-03-09
yeah...

it is trying to run the shell built in command, but you want to use the external one, as shown directly above

---

### Post by protargol on 2009-03-09
> **kanikilu said:**
> I think in bash you have to use the full path: ```
/usr/bin/time -o out acroread
```

At least, according to the man page ;) ```
man time
```

Ha, didn't catch that line in the man page the first time around. [sheepishly]Thank you[/sheepishly]

---

