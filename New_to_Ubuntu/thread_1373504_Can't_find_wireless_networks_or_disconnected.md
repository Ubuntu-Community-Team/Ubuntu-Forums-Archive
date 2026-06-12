---
title: "Can't find wireless networks or disconnected"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by MasonOrange on 2010-01-05
I'm a new Ubuntu user (as of last night) and I'm connected via ethernet cord.  Ubuntu will not recognize any wireless connections (using HP dv8000 with internal wireless card) and I'm in an apartment so it should recognize a number of them.  In the network manager it says "disconnected" under wireless networks.  I have a hawking 802.11g router.  I've tried to help it manually find my Hawking router using WEP 128 and that just gives a shadowed box underneath the network manager that says it's disconnected.  I'm dual-booting with Windows XP and using the most recent Ubuntu with the most recent updates (from ubuntu.com).  Can anyone help?

---

### Post by warfacegod on 2010-01-05
Open a terminal and type this code:


```
sudo iwlist scanning
```


That will scan for wireless networks.

---

### Post by MasonOrange on 2010-01-08
I got the message "Interface doesn't support scanning" for the 1st 3 methods.  For wlan0 I received the message "Interface doesn't support scanning : Network is down."  Obviously it isn't because I connected via cable.

---

### Post by warfacegod on 2010-01-08
> I got the message "Interface doesn't support scanning" for the 1st 3 methods

That's normal.

> Interface doesn't support scanning : Network is down.

That's not.



I've never heard of that result from scanning for wireless signals. Try going to: System> Administration> Hardware Drivers and look for a wireless driver and activate the recommended one. If there isn't one there, you will need to find the chipset of your wireless card with this in terminal:

```
lspci
```

After that, my knowledge ends. Sorry. Try searching for your chipset in the Networking forum.

---

### Post by MasonOrange on 2010-01-08
Wow, worked, and such an easy fix.  Thanks a lot both of you!  I feel like my Linux experience can officially begin now.

---

### Post by warfacegod on 2010-01-08
> Wow, worked, and such an easy fix. Thanks a lot both of you! I feel like my Linux experience can officially begin now.

Glad to hear it. Both of who? I'm the only one that's replied in your thread so far that I see. Don't forget to mark this as solved under Thread Tools. Good Tuxing and have fun!

---

### Post by MasonOrange on 2010-01-08
Maybe if I was more perceptive I would have solved the problem quicker.  Thanks to you anyway!

---

