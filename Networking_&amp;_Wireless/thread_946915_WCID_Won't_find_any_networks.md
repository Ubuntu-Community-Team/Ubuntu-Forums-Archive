---
title: "WCID Won't find any networks"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2008-10-13
I was using gnome's network manager until today when I decided to try WICD.  After I Installed it, I rebooted, and now it will never find any wireless networks.  There are at least 10 around my area, none of which it finds.

Is there any way to fix this?  I'm using an Acer Aspire One if that helps, and I had networking all previously working.

---

### Post by pytheas22 on 2008-10-13
Are you sure that you specified the correct network interface name in wicd's preferences?  It may be set to use your ethernet interface, not the wireless, which would explain the problem.

If you're not sure what your interface name is, post the output of:
```

iwconfig
```

It's probably named 'wlan0', 'eth1' or 'ath0', depending on which wireless driver you use.

Also, to be sure that your computer is definitely still able to see networks, you can run the command:
```

sudo iwlist scan
```

which should produce a list of networks in range.  If it returns nothing, there's a problem at a lower level than wicd.

---

### Post by Hawk__0 on 2008-10-14
It is definitely ath0 (I was using it before as well, and it appears in the output of iwconfig)

sudo iwlist scan returned "interface doesn't support scanning" for all but ath0, which returned "No scan results"


EDIT:
After hours and even days of screwing around i got it to work.  I recompiled my drivers and everything located at the ubuntu documentation site for the aspire one.  I rebooted, nothing.  I did it again and nothing.  I booted into windows while i ate my dinner and surfed the net for a bit, booted back into linux and... well... there's the unexplainable part... it works.

---

### Post by pytheas22 on 2008-10-14
Glad to hear that it's fixed.  Some of the newer Atheros cards do require some hacking to get working in Hardy (although in Intrepid this should be an issue in most cases).  If you run into any other trouble, please let us know.

---

### Post by Epikuma24 on 2008-12-13
i know why it works "9 out of ten time restarting your computer will
fix any problem" readers digest

---

### Post by Mastermind1980 on 2009-05-17
Can you guys help me with my (similar) problem too please?
[http://ubuntuforums.org/showthread.php?p=7291722](http://ubuntuforums.org/showthread.php?p=7291722)

Thanks!

---

