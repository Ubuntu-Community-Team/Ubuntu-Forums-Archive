---
title: "AUtomatix2 and proxies"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by tuqann on 2006-12-05
Hello everyone,

Been working for a couple of days trying to make Automatix2 startup. I'm getting the error where Automatix2 doesn't seem to connect to their server and I don't get the key. I installed automatix just like the site suggested, and nothing seems out of the ordinary.

Now, I have apt-get working fine behind my proxy, but wget doesn't work when I try it with a random file from the internet (I get something about unable to resolve the host).

I remember editing a file a long time ago, but I forgot where. There are a couple of files, one in apt directory and one in etc for wgetrc that I punched my proxy in.

Any ideas? Usually the simplest problems with me for Ubuntu are the hardest to solve, mainly because the answer is very simple and easy that noone wrote it.

Thanks in advance

---

### Post by outlaws42 on 2006-12-05
to configure wget, /etc/wgetrc works for me. Make sure you are uncommenting the line  
```
use_proxy = on
```

---

### Post by tuqann on 2006-12-05
thanks for the reply, but I already knew about the use_proxy option, and yes it is on. Any ideas where other proxy settings can be setup?

---

### Post by arnieboy on 2006-12-05
Declare both your http **AND** ftp proxies in /etc/wgetrc and also in your $HOME/.bashrc

---

### Post by tuqann on 2006-12-06
I didn't know that .bashrc was hidden, but I found it by chance and now it's fixed. Thanks

---

