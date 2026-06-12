---
title: "[SOLVED] Keyring trouble"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by mkbecker on 2008-08-19
When I boot up my newly installed Ubuntu 8.04 I see the message flash by "intel_rng: FWH not detected."  then, as soon as I have logged in, I am prompted to sign in again with a different password by the message 'nm-applet(/usr/bin/nm-applet) wants access to the default keyring, but it is locked.' Once I provide this password my wireless connection then loads.  Isn't this supposed to happen automatically.  How can I fix this?

---

### Post by mkbecker on 2008-08-20
I found a solution in the archives from May.

"To get rid of the keyring prompt after automatic login in Hardy 8.04 you can:

System>Preferences>Encryption and Keyrings
Under Password Keyrings click o 'login Automatically unlocked when user logs in.'
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank."
Click OK

This did it for me.

The downside of this workaround is that it leaves your password exposed to anybody who has access to your files.

---

### Post by luckyuser on 2008-08-31
This was an annoying problem~! Thanks so much for the fix, it worked for me too!:)

---

