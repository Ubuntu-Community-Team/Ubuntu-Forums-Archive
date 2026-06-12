---
title: "wireless problem"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-26
almost everyday my my laptop suddenly disconnects from my wifi and i cant reconnect unless i restart the whole system.
any ideas?

---

### Post by Darkwing-Duck on 2009-09-28
What version of Ubuntu are you running?

Also, open a terminal and type

```
lspci
```

and paste the output in here.

Also what is the output of:

```
iwconfig
```

And right after it happens the output from:

```
dmesg
```

These should be able to help us determine what is going on.

---

### Post by dvn3ch on 2009-09-28
Sounds like a power management problem.  Well, I should rephrase that.  A power management setting problem.  Need to set the management to performance settings so ubuntu does not shut down external power robbing devices, ie USB connected devices, cd/DVD, etc.  Had this problem on a laptop using Intrepid.  Drlled down into the power management settings and found the setting that timed out certain functions after a specified amount of time.    

:guitar:

---

### Post by kevdog on 2009-09-28
My card used to do that way back in Feisty for no apparent reason.  What I had to do was to make a script that did something like the following:

sudo ifconfig <interface> down
sudo rmmod <driver name>
sudo modprobe <driver name -- same as above>
sudo ifconfig <interface -- same as #1> up


You could then add more to this script if you wanted to make a manual network connection or you would need to use network manager or wicd or whatever GUI you were using to complete the wireless connection.

Yes its a pain, but considering rebooting is such a pain, its at least a better solution.

---

