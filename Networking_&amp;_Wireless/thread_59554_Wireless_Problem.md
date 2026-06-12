---
title: "Wireless Problem"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by uncle vernon on 2005-08-24
I have a Sony Vaio VGN-S260 running Hoary.  Most everything worked great on the default install (!!!!), save for the wireless card. It's an Intel Pro Wireless 2200BG using the IPW2200 driver.  It works at first, but if I let the machine idle for more than 10 minutes or so, it stops working and I can't bring it back to life without restarting  the machine.

I've tried all the obvious stuff, but to no avail.  I seem to remember having the same problem on an old Gentoo installation, and I think reloading the firmware fixed it, but I'm not sure how to do that with the pkg version of the driver.

Any ideas?

---

### Post by s_p_a_r_k_y on 2005-08-24
does taking the interface down and back up bring it to life?
```

ifconfig ethX down
ifconfig ethX up

```

or maybe forcing the kernel module out and back in?

---

