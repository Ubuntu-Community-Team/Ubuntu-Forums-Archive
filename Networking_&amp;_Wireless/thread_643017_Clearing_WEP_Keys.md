---
title: "Clearing WEP Keys"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by gruther4 on 2007-12-17
Hey there...

I'm new to Ubuntu, so go easy on me.  The wireless networking seems pretty good... I just click through a few dialogs and it sets things up, and remembers which network to connect to.

Unfortunately, my roommate recently changed the WEP key for the router, and it seems to be remembering the old WEP key.  It tries to connect, and fails, but does not prompt me to reenter the key.  I can connect manually by using the "Connect to Other Wireless Network..." with the appropriate settings, but this is quite tedious.

Is there a way to clear some or all of the saved WEP keys?  It seems there would be security reasons to want to do this.

Thanks,
Grant

---

### Post by davidgarcin on 2007-12-17
hey Grant,
the application that Ubuntu uses to remember encryption keys is the GNOME keyring.  To edit the keys stored on this keyring, type gnome-keyring-manager in the terminal.  This will open a GUI listing all the keys/passwords that are remembered.  Select the one you want to delete, and choose the "Delete Key" option from the "Keyring" menu.

-Dave

---

### Post by gruther4 on 2007-12-18
Thank you!  That solved the problem.

Grant

---

