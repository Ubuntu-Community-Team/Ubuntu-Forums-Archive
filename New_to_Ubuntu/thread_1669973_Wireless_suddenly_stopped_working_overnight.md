---
title: "Wireless suddenly stopped working overnight?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by damien750 on 2011-01-18
Hey everyone. I've had my wireless up and running for quite some time now. There haven't been any problems, connection was always fine, until suddenly last night it stopped connecting.

Now I haven't tweaked any settings on the router or my computer, so there's no reason for this to happen. The only other computer on the network is connecting fine.

On my dual boot computer, both ubuntu and windows show a strong available connection to the router (among with other nearby connections that are password protected). When I try to connect, however, the icon in the upper right just spins endlessly, before notifying me I am disconnected. Even live cds that usually have connection on boot aren't connecting. All of these OS's show the available network from the scan, none will connect.

1: What would cause the wireless connection to just bomb like this?

2: How do I fix it?

Thanks for your help.

---

### Post by Kirboosy on 2011-01-18
Can you give us more details on your computer? Like wireless card chipset, type of computer, etc.

Run this command in the terminal if you aren't sure about your wifi card
```
sudo lshw -C network
```

---

### Post by mick222 on 2011-01-18
Sounds like a problem between your router and either the modem if it's separate or your isp . try using an ethernet connection and reboot your modem and router if that doesn't work.

---

### Post by damien750 on 2011-01-18
I will do that, the router and my computer are in separate households, so it will take me a minute to walk next door.

Also, I just connected the wii to the wireless network and downloaded a demo with no problems. It appears only my computer is having this connection problem.

---

### Post by damien750 on 2011-01-18
Have tried resetting the modem to no avail. 
Router is a separate piece, resetting it now. 

Dell dimension 8300
Wireless card is atheros ar5001x+

---

### Post by Kirboosy on 2011-01-18
What if you try connecting to another wireless point all together?

---

### Post by damien750 on 2011-01-18
> **mick222 said:**
> Sounds like a problem between your router and either the modem if it's separate or your isp . try using an ethernet connection and reboot your modem **and router** if that doesn't work.

Good call. I went to the router's config program on the computer and couldn't seem to do anything, which led to me disconnecting the modem. Physically restarting the router by unplugging the power and replugging it solved the problem. I really don't understand WHY, but it works now. Thank you. 

Man, google searches always fail me, and then I come here and always end up looking like an idiot. ](*,)

---

### Post by damien750 on 2011-01-18
> **Caboose885 said:**
> What if you try connecting to another wireless point all together? 

I am starting to lean to the side of your WiFi card is failing. If no other computers in the house are having issues...

I did try that, but all of my neighbors have their routers password protected.

---

### Post by Kirboosy on 2011-01-18
Glad it was an easy fix. Even though I didn't do much.

---

### Post by walt.smith1960 on 2011-01-18
If this recurs, you might want to check if there are any firmware updates for your router.  Linksys had a problem with their routers locking up.  A firmware update fixed the problem.

---

### Post by walt.smith1960 on 2011-01-18
Duplicate post, sorry.  Could a mod fix this, please?

---

### Post by mick222 on 2011-01-19
> **damien750 said:**
> Good call. I went to the router's config program on the computer and couldn't seem to do anything, which led to me disconnecting the modem. Physically restarting the router by unplugging the power and replugging it solved the problem. I really don't understand WHY, but it works now. Thank you. 

Man, google searches always fail me, and then I come here and always end up looking like an idiot. ](*,)

Glad you got it fixed this happens to me now and then I think it is something to do with my cable company as all my computers seem connected to the router.

---

