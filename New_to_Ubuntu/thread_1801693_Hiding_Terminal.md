---
title: "Hiding Terminal"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by mortified_pengiun on 2011-07-10
If I launch an application from the terminal, is there anyway to hide the terminal?  

What I'm doing is running Skype through Tor and Proxychains, so when I launch Skype, I have to launch a script that says

```
proxychains skype
```

But then if I close the terminal, Skype also terminates.  Is there any way I can just hide the terminal without it being in my taskbar?

Thanks

---

### Post by wojox on 2011-07-10
```
proxychains skype &
``` ???

---

### Post by mortified_pengiun on 2011-07-10
what?

---

### Post by wojox on 2011-07-10
Sorry, run the name of the script in the terminal and add an & (ampersand). It should free up your terminal.

---

### Post by lmarmisa on 2011-07-10
Try this command:

```

nohup proxychains skype

```

---

### Post by wojox on 2011-07-10
> **lmarmisa said:**
> Try this command:

```

nohup proxychains skype

```

Even better. :P

---

### Post by mortified_pengiun on 2011-07-10
> **lmarmisa said:**
> Try this command:

```

nohup proxychains skype

```

Okay, that worked.  And if I close it, proxychains is still running Skype correct?

---

