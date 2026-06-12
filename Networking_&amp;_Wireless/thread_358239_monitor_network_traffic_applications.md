---
title: "monitor network traffic applications"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by ryu kun on 2007-02-10
I listen online radio with my limited internet connection and I want to know how much bandwidth does this cost me. Is there a software that can show me this?

Etherape [seems]("http://etherape.sourceforge.net/images/") too complicated for this purpose.

Any suggestions, please?

---

### Post by ryu kun on 2007-02-10
```
 netstat -taup
```

This command shows which process uses how much traffic. :)

---

### Post by linuchsan on 2007-02-10
It is for the console, but if that is no problem try bwm-ng. It is in the repository.

---

### Post by ryu kun on 2007-02-10
Actually, netstat -taup only shows "Recv-Q" which means "the count of bytes not copied by the user program connected to this socket", according to the manual. So it is not what I am looking for, right?

I'll try bwm-ng, thanks.

---

### Post by carverj on 2007-02-10
> Actually, netstat -taup only shows "Recv-Q" which means "the count of bytes not copied by the user program connected to this socket", according to the manual. So it is not what I am looking for, right?

I'll try bwm-ng, thanks.

This tool (bwm-ng) is awesome for counting throughput in kbps, but is there a tool (other than system monitor) which will allow me to monitor the amount of MB I have downloaded over  a particular period of time?
Thanks

---

### Post by carverj on 2007-02-10
Can prob. answer own q after quick google search
[http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html](http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html)

---

