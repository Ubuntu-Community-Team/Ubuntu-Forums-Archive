---
title: "Upgrade not working right. Help needed"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Jay Rutherford on 2009-09-06
Apologies for the lengthy post...

I had a PC with Ubuntu 8.04 running. I changed internet technologies and now need a wireless card instead of wired, so currently have no internet access with this machine. I have the wireless card but can't figure out how to install the driver.

I decided to do an upgrade to 8.10 and then to 9.04, which has native support for the wireless card (Realtek 8187). I did the upgrade to 8.10 with Alternate Install and it seems to have gone correctly, except that the About Ubuntu does not recognize the version, and inserting the Alternate Install 9.04 CD will not automatically go into upgrade mode, like the 8.10 CD did.

About Ubuntu says, "Our first release (Warty Warthog) was in October 2004 so its version was 4.10. This version () was released in so its version number is ."

lsb_release -a results in:

Distributer ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       Intrepid

So, terminal thinks I'm running 8.10 but About Ubuntu has no idea. Any suggestions where to look? I want to do the upgrade to preserve my settings and files if at all possible.

Thanks. Jay

---

### Post by cariboo on 2009-09-06
THe upgrade probably hasn't been completed. Open a terminal and type:

```
sudo apt-get -f install
```

This should finish the upgrade.

---

### Post by Jay Rutherford on 2009-09-06
I tried that just now. Results were:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

It returned this information very quickly, and it doesn't look like it did anything. I see no difference in behavior.

Jay

---

