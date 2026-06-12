---
title: "mv command"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by cmwarre on 2009-12-25
Hey guys.  My problem is that I'm trying to move a binary file from my Desktop to ~/usr/bin.  I have no idea how to use the mv command and it's driving me nuts.  Thanks

---

### Post by taurus on 2009-12-25
Do you mean /usr/bin since ~/usr/bin means usr/bin under your $HOME--~.

If you want to move something to /usr/bin, you need root privilege so sudo in front of the command is a must.

```
**sudo** mv ~/Desktop/filename /usr/bin
```

---

### Post by tom.swartz07 on 2009-12-25
> **taurus said:**
> Do you mean /usr/bin since ~/usr/bin means usr/bin under your $HOME--~.

If you want to move something to /usr/bin, you need root privilege so sudo in front of the command is a must.

```
**sudo** mv ~/Desktop/filename /usr/bin
```

Just what he said.

If you ever have any confusion with a command, you could ALWAYS type

```
*command* --help
```

and it will list help on how to use the command.

in your case, it would be ```
mv --help
```

To learn about the command, IE 'read a manual' guide, you could type

```
man *command*
```

in your case, ```
man mv
```
(to quit from the manual, just hit "q")

---

