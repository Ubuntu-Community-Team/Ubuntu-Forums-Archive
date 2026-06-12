---
title: "Security....any way to track which process is trying to use Network ?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by padmanabh on 2007-04-22
Is there any way I can track which processes are trying to access network and if possible block/unblock them? ...Also how safe is it to do Online Banking transactions on Ubuntu?

---

### Post by spd106 on 2007-04-22
You can use the nestat utility to see listening ports and current connections, though it's not very beginner friendly.

Firestarter is a useful firewall config utility, but it doesn't track outgoing connections.

You don't really have anything to worry about in terms of keyloggers or malware on Ubuntu. As long as you follow the instructions given to you by your bank you should be ok. The biggest limitation is if you need Internet Explorer or Active X plugins, these won't work except perhaps through WINE.

---

### Post by rich.bradshaw on 2007-04-22
Banking is fine, your Ubuntu computer is much more secure than any Windows box, as long as you are only using the official repositories then you should be fine.

---

### Post by padmanabh on 2007-04-22
Thanks...In windows I had a habit of tracking which process is trying to use network because inspite of all the Antivirus stuff I still manged to find creepy suspicious processes in background...often I had to manually stop them. I CAN do that here too i suppose but just that here , I donno which one is legitimate.

---

### Post by padmanabh on 2007-05-05
One more thing I wanted to be clarified....even after I disconnect from my ISP service, I can see my network usage rising for quite some time...say 1 hour or so....is this some security issue?...is some process still using my modem...even after i disconnect from my service?....

I use Motorola ADSL modem (non-USB) ....also after I do 'poff' ...sometimes, when I do 'sudo pon dsl-provider' again, it doesn't ask for the password...it happens even if i close the console....is this a serious risk?

---

### Post by ohioboy757 on 2007-05-05
```
netstat -ap
```

This will display network connections and PIDs associated with them.

If you find an connection you do not like you can use:

```
kill -9 PIDNUMBER
```

---

