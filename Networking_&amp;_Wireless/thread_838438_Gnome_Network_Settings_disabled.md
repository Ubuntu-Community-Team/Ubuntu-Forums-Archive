---
title: "Gnome Network Settings disabled"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by fmouse on 2008-06-23
I just upgraded my Dell D600 laptop from Gutsy Gibbon to Hardy Heron, and among the several glitches which emerged from the upgrade is that after the upgrade, when I bring up the Gnome Network Settings dialog (/usr/bin/network-admin), every possible input field on it is disabled in the GUI and it's virtually useless.  Before the upgrade it worked OK, although I wouldn't describe it at well-designed software :( 

I have a few clues.  First, if I log in as root and run a root Gnome desktop, the dialog works as expected.  The problem occurs when logging in as a mere mortal.  The app works via gksudo, and running it at the CLI level from a root shell, or via gksudo when logged into Gnome as a non-root user, I get the following:

```
~# network-admin 

(network-admin:10949): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:10949): CRITICAL **: Unable to lookup session information for process '10949'

```
The second error seems to be the operative one here.  When logged in to a root desktop I don't get this error and network-admin is functional.

What do I need to do to make session information available to network-admin?

---

### Post by fmouse on 2008-06-23
A different gksudo invocation made the Network Settings UI available.  In this case, I used "gksu -w network-admin", which works, but network-admin is still ****.  As before, it's usable, but barely.  If I run it from the System | Administration | Network menu item it's still disabled.  This should not be.  Perhaps dbus /etc/group or some other facility needs to be tweaked.

I tried creating a new user with administrative privs, but to no avail - same problem.

---

