---
title: "Atheros Card on Ubuntu Server x86_64"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2007-01-09
hi,

i am trying to use ubuntu on a 64bit box i have.
the card is a WG311T.
but i need to install wireless card on it.
i followed the instruction found on:

[b]
[http://ubuntuforums.org/showthread.php?t=38972]("http://ubuntuforums.org/showthread.php?t=38972")
[/b]
but it fails when compiling the driver, giving the following error:

$make

Checking requirements ...ok
Checking kernel configuration ...FAILED
Please enable wireless extensions.
make: *** [configcheck] Error 1

so it seems i need to enable wireless extensions, but i do not know how to go about it.

thanks in advance for your assistance.

regards

---

### Post by tturrisi on 2007-01-09
Debian:
apt-get install wireless-tools module-assistant madwifi-source madwifi-tools
m-a prepare
m-a a-i madwifi

Ubuntu:
how to install as well as how to build-install
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by nicolasdiogo on 2007-01-10
since i am using the Ubuntu server distribution i do not have gnome installed, so i will not be able to isntall the graphic tools.
i had a look at the madwifi website as well but it did not seems to work, giving me the same error messages.

thanks

---

### Post by tturrisi on 2007-01-10
> **nicolasdiogo said:**
> since i am using the Ubuntu server distribution i do not have gnome installed, so i will not be able to isntall the graphic tools.
i had a look at the madwifi website as well but it did not seems to work, giving me the same error messages.

thanks
What grahoic tools?  There's nothing graphical in what I posted!

---

### Post by tturrisi on 2007-01-10
In truth, all you need do is this:
linux-restricted-modules-$(uname -r) 
then reboot.

---

### Post by echeadle on 2007-01-10
Dumb question, but what encryption are you using.  None, WEP or WPA?

---

### Post by dlarr81 on 2007-01-11
> **tturrisi said:**
> In truth, all you need do is this:
linux-restricted-modules-$(uname -r) 
then reboot.

I am having a problem installing the modules.

uname -r = 2.6.17-10-server

Apt cannot find the modules with -server as a prefix.  I can find linux-restricted-modules-2.6.17-10-generic and install that, but it does not load when I boot to the server kernel.  Is there a way to get the server to load the generic modules?

---

### Post by tturrisi on 2007-01-11
try this:
apt-get install wireless-tools module-assistant madwifi-source madwifi-tools
m-a prepare
m-a a-i madwifi

---

