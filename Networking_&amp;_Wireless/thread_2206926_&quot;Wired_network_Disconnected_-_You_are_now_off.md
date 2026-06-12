---
title: "&quot;Wired network Disconnected - You are now offline&quot; message appears constantly"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by mirela3 on 2014-02-21
[COLOR=#000000]Hello!
 I just joined the ubuntu community and just installed Bio-linux 7 (Ubuntu Linux 12.04 LTS base) on  my Lenovo G550 along with windows 7. The wire is plugged in but a notification pops out  after about 2-5 minutes and says "Wired network Disconnected - You are now offline".  And the internet isnt working. I mention that on windows 7 on the same laptop the wired network works perfectly. I dont know how to fix it. The wireless works just fine after i activated in additional drivers. Could anyone please help me fix this?:confused:[/COLOR]

---

### Post by varunendra on 2014-02-21
Welcome to the forums mirela3 !

Please open a terminal (Ctrl-Alt-T on Ubuntu, not sure about Bio-linux), and post back the output of the following commands-
```
uname -mr
sudo lshw -numeric -C network -sanitize
```

---

