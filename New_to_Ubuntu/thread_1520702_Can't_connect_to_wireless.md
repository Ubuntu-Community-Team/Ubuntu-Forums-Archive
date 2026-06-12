---
title: "Can't connect to wireless"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-06-29
I tried searching for other posts and came up with trying the command

sudo dhclient etho0

It said, no such device
etho0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device.

I don't know what this means. I tried rebooting several times and my Internet still doesn't work. I can't use a cable.

The wireless on my PC is working just fine.

Please help.

---

### Post by lisati on 2010-06-29
eth0 is usually assigned to a wired connection. Are you able to have any joy with wlan0 instead?

---

### Post by greenleaves123 on 2010-06-29
I did the same command except with wlan0 and go:

wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

What do I do now?

---

### Post by greenleaves123 on 2010-06-29
I found a weak connection without a password and was able to connect to it. How can I connect to my own connection?

I don't know anything about it as my sister's boyfriend set up Internet for me.

---

### Post by RetchingRabbit on 2010-06-29
Turn off any encryption at the router, at least for troubleshooting purposes, and report back.

---

### Post by Bucky Ball on 2010-06-29
Could you run:

```
 lspci
```

... and just make sure the card is still showing up as being physically present in the machine.

---

### Post by greenleaves123 on 2010-06-30
I typed ispci into the terminal and it said "command not found".

Anyways, I called my ISP and they don't support Ubuntu, but they told me to try turning my router off for 30 seconds and turning it back on and it worked!

I'm able to connect to the Internet again!

---

### Post by Bucky Ball on 2010-06-30
'l' not 'i'

lspci

---

