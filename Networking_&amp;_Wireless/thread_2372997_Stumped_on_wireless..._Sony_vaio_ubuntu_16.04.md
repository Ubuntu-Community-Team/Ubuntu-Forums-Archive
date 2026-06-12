---
title: "Stumped on wireless... Sony vaio ubuntu 16.04"
date: 2017-10-01
forum: Networking &amp; Wireless
---

### Post by julio.plastikk.info on 2017-10-01
Hello, I did my best to find the solution to this problem but I am out of it.

The fresh install mimics the behavior of the last install in that it connects to wireless, but yields no internet at home.

It seems to work at school, but that's it. 

Ethernet works great.

My output is attached for network info, if you have a moment.

-j

[https://pastebin.com/6JQxBxJn ]("https://pastebin.com/6JQxBxJn")

---

### Post by ian-weisser on 2017-10-01
What's the exact error at home?

---

### Post by julio.plastikk.info on 2017-10-01
At home, the wireless connects to the router, but I have no access to the internet. I can log into the router is about all.

---

### Post by julio.plastikk.info on 2017-10-01
I'm sorry if that's not helpful... the exact error is beyond me at this point.

I have tried disabling ipv6 and I have tried using different dns servers to no avail.

---

### Post by ian-weisser on 2017-10-01
Well, first I suggest looking again at DNS. The one in your pastebin is on some private network somewhere. Is that DNS Server at home or at school?
Try a public DNS, or multiple DNS to cover both home and school. Make sure your DNS is numeric, or it won't work without yet another DNS.
 With 16.04, be patient - it may take a few minutes.

---

### Post by julio.plastikk.info on 2017-10-01
Thanks for the advice, I'll keep at it and report back with any development. 

I am most suspect of the DNS too.

---

### Post by jeremy31 on 2017-10-01
I suspect wireless power management is causing issues, Intel cards don't function well with power save enabled
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by julio.plastikk.info on 2017-10-01
I seem to have gotten my wireless back, and it's good. 

I thought to copy my gfs network dns server, rebooted, and and that seemed to work. 
I guess patients won out on what seems like such a simple issue. Never again lads!

Jeremy31, thanks for the advice. I'll report back if the problem crops up again. 

I'm much obliged to the both of you, thanks =)

-J

---

