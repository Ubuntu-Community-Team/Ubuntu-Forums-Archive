---
title: "no internet"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by degarb on 2011-08-26
I have a working wireless card that was working on a ubuntu notebook.  BUt some 11 year old girl tried to bypass adult protection by bobby pin resetting modem.   I recreated the wireless.

Now, while xp machine, symbian, and wii work with same old settings.  The Ubuntu will not work.  I can get it to pull ip and connect.  But won't pull pages, even with direct ip entry. 


With direct dhcp nothing, but can connect with manual, using old subnet 255.255.255.0   dns 208.67.222.222...  Proper ssid

---

### Post by e79 on 2011-08-26
Could you post the result of :

```
cat /etc/network.interfaces
```

```
ifconfig
```

```
cat /etc/resolv.conf
```

---

### Post by degarb on 2011-08-26
Looks like it thinks it has an ip.  But on router end the ip different.   

Sorry just too much transcribing code jibberish to post results for all. I am about to give up anyway and try again in a few months when better disposed.  I have never had much luck with ubuntu and wireless.  it took 2 day of solid playing to get internet to work.  Now with one reset on router side, back to nothing, while symbian os, wii os, xp os are still connecting with old wep key etc.  Never got wpa ever to work with ubuntu.

---

### Post by e79 on 2011-08-26
> Sorry just too much transcribing code jibberish to post results for all.  I am about to give up anyway and try again in a few months when better  disposed.If you are not inclined to understand and try to solve your problem, it's up to you, and I then wish you good luck.

---

