---
title: "Remote Desktop to Ubuntu from windows"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by robert71 on 2014-03-16
Hello, Does anyone know how i can remote desktop from my windows machine to my ubuntu machine.... Thanks

---

### Post by calderon8403 on 2014-03-18
Connect to Ubuntu from Windows via [SIZE=4]RDP[/SIZE] 


press **[SIZE=3]Ctrl – Alt – T[/SIZE]** on your keyboard to open Terminal

When it opens, run the commands

```
[sudo apt-get install xrdp/CODE]

Next, open Windows’ Remote Desktop Connection and type Ubuntu hostname or IP address

When prompted, type your Ubuntu username and password to connect.


If you have a problem connecting, run the commands below and restart Ubuntu, then try again.

[CODE]echo "gnome-session --session=ubuntu-2d" > ~/.xsession
```

Or install gnome session fallback

```
Or install gnome session fallback
```

---

