---
title: "CIFS shares not mounted with pam_mount at first gdm logon"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Sekim on 2008-11-23
Hi,

At home my family has a mixture of desktops (connected via wire to the network) and laptops (connected via wireless to the network).  My target is to have some shared filesystems (from a small NAS) available for everybody when they login to Ubuntu (Intrepid Ibis).

For some time I've been using /etc/fstab entries with mount.cifs and a credentials file for the authentication.  I've found this to be less satisfactory if on each computer I have multiple persons logging in - as the authorizations on the mounted directories are dependent on the initial credentials specified and not on the person logged on.  So, I started yesterday to setup pam_mount.

My setup works, for the computers attached via a wire, as they quickly connect to the network.  I have set it up by modifying three files:
/etc/fstab: basically I removed all the previous entries here for the CIFS mounts and the associated credential files.

/etc/pam.d/gdm, where I appended @include common-pammount.

/etc/security/pam_mount.conf.xml (versions with and without _netdev option for mount.cifs are attached)

For the computers connecting via wireless to the network, though, the setup fails when I logon with a user the first time via gdm.  NetworkManager does not manage to complete the wireless connection before the pam_mount module tries to mount the CIFS filesystems, as can be seen from the log extracts attached (debug mode on).

If the user then logs off and logs on again via gdm, all the CIFS shared filesystems are available, since the network connection is maintained between these log-ons.

Is there anybody who could help me ensure that the pam_mount module does not execute until the wireless connection (preferably my own named connection) is established/activated?

Best regards - Sekim

---

### Post by Sekim on 2008-11-28
bump

---

### Post by prrrtpieppieptoettoet on 2010-01-04
Did you ever get this fixed? I'm having the same problem: wired the mounts are ok, wireless pam_mount complains about the realpath not existing (as the network interface is not up yet).
Grtz!

---

### Post by rhp997 on 2010-03-17
I'm also having this issue in Ubuntu 9.04.  Works fine when wired.  Curiously (related?), after logging out and then back in again, gnome seems to hang at the password entry screen for a long time (some sort of network timeout?) before *finally* letting me in...and then with errors aplenty.  This timeout problem only happens when I'm wireless.

---

