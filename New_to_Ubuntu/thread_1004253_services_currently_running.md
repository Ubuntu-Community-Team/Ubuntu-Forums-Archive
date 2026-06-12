---
title: "services currently running"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by ub007 on 2008-12-07
Hi,

A quick question.What are the command/s that would show which services are currently running on my machine,for example I need to know whether the firewall service is currently running...

I could say something like 

> service iptables stop

But prior to that ,I like to know whether its running in the first place..

Thanks in advance
David

---

### Post by taurus on 2008-12-07
Do you mean

```
ps -A
```

---

### Post by sdennie on 2008-12-07
You might be able to use pgrep here:

```

pgrep iptables

```

If any pids are returned, it's running.  You can also use that notation (though, it's not exact) in a script like this:

```

while pgrep iptables ; do
   something
done

# iptables has finished
something_else

```

---

### Post by ub007 on 2008-12-07
Thanks guys,I guess pgrep hits right on the money in this case.ps would be handy as well

---

