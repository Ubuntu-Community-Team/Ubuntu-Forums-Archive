---
title: "stop wine  messages from appearing on console"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by purplearcanist on 2010-08-24
Is there any way to stop wine messages from appearing on the console when I am running a program?

Thanks

---

### Post by decoherence on 2010-08-24
does

```
wine *command* &> /dev/null
```

work? It should redirect STDOUT and STDERR to /dev/null which should keep messages off your console. But it's wine and it has something to do with windows so all bets are off ;)

---

### Post by Silent Warrior on 2010-08-24
Hm... Could you start wine through another tab in the terminal, and then switch back to the first tab?

---

