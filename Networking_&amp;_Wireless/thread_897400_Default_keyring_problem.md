---
title: "Default keyring problem"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by Lorelei- on 2008-08-22
I'm running 8.04 at home and when I log into my system it displays the following message:'nm-applet(/usr/bin/nm-applet) wants access to the default keyring, but it is locked.'  I found the solution posted on here to this in an earlier thread, but when I've tried this solution on my own machine at home it comes up telling me that I don't have the access requirements to change the password for the automatic login key!

So any other suggestions on how to resolve this?

---

### Post by luckyuser on 2008-08-31
by mkbecker:

Re: [SOLVED] Keyring trouble
I found a solution in the archives from May.

"To get rid of the keyring prompt after automatic login in Hardy 8.04 you can:

System>Preferences>Encryption and Keyrings
Under Password Keyrings click o 'login Automatically unlocked when user logs in.'
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank."
Click OK

This did it for me.

The downside of this workaround is that it leaves your password exposed to anybody who has access to your files.

from the thread [http://ubuntuforums.org/showthread.php?p=5698832#post5698832]("http://ubuntuforums.org/showthread.php?p=5698832#post5698832")

---

