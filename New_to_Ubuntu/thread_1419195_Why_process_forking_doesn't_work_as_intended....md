---
title: "Why process forking doesn't work as intended...?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-01
I type this command...


```
sudo wireshark  &

```

I don't see any window, it never prompts for my root PWD. It just seems to ignore it. The command is valid...


So I type this
```

sudo wireshark
```


and it works as it should. So my question is, how am I forking incorrectly? Why doesn't the prior command fork, create a new window.

---

### Post by r-senior on 2010-03-01
How about ...

$ gksudo wireshark &

Anything windowed should be started with gksudo really.

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by TurnOfTide on 2010-03-03
Excellent answer... but what should I do if want to fork a process and not run it in as root?

---

### Post by TurnOfTide on 2010-03-04
bump, anyone?

---

### Post by capscrew on 2010-03-04
> **TurnOfTide said:**
> I type this command...


```
sudo wireshark  &

```

I don't see any window, it never prompts for my root PWD. It just seems to ignore it. The command is valid...


So I type this
```

sudo wireshark
```


and it works as it should. So my question is, how am I forking incorrectly? Why doesn't the prior command fork, create a new window.
What are the implications of forking this as a root process?  Will it leave a root owned shell open to the user?  I believe it would.

My guess is that this a security issue and therefore is not allowed to happen.

---

