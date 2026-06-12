---
title: "[SOLVED] check ip and Diff btwn computer ip and the service provider ip"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by AceDip on 2008-10-24
Hi there.
I want to check my computer ip.
first of all the 
```
ipconfig
```is not at all a command,as shown in google search results.
And wen i
```
$ ip -s route
```
it gives the ip of the connection of the service provider i'm using.But in the gmail account details the computer ip shown, is completely different..

---

### Post by hyper_ch on 2008-10-24
```

ifconfig

```

---

### Post by AceDip on 2008-10-24
well thanks for that but i got it anyways through an extensive search..
but here again..the output of 
$ ifconfig
is completely different from the details of my computer ip shown in gmail.
and secondly i've dynamic ip form the service provider but the
$ ifconfig 
always gives the same ip.
i'm using a router,given by the service provider,whose ip is same as the output of
$ ifconfig

---

