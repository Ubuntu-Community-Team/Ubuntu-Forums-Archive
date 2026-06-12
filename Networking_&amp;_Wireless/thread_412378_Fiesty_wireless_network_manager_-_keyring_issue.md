---
title: "Fiesty wireless network manager - keyring issue"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by laltopi on 2007-04-18
I have the wireless network setup using the network manager and have enabled the roaming mode. This allows for selection of the keys and has saved them with the gnome keyring. When connecting on each login it asks for a password and when the correct password is entered - it connects to the network very nicely. However, if an incorrect password is entered by mistake, there  is no dialog to retry the password entry - the network connection fails and the network manager starts asking for the network key again. This time entering the correct key does not help connect correctly either. The only work around I have found is to log out and back in and enter the right password for the gnome keyring.

Has anyone else seen this? Is there a way to get the gnome keyring to retry on a bad password vs seeing the network manager fail and ask for the wireless key again and again and fail even when the correct wireless network key is supplied?

---

### Post by wyth on 2007-04-18
As far as I know, there's no easy way to redo the keyring.  What you'll have to do is eliminate that network from your list of networks and start again.

Go to the Configuration Editor and then to /system/networking/wireless/networks.  Select the network with the mistaken key, right click the entries, and unset the key.

You may be able to unset the key with the password and just try that.

---

### Post by srt4play on 2007-04-18
> **wyth said:**
> As far as I know, there's no easy way to redo the keyring.  What you'll have to do is eliminate that network from your list of networks and start again.

Go to the Configuration Editor and then to /system/networking/wireless/networks.  Select the network with the mistaken key, right click the entries, and unset the key.

You may be able to unset the key with the password and just try that.

Hey you're from Charlottesville, cool!   What I understand of the first post is the problem is not with the network keys, but the keyring manager password.  He means when you mistype the keyring password.  And I agree, there needs to be a 'retry password' dialog that comes up similar to when you mistype your sudo password where a dialog comes up saying 'sorry , incorrect password try again'.

---

### Post by wyth on 2007-04-18
Ah, got it.  I was rushing out the door when I wrote that -- read and wrote too quickly.  Maybe it'll come in handy for something else.

Yep, I'm from Charlottesville.  Stuck in a never-ending grad school cycle of teaching and writing.

---

