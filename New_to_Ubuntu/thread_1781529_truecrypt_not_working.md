---
title: "truecrypt not working"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by noidian on 2011-06-13
I have been using truecrypt and typically it works but when I restart the computer, I am not able to start the application and ps -elf does not even list the process as running. Whereas, I get a message saying it is already running. 

I tried all kill commands but the process is not listed.

That having said if I shut down and restart it works fine.

---

### Post by crispy_420 on 2011-06-15
I just checked my install and it looks like truecrypt starts two processes when run. My guess you have killed one but the other is lingering.

ps aux | grep truecrypt

---

