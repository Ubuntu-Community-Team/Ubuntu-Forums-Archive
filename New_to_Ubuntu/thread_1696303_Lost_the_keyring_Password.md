---
title: "Lost the keyring Password"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-02-27
Sorry to  bother people with a numpty question but it appears that I wrote the keyring password down wrongly.

The situation is this:

1.  I have just installed Ubuntu.
2.  I am logging in for the first time.
3.  A box headed "Unlock Keyring" has appeared saying that "An application wants access to the keyring 'Default', but it is locked."
4.  It won't accept the password for logging in or the keyring password that I defined when I was trying out Ubuntu using a memory stick.

Is there any way of defining a new keyring password?  What is the keyring for anyway?

TIA

Nick

---

### Post by vivek.pandey on 2011-02-27
can you make out which applications' keyring is it?

---

### Post by Frogs Hair on 2011-02-27
Take a look at this.[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by Churchwarden on 2011-02-27
It just said "An Application..."

N

---

### Post by Churchwarden on 2011-02-27
> **Frogs Hair said:**
> Take a look at this.[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

Those look useful links. Thank you.

The request has now gone away for some unknown reason so I will keep these links for the next time it turns up.

Nick

---

### Post by Churchwarden on 2011-02-27
> **neo_aryan said:**
> can you make out which applications' keyring is it?

It looks as if it is to do with the wireless router.  I seem was getting it every time I tried to connect.   I would then cancel the keyring password request and it would take me to the box to enter the psk code which then appeared to work.  Very soo, though it would be asking for the keyring password again.

Nick

---

### Post by vivek.pandey on 2011-02-27
well something similar happened with me too. with me it was my internet connection through my 3g modem. i configured my modem again. it was just deleting it from the network manager and plugged in modem again. ubuntu detected it as a new 3g gsm device and i entered a couple of needed things and made sure to drop any elevated privileges . now i dont need any key ring .

---

