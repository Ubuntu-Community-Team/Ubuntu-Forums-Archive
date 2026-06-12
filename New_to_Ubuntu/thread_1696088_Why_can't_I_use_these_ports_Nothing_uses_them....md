---
title: "Why can't I use these ports? Nothing uses them..."
date: 2011-02-26
forum: New to Ubuntu
---

### Post by newn on 2011-02-26
Hi. I am unable to use ports like 27022. And nothing seems to be using them. What could be the reason?

---

### Post by doas777 on 2011-02-26
> **newn said:**
> Hi. I am unable to use ports like 27022. And nothing seems to be using them. What could be the reason?

in what way are you trying to use them?

for a port to be open, it must have an application listening on it, and it must be allowed through the firewall. 

you can see your listening ports with 
```
sudo netstat -ntlup
```

and you can check your firewall rules with 
```
sudo ufw status
```

---

### Post by asmoore82 on 2011-02-26
Just to clarify, could you do this simplest form of test?

In a terminal:
```
nc -l 27022
```

In a new terminal:
```
nc localhost 27022
```
Type some stuff, returning after each line. Then Ctrl+d to stop

Did it go to the first terminal?

It's working fine over here. AFAIK, a firewall or port already in use
is the only thing that should stop this simple test.

---

