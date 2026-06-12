---
title: "simple question about a security update"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-09
i've just had an update available (description [here]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/410171")
in order to take advantage of this vulnerability do you need to be already a user inside the system?

---

### Post by zvacet on 2009-09-09
I will not take any chances.I will install it.

---

### Post by dearingj on 2009-09-09
This update was announced in an [Ubuntu Security Notice]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce") email. Here's what the email said about it:

> In general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

Russell Senior discovered that the system authentication module
selection mechanism for PAM did not safely handle an empty selection.
If an administrator had specifically removed the default list of modules
or failed to chose a module when operating debconf in a very unlikely
non-default configuration, PAM would allow any authentication attempt,
which could lead to remote attackers gaining access to a system with
arbitrary privileges.  This did not affect default Ubuntu installations.

---

### Post by 3rdalbum on 2009-09-09
You might as well just install it, in case you decide to play around with PAM later on, or even just so you can no longer be bothered by seeing the update there :-)

---

