---
title: "unable to access keyring password"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-08-13
I lost my password,by using grub i changed my password.
Now i cant access keyring password.
Any suggestions..
Thanks in advance

---

### Post by anewguy on 2010-08-13
If you initially set up your keyring password with password "x", that set the password to "x".  Changing your logon password does not change the keyring password - it would still be "x".

If that isn't your problem, then perhaps you could add some detail so we know what is happening - error messages, prompts, etc., would be very helpful.

Dave ;)

---

### Post by jfreak_ on 2010-08-13
yes, as i said i forgot my login password, and as it so unfortunately happens, the login and the keyring password are the same. I managed to change the login password through grub , but now it seems that the keyring password has not changed. so what to do?

---

### Post by anewguy on 2010-08-13
You could always clear the keyring password and let it ask for a new one.

Dave

---

### Post by jfreak_ on 2010-08-13
I don't get your point (scratching my head). clear where? clear how?

---

### Post by varunendra on 2010-08-13
> **jfreak_ said:**
> I don't get your point (scratching my head). clear where? clear how?
:lolflag:

[Here]("http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/") you go....

[COLOR=Red]**_CAUTION_:** This will erase all (I'm not sure about '**all**') the previous passwords![/COLOR]

---

### Post by jfreak_ on 2010-08-14
> **varunendra said:**
> :lolflag:

[Here]("http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/") you go....

[COLOR=Red]**_CAUTION_:** This will erase all (I'm not sure about '**all**') the previous passwords![/COLOR]



thank u..it wrks

---

