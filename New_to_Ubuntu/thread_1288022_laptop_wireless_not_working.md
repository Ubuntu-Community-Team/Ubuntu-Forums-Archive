---
title: "laptop wireless not working"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by SLokos on 2009-10-10
I just installed ubuntu 9.04 on a compaq laptop with built-in wireless.  The laptop has a button to turn on/off the wireless but in windows it comes on automatically on start-up.  when i boot in ubuntu the wireless is not on and it does not come on when I hit the button thus I can't get on-line.  I can't figure out how to activate the wireless.  Any suggestions?

---

### Post by B!aine on 2009-10-10
Go to Applications, Internet, Network Manager.  When the window opens, find your network and click connect.

---

### Post by SLokos on 2009-10-10
> **B!aine said:**
> Go to Applications, Internet, Network Manager.  When the window opens, find your network and click connect.
That does not work. No networks are found because the wireless adapter is not turned on and I can't figure out how to turn it on.  Hitting the "on" button does nothing.

---

### Post by lkraemer on 2009-10-10
Boot into Windows, then ENABLE the Wifi with the Button, then exit Windows.
Don't touch the Button again while in Ubuntu.  Forget about the LED in the
Button also.......Wifi will be enabled even though the LED is wrong.....

Find out what Hardware you have.......

Open a Terminal window and Cut/ Paste these commands:
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig

```

Then post the output of each.

lk

---

