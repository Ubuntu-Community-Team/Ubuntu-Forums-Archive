---
title: "Updating on a dial-up connection"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by alpage2 on 2009-08-18
I am away from home and my normal broadband service, but can access a dial-up service. However, it automatically disconnects every 2 hours, which doesn't give enough time to do large updates, such as a new kernal.

Can the Update Manager resume an interrupted download?

And if so, any limitations on that? does it have to reconnect immediately, or can I reconnect the next day and still resume a download?

If I use apt-get update in a terminal, can the terminal resume an interrupted download?

Thanks in anticipation.
Alan

---

### Post by philinux on 2009-08-18
I've had my wireless cut out a few times during an update and yes it does pick up where it left of if you issue the command again.

---

### Post by alpage2 on 2009-08-18
Many thanks, Phil

Sorry to be pedantic, but I don't want to waste a 2-hour download by assuming too much.

I don't think there is any way to issue a command in the update manager gui? So I assume you mean the terminal, as in:

sudo apt-get update again

Thanks
Alan

---

