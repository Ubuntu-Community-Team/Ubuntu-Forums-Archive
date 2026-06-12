---
title: "How to boot with &quot;nohdparm&quot; option?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by alexazul on 2010-05-27
Short version: I don't know how to boot with the "nohdparm" boot option. Can someone tell me how?

Long version: I am trying to fix a sleep/suspend issue on my Samsung NC10. I'm running 10.04 and Windows. As part of this bug ([https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/340014](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/340014)), I've been told to bootup with the "nohdparm" boot option. So far, I've figured out how to call the command line in Grub2, but when I type "nohdparm," Grub2 tells me that it's an invalid command. This makes sense, as I've looked through the valid Grub2 commandline calls, and it's not one of them. I've searched everywhere I know (Google, these forums, Launchpad). There are many mentions of "nohdparm," but I cannot find a tutorial that tells me how to do use it. I'm new to Linux, obviously, and am doing my best to learn how it works, but I don't know where else to go with this problem. Thanks in advance for any help you guys can provide.

---

### Post by mikewhatever on 2010-05-27
In a terminal, run gksudo gedit /etc/default/grub
find the following line and add your boot option
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

example:
```
GRUB_CMDLINE_LINUX_DEFAULT="nohdparm quiet splash"
```
save and exit
Now update grub with **sudo update-grub**

---

### Post by alexazul on 2010-05-27
This was very helpful. Thank you.

---

