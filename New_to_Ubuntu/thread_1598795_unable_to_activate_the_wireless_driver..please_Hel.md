---
title: "unable to activate the wireless driver..please Help."
date: 2010-10-17
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-10-17
Hi there!
Recently I have reinstalled ubuntu 10.04 in my computer dual booting with windows 7

But when i went to administration-->hardware driver to activate the drivers, there is only one option of driver and that is---->
Broadcom STA wireless driver, but there used to be two of them.
I don't remember the name of  the other one, but it was something boadcom b43 ...

And the big problem is that i can not even activate the remaining option, that is broadcom sta 

It gives an error on activating----->>

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log


Please Help me if you have understand my problem..

---

### Post by diablo75 on 2010-10-17
If this is a fresh install that has not seen a live Internet connection yet (and so hasn't checked for and applied outstanding updates), you should connect an Ethernet cord to the computer (just for a moment) to download and install the latest updates.  This should perhaps restore the alternative driver you once saw in the inventory.

---

### Post by amityadav9314 on 2010-10-17
i am connected to the Ethernet...
Did you mean I have to update my system from the update manager?

---

### Post by diablo75 on 2010-10-17
> **amityadav9314 said:**
> i am connected to the Ethernet...
Did you mean I have to update my system from the update manager?

Yes, System>Administration>Update Manager.  Then click the Check button and then install all the updates it says are available (you don't have to upgrade to 10.10 if you don't want to; it might tell you it's available... if it doesn't, your Software Sources need to be adjusted to allow for "Normal releases").

---

