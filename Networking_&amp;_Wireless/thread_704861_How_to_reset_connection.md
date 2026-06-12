---
title: "How to reset connection?"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by iamvoyager on 2008-02-22
Hello. I have a Windows machine directly to the right of a Linux machine. The Linux machine is connected to the Windows machine with an ethernet cable. The Windows machine has the internet connection and shares it so that the Penguin can surf the InterWeb.... but if the Windows machine is restarted, the Linux box can no longer connect... logging off and on does not correct the problem... I have to restart the Linux machine in order to get the connection to work again.

I am assuming there is an easier way to accomplish the same goal? Thanks in advance :-)

---

### Post by sisco311 on 2008-02-22
yes. you can restart your network from the terminal(Applications -> Accessories -> Terminal):
```
sudo /etc/init.d/networking restart
```

---

### Post by iamvoyager on 2008-02-22
I actually found that command with Google, but it doesn't work (no error, it appears to "work," it just doesn't correct the problem). If I try to load a page in Firefox, it just gets stuck "looking up www.something.com" until it finally says that it can't find the server...

---

