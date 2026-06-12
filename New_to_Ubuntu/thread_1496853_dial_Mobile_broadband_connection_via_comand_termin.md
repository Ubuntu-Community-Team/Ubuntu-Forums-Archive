---
title: "dial Mobile broadband connection via comand? terminal"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by virtualstefan13 on 2010-05-29
Hi Everyone,

A newbie linux user here.  I would just like to ask if there is a command which can I execute via terminal?

Currently, I am using netwrork-manager to connect to the 3G network. I have a ZTE mf627 modem.

any comments?  Thanks

---

### Post by hok00age on 2010-05-29
> **virtualstefan13 said:**
> Hi Everyone,

A newbie linux user here.  I would just like to ask if there is a command which can I execute via terminal?

Currently, I am using netwrork-manager to connect to the 3G network. I have a ZTE mf627 modem.

any comments?  Thanks

First, plug your device (but don't connect to the Internet):
Run:
```
sudo pppconfig
```
Follow instructions on screen.

Then run:
```
sudo pon <provider_name>
```
Replace <provider_name> with name that you've entered in pppconfig.

Hope it helps you.
Regards :)

---

### Post by kvapil on 2011-06-13
This works just Gr8!

Thanks!

---

