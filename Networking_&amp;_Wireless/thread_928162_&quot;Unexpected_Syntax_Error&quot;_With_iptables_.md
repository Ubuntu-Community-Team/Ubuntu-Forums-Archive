---
title: "&quot;Unexpected Syntax Error&quot; With iptables Command"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by odduck on 2008-09-23
First off, I'm admittedly no the most savvy person with the terminal, but I'm learning.

I'm trying to open up the ports on my Ubuntu machine so that I can get Azureus working optimally (as per [this tutorial]("http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu")) but when I enter in the line: 

```
iptables -I INPUT -p tcp --dport <52535> -j ACCEPT
```

I get the error: "syntax error near unexpected token '52535'"  (52535 being the port I've opened on my router for Azureus).

Any help with why I'm getting this error message or with this process would be greatly appreciated.  Thanks in advance.

---

### Post by willca on 2008-09-24
iptables is good but if you are new to it i suggest going with the gui.

sudo apt-get install guarddog or firestarter

Both do use iptables.

---

### Post by odduck on 2008-09-24
ah ok, thanks.  i'll give one of those a shot.

i'm still curious, though, about what that error is all about?

---

