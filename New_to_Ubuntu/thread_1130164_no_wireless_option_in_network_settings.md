---
title: "no wireless option in network settings"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Beaker Boy on 2009-04-19
Ahhh, flashed the computer up today to find that a had no wireless connection available on the Network Settings.  Any one got any advice?

Beaker Boy

---

### Post by jamesrfla on 2009-04-19
Maybe the driver had issues on boot up. Go to System>Administration>Hardware drivers (I think it is restricted drivers for 7.10) Make sure the driver for your wireless card is installed if you do need to install it. It also maybe as simple as a reboot. Also check the wireless button on your computer you might of turned your wifi off. Did you run updates recently? A new update might have screwed it up. Can other computers pick up you wifi network? Maybe you need to reboot your wireless router.

---

### Post by hesjnet on 2009-04-19
run this and post the results
```
lshw -C network
```

---

### Post by JoshuaRL on 2009-04-19
Have you gotten a kernel update just recently?

---

### Post by Beaker Boy on 2009-04-19
> **jamesrfla said:**
> Maybe the driver had issues on boot up. Go to System>Administration>Hardware drivers (I think it is restricted drivers for 7.10) Make sure the driver for your wireless card is installed if you do need to install it. It also maybe as simple as a reboot. Also check the wireless button on your computer you might of turned your wifi off. Did you run updates recently? A new update might have screwed it up. Can other computers pick up you wifi network? Maybe you need to reboot your wireless router.
You genius, me moron.  I remain bottom of the newbie class with nil point.  The WIFI switch was in the Oscar Foxtrot Foxtrot position.

Many thanks

Beaker Boy

---

### Post by Beaker Boy on 2009-04-19
Sorry, I've forgotten how to mark a thread as complete. Could you remind me.

Many thanks

Beaker Boy

---

### Post by jamesrfla on 2009-04-19
> **Beaker Boy said:**
> Sorry, I've forgotten how to mark a thread as complete. Could you remind me.

Many thanks

Beaker Boy

They have removed the solved option on threads due to database issues with the forums. I will add a tag stating this thread is solved. You can find the tags at the end of the last post under bookmarks.

---

