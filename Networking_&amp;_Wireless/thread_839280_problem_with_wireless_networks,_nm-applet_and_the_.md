---
title: "problem with wireless networks, nm-applet and the keyring-manager"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by szopa on 2008-06-24
Hi,

When I logged in today, I was surprised by Gnome asking first for the password to unlock the keyring, then for the passphrase to my wireless network. This isn't normal, because such stuff is supposed to be in the keyring unlocked on login. I gave them, but it didn't work.

Then I decided that something must have gone wrong with the keyring, os I just removed it. However, this also didn't help. When I start nm-applet in a terminal, I keep getting error messages like the following:

** (nm-applet:21199): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:21199): WARNING **: <WARN>  real_write_secrets_cb(): Error saving secret for wireless network 'iwicka' in keyring: 5

I suspect this may have something to do with nm-applet referring to a non-existing keyring...

Does anybody have similar problems? Is there a way to completely wipe nm-applet settings?

---

