---
title: "Software index is broken"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by huiprobable on 2011-04-22
I've encountered a problem with Package Manager, it gives me the following error message: 
[B][I]Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/I][/B]

Furthermore, I can't open Synaptic, it says: 
[B][I]Another synaptic is running
There is another synaptic running in non-interactive mode. Please wait for it to finish first.[/I][/B]

If I type** *sudo apt-get install -f*** in the terminal, I get the following error message:
[B][I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I][/B]
I don't know what to do. Can anyone help me on this?

---

### Post by drs305 on 2011-04-22
Normally this means you have another package manager open (such as a second Synaptic). If you do, close it and try again. If you don't see any, you can try ALT-TAB, which will cycle through your open apps.

From a terminal, you could also run "ps -u root" to see if you can spot any likely candidates that might be open. If you find one listed, you could try to close it with "sudo killall xxx" with xxx being the running app's name.

If all else fails, you can just try shutting down normally and rebooting. Hopefully that will remove any locks on the Ubuntu package managers.

---

### Post by huiprobable on 2011-04-22
by the way, restart doesn't fix the problem.

---

### Post by huiprobable on 2011-04-22
Thank you very much! Yes, I killed the process synaptics, and used the broken filter to remove a broken package. The problem is solved. I'm so happy. :D



> **drs305 said:**
> Normally this means you have another package manager open (such as a second Synaptic). If you do, close it and try again. If you don't see any, you can try ALT-TAB, which will cycle through your open apps.

From a terminal, you could also run "ps -u root" to see if you can spot any likely candidates that might be open. If you find one listed, you could try to close it with "sudo killall xxx" with xxx being the running app's name.

If all else fails, you can just try shutting down normally and rebooting. Hopefully that will remove any locks on the Ubuntu package managers.

---

