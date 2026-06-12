---
title: "D-Link DWL-122"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by stkaplan on 2005-07-06
I'm having problems getting my D-Link DWL-122 adapter working in Ubuntu. I've seen other posts where people have gotten this adapter to work, but they don't work for me. (For example, [http://ubuntuforums.org/showthread.php?t=4041](http://ubuntuforums.org/showthread.php?t=4041) )

The problem is that I simply don't have a wlan0 interface. I installed the linux-wlan-ng package, but that didn't seem to do anything. I don't see any mention of the adapter anywhere in my dmesg, either.

I read that this adapter will work with linux-wlan-ng version 0.2.1pre13 or later. Ubuntu includes version 0.2.0+0.2.1pre21 and I have no idea what this means. Does this mean that both versions are installed together? Or some mix of both versions?

---

### Post by ranf on 2005-07-06
What do you get when you open a terminal and type:
```
lsusb
```

---

### Post by stkaplan on 2005-07-07
One of the lines from lsusb is

```
Bus 002 Device 002: ID 2001:3704 D-Link Corp. [hex]
```

---

### Post by ranf on 2005-07-07
[QUOTE=stkaplan]One of the lines from lsusb is
```
Bus 002 Device 002: ID 2001:3704 D-Link Corp. [hex]
```[/QUOTE]
Oops, I get "2001:3700" as ID. Yours seems to be some newer(?) brand.
What's the output of ```
sudo /etc/init.d/wlan start
```

---

### Post by stkaplan on 2005-07-07
I actually got this to work with ndiswrapper, after I gave up on the linux-wlan-ng drivers. It works fine now. 

"sudo /etc/init.d/wlan start" gave me an error when the adapter wasn't working, but I don't remember what it was, and it's probably not worth it to figure it out.

---

