---
title: "Bash script"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by ninajo on 2011-06-06
Hello to everyone.

I am trying to make the traceroute command work in bash script, using only the ping command. To be more accurate I want to see the packet route, which ips passing.

Thanks in advance for your time.
Nina

---

### Post by AlphaLexman on 2011-06-06
What is the output of:
```
traceroute www.google.com
```
Do you want to 'ping' each route to [www.google.com](www.google.com)?

---

### Post by conradin on 2011-06-06
As an added note, if you're coming from windows, ping and traceroute aren't exactly the same in linux. There may well be better networking tools for what your trying to do, though Im not sure exactly what that is.

you might look at the manuals for ping and traceroute, with man ping.
Check out the -R option for ping and try code like:
```

ping -R -c 1 216.239.51.99

```
Thats one of google's servers

---

### Post by CVGH on 2011-06-06
Try:
```
mtr 216.239.51.99
```

---

