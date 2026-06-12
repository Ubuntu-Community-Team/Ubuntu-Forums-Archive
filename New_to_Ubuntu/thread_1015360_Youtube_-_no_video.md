---
title: "Youtube - no video"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by oopsHelp on 2008-12-18
Hi,

When I first went to Youtube I was presented with:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

I have checked the Java and it is on, and I went to Adobe and downloaded the Flash Player for Debian from the dropdown, but it is not working.

Any idea?

Thanks

---

### Post by taurus on 2008-12-18
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Now, restart firefox.

---

### Post by oopsHelp on 2008-12-18
Ok I just rebooted and it worked.

I thought you never had to reboot in Linux and you only had to do that in Windows.

---

### Post by donkyhotay on 2008-12-18
Try installing flash player from the ubuntu repositories.
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by donkyhotay on 2008-12-18
> **oopsHelp said:**
> Ok I just rebooted and it worked.

I thought you never had to reboot in Linux and you only had to do that in Windows.

Oops, someone beat me to it. Anyways, the only time you *must* reboot is when there are changes to the kernel. Any other changes can theoretically be reset without rebooting the entire machine by using telnit but practically it's usually just easier to reboot.

---

### Post by stchman on 2008-12-18
> **oopsHelp said:**
> Ok I just rebooted and it worked.

I thought you never had to reboot in Linux and you only had to do that in Windows.

Restarting Firefox is not the same as rebooting the PC.  You only have to reboot when you update the kernel.  Sometimes a workspace reboot is necessary (Ctrl-Alt-Bksp), but that is very quick.

---

