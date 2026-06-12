---
title: "Intel wireless 7260 unrecognized on ASUS Q502L"
date: 2014-10-02
forum: Networking &amp; Wireless
---

### Post by ct95 on 2014-10-02
Hi. Intel wireless 7260 rev cb chip is totally unrecognized on my laptop ASUS Q502L, no wireless available at all. I'm running XUbuntu 14.04 with latest updates, kernel 3.15.0-031500-generic. Intel firmware is version 9. Does anybody have an idea on how to make it work? Thanks in advance.

```

carlo@ct-lap:~$ iwconfig
eth0     no wireless extensions.
lo        no wireless extensions.

```

---

### Post by Michael_McKenney on 2014-10-02
[http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

---

### Post by jeremy31 on 2014-10-02
> **ct95 said:**
> Hi. Intel wireless 7260 rev cb chip is totally unrecognized on my laptop ASUS Q502L, no wireless available at all. I'm running XUbuntu 14.04 with latest updates, kernel 3.15.0-031500-generic. Intel firmware is version 9. Does anybody have an idea on how to make it work? Thanks in advance.

```

carlo@ct-lap:~$ iwconfig
eth0     no wireless extensions.
lo        no wireless extensions.

```

Can you run the wireless script from the sticky post ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]I might have to look at some month old posts by Chili555 as that chipset might not be included in iwlwifi

EDIT: You seem to have the same chipset as in Chili's post here: [http://ubuntuforums.org/showthread.php?t=2242147&p=13112184#post13112184](http://ubuntuforums.org/showthread.php?t=2242147&p=13112184#post13112184)

Follow the instructions and your wifi should work

---

### Post by ct95 on 2014-10-04
That's it, problem solved! This is the solution, requires 10 minutes to do it: [http://ubuntuforums.org/showthread.php?t=2242147&page=2&p=13112184#post13112184](http://ubuntuforums.org/showthread.php?t=2242147&page=2&p=13112184#post13112184)
Thanks to all and specially to jeremy31 for pointing out the solution ;). The wireless script is also very useful stuff.

---

