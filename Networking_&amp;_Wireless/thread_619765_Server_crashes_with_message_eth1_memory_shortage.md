---
title: "Server crashes with message: eth1: memory shortage"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by captbaritone on 2007-11-21
I recently upgraded my server to Gustsy and now it can't stay up for more then a day or two without crashing. At first the symptoms were just that the server crashed with no message or log, and the only thing I could get it to do was change terminals (Ctrl+Alt+F2). However after enabling (with a little help) some log output to the terminal, I now get this error message when it crashes:

[130220.576000] eth1: memory shortage

Google did not produce any help.

Does anyone have any ideas?

-Captbaritone

---

### Post by MrFSL on 2007-11-21
What device is eth1?

Is it an ethernet port or a wireless etc?

Who is the manufacturer?

Not sure what the problem is but this information will most definitely help whomever can help you.

---

### Post by captbaritone on 2007-11-21
It is an ethernet port. I am not sure about the manufacturer.

---

### Post by MrFSL on 2007-11-21
The following might help identify it:

```
lspci | grep -i net
```

---

### Post by captbaritone on 2007-11-21
```
00:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)
```

---

### Post by captbaritone on 2007-12-09
I still don't really know what was going wrong. But it seemed to be a problem with memory (the machine only has 128 meg of ram). I downgraded the kernel and that seems to have fixed it.

---

