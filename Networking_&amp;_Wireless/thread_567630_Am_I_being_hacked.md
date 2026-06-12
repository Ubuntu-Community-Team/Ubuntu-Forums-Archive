---
title: "Am I being hacked?"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by kelbizzle on 2007-10-04
Am I being hacked? I've included a screenshot of the ip and port. 
rkhunter also reports
```

[20:05:25] Performing filesystem checks
[20:05:25] Info: Starting test name 'filesystem'
[20:05:25] Info: SCAN_MODE_DEV set to 'THOROUGH'
[20:06:24]   Checking /dev for suspicious file types         [ None found ]
[20:06:25]   Checking for hidden files and directories       [ Warning ]
[20:06:25] Warning: Hidden directory found: /dev/.static
[20:06:25] Warning: Hidden directory found: /dev/.udev
[20:06:25] Warning: Hidden directory found: /dev/.initramfs

```

```

kelbizzle@hoodbocks:~$ users
kelbizzle kelbizzle kelbizzle

```

Am I logged in 3 times?

---

### Post by ofir_k on 2007-10-04
It's weird...

If I type 'users' in the terminal, I get my username displayed twice. Thats it normal?

---

### Post by odiseo77 on 2007-10-04
I also get this hidden files/directories inside /dev when running rkhunter, even on a fresh install, so I guess they're system's files (not sure what they're for, though).

About the 'users' output, I'm not sure at all, try 'who' (you'll probably see the same users 3 times, but in a more explanatory way)... maybe you have some virtual console opened and that's why you're getting the same user 3 times?

Regards.

---

### Post by ofir_k on 2007-10-04
> **odiseo77 said:**
> I also get this hidden files/directories inside /dev when running rkhunter, even on a fresh install, so I guess they're system's files (not sure what they're for, though).

About the 'users' output, I'm not sure at all, try 'who' (you'll probably see the same users 3 times, but in a more explanatory way)... maybe you have some virtual console opened and that's why you're getting the same user 3 times?

Regards.

You are right, this is a console issue.

When I type 'who' in the console I get two users:
1. Me
2. The console
I can see it by the displayed hour!

---

### Post by odiseo77 on 2007-10-04
Yeah, I guess it's a virtual console opened; just pressed ctrl-alt-F1 and logged in as my user, then went back to the GUI typed 'users' and 'who' in a terminal and got this:

```
vicente@ubuntu-box:~$ users
vicente vicente vicente
vicente@ubuntu-box:~$ who
vicente  tty1         2007-10-04 21:52
vicente  :0           2007-10-03 21:10
vicente  pts/0        2007-10-04 21:52 (:0.0)
vicente@ubuntu-box:~$
```

Greetings! :)

---

