---
title: "&quot;Connect to Server...&quot; seriously buggy in 7.04 Feisty"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-05-22
When trying to do a remote login via SSH using Ubuntu's "Connect to Server...", the desktop icons (and corresponding menu shortcut in "Places") rarely appears upon creation. If the shortcuts do appear, quite often Ubuntu hangs on "Connecting to Server..." or shows nothing at all in indication of what went wrong.

If the shortcuts don't appear, "killall nautilus" is insufficient so a reboot is in order. Once the shortcuts finally appear, the have little to no functionality as described above.

I've used an upgrade and a fresh install of 7.04 Feisty, so please don't tell me this has to do with any of my configuration files.

---

### Post by gwm on 2007-06-04
Similar problem - now fixed. Perhaps my fix can help you track down your problem. I wrote a whole essay about it here:

[http://ubuntuforums.org/showthread.php?p=2778127#post2778127](http://ubuntuforums.org/showthread.php?p=2778127#post2778127)

:popcorn:

---

### Post by altonbr on 2007-06-04
Yeah, but since you don't even know what ./.ssh/known_hosts is, I'm going to assume that my problem is with Nautilus and not with ssh. Uninstalling the libraries does nothing when your RSA keys are conflicting and I already know the method of deleting the known_hosts file... That isn't my complaint. My complaint is that there is a bug with Nautilus not places shortcuts on the desktop and not giving me an error message.

I made a more formal complaint in the Gusty Idea Pool: [http://ubuntuforums.org/showthread.php?t=457332](http://ubuntuforums.org/showthread.php?t=457332)

---

