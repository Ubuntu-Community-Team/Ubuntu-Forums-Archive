---
title: "seirra wireless with telstra and  ubuntu"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by nuttycake on 2011-07-30
this is my first time here and first time user of ubuntu ... my problem is I can not connect my next g, sierra wireless usb stick using ubuntu but I know it can be done. Can anyone help me.... step by step please as I am not happy with techno terms.... many thanks :confused:

---

### Post by therog726 on 2011-07-30
> **nuttycake said:**
> this is my first time here and first time user of ubuntu ... my problem is I can not connect my next g, sierra wireless usb stick using ubuntu but I know it can be done. Can anyone help me.... step by step please as I am not happy with techno terms.... many thanks :confused:

Can you post some more detail? Like the model of the usb stick (Should be on it somewhere or on the box it came in) also what version of ubuntu you're running? Then we'll do what we can to help with no techno talk!! ;)

Thanks! :popcorn:

---

### Post by Wim Sturkenboom on 2011-07-31
We probably need some info ;)
Open a terminal and run the lsusb command before and after you have inserted the dongle
```

fortyfourgalena@desktop-01:~$ **lsusb**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fortyfourgalena@desktop-01:~$ **lsusb**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]**Bus 001 Device 004: ID 13fe:1e00 Kingston Technology Company Inc. **[/COLOR]
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fortyfourgalena@desktop-01:~$ 

```
Post the output here. I've marked the difference in above example in red (and it's for a memory stick).

As you don't mention the Ubuntu version, I assume it's 11.04 and I don't know how to get to a terminal. In earlier versions, applications -> accessories -> terminal

You can close the terminal by typing *exit*

---

