---
title: "UNR wants to re-install"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by tonymoloney on 2009-11-15
I have installed Ubuntu Netbook Remix on my Asus eee701. Now, whenever I start it up, it asks if I want to install the system and I have to quit to get it running.

There's nothing in boot/grub/menu.lst to account for this behaviour, so where else can I look?

Also, before I can do anything with the system, I have to enter my password in the keyring. Is there any way to avoid this, as I am the only person who uses this netbook?

Thanks in advance.
Tony

---

### Post by rustutzman on 2009-11-15
Did you install from a SD card? Is that card still in your machine?

---

### Post by tonymoloney on 2009-11-16
Sorry for the delay in answering - time zone differences etc.

No, I installed from an external DVD drive.

Tony

---

### Post by barrieluv on 2009-11-16
I had the same problem with 9.04.  Removing ubiquity in Synaptic solved it for me.
To remove the password and stop the Keyring constantly asking for it, go to:

Applications > Accessories > Passwords and Encryption Keys

Hit the Passwords tab and then right click the Keyring Password (or whatever it's called) > Change Password.

You have to put the old password in but then don't type anything into the other two boxes and hit Change. A message pops up about lack of security, but that's fine. Hit Ok or whatever and then reboot to see the changes.

---

### Post by tonymoloney on 2009-11-16
That worked.
Thanks a lot.
Tony

---

