---
title: "connected to router no internet"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by robalcorn on 2010-09-02
I finally convinced my wife to get rid of xp and use ubuntu 10.4 on her acer 5102WLMI laptop. After a fresh install i can connect to my router but no browser loads a page. I also have the same laptop and i have no issues. What am I missing?

---

### Post by bodhi.zazen on 2010-09-02
What are the contents of /etc/resolv.conf ?

If they are empty, you need to add your router for DNS. You would do this in networkmanager or manually.

---

### Post by eriktheblu on 2010-09-02
I assume your connecting wirelessly.

Sometimes you can connect to a wireless network without proper authentication.

Check and recheck the connection settings. Make sure you're using the correct protocol. If you are using a passphrase, you might consider trying the hexdecimal.

---

### Post by robalcorn on 2010-09-02
> **bodhi.zazen said:**
> What are the contents of /etc/resolv.conf ?

If they are empty, you need to add your router for DNS. You would do this in networkmanager or manually.

They are the same as my other laptop.

---

### Post by bodhi.zazen on 2010-09-02
Are you sure you are connected ?

What happens when you ping your router ? ping google.com ?

---

### Post by robalcorn on 2010-09-02
When i ping the results are fine. I decided to just reset the router to factory settings and re applied everything and rebooted and life is good. Thanks to everyone for taking the time to help very much appreciated.

---

