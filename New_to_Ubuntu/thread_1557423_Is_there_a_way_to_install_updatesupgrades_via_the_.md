---
title: "Is there a way to install updates/upgrades via the recovery mode terminal?"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by diablo75 on 2010-08-20
Someone I know is arm wrestling with a Toshiba A505 series laptop and is having a problem during boot involving the kernel.  I've tried to have them disable acpi (which is what they did in order to get the live-cd to boot) but that doesn't seem to do the trick for the installed OS.

So I was thinking that perhaps there are some updates out there that might magically fix whatever is going wrong with this thing.

It's been a long time since I booted into a recovery terminal to attempt to download updates, but was wondering what would be required.  If you enter a recovery terminal, is your ethernet adapter already enabled and using DHCP?  In other words, if they plugged their laptop into a router, would they have to enable the port and then configure an IP, gateway and subnet mask?

Also, what would the best command be to apply all available updates?  sudo apt-get upgrade?  Or sudo apt-get update?

---

### Post by sandyd on 2010-08-20
> **diablo75 said:**
> Someone I know is arm wrestling with a Toshiba A505 series laptop and is having a problem during boot involving the kernel.  I've tried to have them disable acpi (which is what they did in order to get the live-cd to boot) but that doesn't seem to do the trick for the installed OS.

So I was thinking that perhaps there are some updates out there that might magically fix whatever is going wrong with this thing.

It's been a long time since I booted into a recovery terminal to attempt to download updates, but was wondering what would be required.  If you enter a recovery terminal, is your ethernet adapter already enabled and using DHCP?  In other words, if they plugged their laptop into a router, would they have to enable the port and then configure an IP, gateway and subnet mask?

Also, what would the best command be to apply all available updates?  sudo apt-get upgrade?  Or sudo apt-get update?
when you get to the recovery section, you should be able to choose what kind of environment it is. choose "netroot" for networking support.
If you don't have it, just start networkmanager, dhcp, and networking from /etc/init.d

---

### Post by oldfred on 2010-08-20
I normally post this as part of a chroot. I thought the recovery had options to do most if not all the updates.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

