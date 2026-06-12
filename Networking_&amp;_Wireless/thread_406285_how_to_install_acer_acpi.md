---
title: "how to install acer_acpi?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by notsteve on 2007-04-10
dose anyone have any idea how to install acer_acpi, i tried to follow the other how to"http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi" but it's out of date, so i downloaded it and i'm having a hell of a time trying to install it, can anyone help?

---

### Post by archernar on 2007-04-14
Depending on which version of Ubuntu you're using, the problem may be that the version in that howto post is too old.  Follow the instructions at [http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi]("http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi"), but get version 0.4 from [http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/") instead of using wget, and change all the 0.3 references in the build instructions to 0.4, i.e. :

```
tar zxvf acer_acpi-0.4.tar.gz
cd acer_acpi-0.4
make
sudo make install
cd ../..
```

Instead of setting up an init script, I create a file called /etc/modprobe.d/acer-network, containing the following:

```
install bcm43xx /sbin/modprobe acer_acpi >/dev/null 2>&1; echo "enabled : 1" >/proc/acpi/acer/wireless; /sbin/modprobe --ignore-install bcm43xx

```

(you may need to change bcm43xx to another module if you have a different network card, or are using ndiswrapper).  Then, when the network card driver loads, acer_acpi is enabled automatically.

---

