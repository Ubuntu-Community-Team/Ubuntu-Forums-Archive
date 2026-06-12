---
title: "Not possible to change password? Now what?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Wanda's on 2010-07-05
Dear Ubuntu community,

I have repeatedly reinstalled different versions of Ubuntu and am now limping along with hardy... at issue now is this unexpected window that I don't understand.  After clicking System-Preferences-About Me, I arrive at this pop up window that states:

"There was an error while trying to get the addressbook information
Evolution Data Server can't handle the protocol"

This is very disturbing.  I am not a programmer... I just want to resolve this problem without having to reformat the machine.

Prior to this I wanted to use the terminal to mount a common program and the terminal would not recognize my password... which is odd because for Applications - add/remove function it does recognize the password... (is this related?)

please clarify, and give simple, clear, step by step instructions TIA

---

### Post by philinux on 2010-07-05
Try reinstall evolution-data-server from synaptic.

---

### Post by Wanda's on 2010-07-05
Thank you for the reply Phil,

However... after the reinstall of evolution-data-server... it did not correct the problem... here is a screen shot of the recurring message after trying to access System-Preferences-About Me:

[ATTACH]162486[/ATTACH]

other ideas?

Please be clear and simple for my feeble mind. 
TIA

---

### Post by the.dark.lord on 2010-07-05
Try uninstalling Evolution.

Go to software center, or

```
sudo apt-get remove evolution
```

---

### Post by Wanda's on 2010-07-05
Thank You Dark Lord!

This worked!  I went the [sudo] terminal route and then installed evolution anew. This resolved up the problem.

City of gardens? Jalapa, capital of Veracruz Mexico? 

Muchas gracias.

---

### Post by the.dark.lord on 2010-07-05
> **Wanda's said:**
> Thank You Dark Lord!

This worked!  I went the [sudo] terminal route and then installed evolution anew. This resolved up the problem.

City of gardens? Jalapa, capital of Veracruz Mexico? 

Muchas gracias.

You're welcome. :)

Not at all! Bangalore, in Karnataka, India! Though, the way it is now, City of Garbage would be a better epithet!

---

