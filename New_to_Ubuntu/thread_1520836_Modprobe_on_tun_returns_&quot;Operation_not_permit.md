---
title: "Modprobe on tun returns &quot;Operation not permitted&quot;"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Chaser98 on 2010-06-30
Hi, I've been trying to  get tun working on my VPS, so I can run OpenVPN.

Of course when I run OpenVPN, access is denied for /dev/net/tun. So I've googled around for a while and found that I need to load tun via modprobe. So I tried that and here's the result:

```

root@3esfd:/etc/openvpn# sudo modprobe tun
FATAL: Error inserting tun (/lib/modules/2.6.18-164.2.1.el5.028stab066.10/kernel/drivers/net/tun.ko): Operation not permitted

```

Everything in that given drivers folder is chmodded to 777. So I don't know what's going on here.

Help would be appreciated.

---

### Post by okplayer02 on 2010-06-30
well one thing that is curious is this module from Red Hat Enterprise Linux? i notice in the error message and the kernel version. 


take a look at this thread post #25
[http://ubuntuforums.org/showthread.php?t=1459559&page=3](http://ubuntuforums.org/showthread.php?t=1459559&page=3)


did you build a module for your kernel specifically that would be better for sure.

---

### Post by Chaser98 on 2010-06-30
Thanks, okplayer. I am now able to modprobe it.

However, I still get my original error: ```
Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)

```

Note: I am running it as root, AND sudo

---

### Post by okplayer02 on 2010-06-30
are u running any other instance of like openvpn? 

reference this post from Ubuntu thread. 

[http://ubuntuforums.org/archive/index.php/t-1489221.html](http://ubuntuforums.org/archive/index.php/t-1489221.html)

read the entire thread and you will see there is an issue in regards to hosts end.

---

