---
title: "Ethernet problem"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by bitslow on 2009-03-25
Hi,

Firstly apologies if this has been covered before - I'm sure that it has but I've searched all day and can't seem to find an answer.

I have just decided to learn a little  about linux, and have installed Ubuntu on a partition of my MSI wind using WUBI.

The installation went fine, I fired up Ubuntu (8.10) and had a mess around trying to get familiar, then decided to get my updates.

I already had the laptop plugged into my WIRED connection, I'm aware from looking on the MSIWIND forums that I have to download and install a driver before my wireless interent will work.

The update manager found quite a list of updates, and I set it downloading and installing them.

Now comes the problem, I cant connect to the internet anymore...?!  The icon at the top of my screen shows a network icon, and if I click on it, it shows me 'Auto eth0' which I select.  I then get the 'connecting' icon, before being told 'DISCONNECTED - The network connection has been disconnected'.

Sorry again if I'm dragging up old stuff

---

### Post by iBurger on 2009-04-07
Some hints howto go further;

open up terminal and enter:

```
lspci
```

try to find out how your wifi adapter is exactly called, and post a new topic.

---

