---
title: "No Wireless - D830 - bcm43xx"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by flyeng4 on 2008-06-03
I have a Dell D830 with a Broadcom BCM4310(rev01) wireless card that is not being seen. I have been trying different methods for days and need some help.  The fix that seems to be getting most people up is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").
This did not work for me. When I got to the ndiswrapper -l step here was the output:
```

william@william-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!

```

Here is some more info that might be usefull.
```

william@william-laptop:~$ lspci | grep 'Broadcom'
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

```

william@william-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

william@william-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Any info will be extremely appreciated. Thanks in advance.

Oh, yeah, and I am using Gutsy.

---

### Post by Ayuthia on 2008-06-03
You might want to try this out:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)
This one seems to work for some 4310 cards. You will most likely need to use the driver in step 0 and make sure that you do step 2. That seems to be the helping factor.

---

### Post by flyeng4 on 2008-06-04
That did it. Thanks a million!!!

---

