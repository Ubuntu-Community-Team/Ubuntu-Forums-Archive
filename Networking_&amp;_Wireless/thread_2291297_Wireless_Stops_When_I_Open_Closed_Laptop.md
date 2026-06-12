---
title: "Wireless Stops When I Open Closed Laptop"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by eric75 on 2015-08-19
I am running ubuntu 14.04 on an Asus X550CA. Sometimes I close my laptop when I go to sleep, or to put in my bag for travel. 

Usually when I open it, all works, and the wifi resumes. Sometimes the wifi does not work. The symbol is replaced with a 'pie-shaped' triangle, and won't work unless I reboot.

Anyone know why this is? How can I keep it from happening?

---

### Post by matt_symes on 2015-08-19
Hi

Hav you been bitten by the "network manager sleeping after resume" bug ?

When you resume and network manager is not working, open a terminal and type

```
nmcli nm
```

Post the results back here. Looking for state of sleep.

Kind regards

---

### Post by eric75 on 2015-08-21
Hi, thanks. Those are cool quotes. I think that is the issue. Happened again today, ran the command, here's what I saw:

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         asleep          enabled         enabled    enabled         enabled

---

### Post by matt_symes on 2015-08-21
Hi

I like those quotes as well :)

You have the bug as STATE asleep. I'll post a fix in the next hour.

Kind regards

---

### Post by matt_symes on 2015-08-21
Hi

Open a terminal, copy and paste the text below into it. Hit enter and then enter your password

```

sudo tee /etc/pm/sleep.d/30_networkmanager<<EOF
#!/bin/sh

case "${1}" in
    resume|thaw)
    nmcli nm sleep false
    ;;
esac
EOF

```

Kind regards

---

