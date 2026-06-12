---
title: "After upgrade to 9.04 internet connection disappear"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by colormoon on 2009-05-07
I used xubuntu 8.10 and I upgrade to 9.04. After that the internet connection cannot use. What should I do?
Thank you.

---

### Post by Saghaulor on 2009-05-07
Try this first
```
ifconfig
```

Hopefully it will list an interface such as 'eth0' or 'wlan0'.

If it does, the interfaces is still there. But it's not working?

If it's a wired connection, it may be as simple as the following
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

Assuming 'eth0' is the name of your wired ethernet interface.

You can also try 
```
route
```

That will list the iptables that are currently active. You should see the ip address of your gateway interface under the 'destination' and 'gateway' columns and the name of your ethernet device to the far right under the 'Iface' column.

If you're seeing all that, you should be connecting to the internet.

Btw, I would recommend doing clean installs rather than upgrades. Upgrades are often sloppy and things go awry.

---

### Post by colormoon on 2009-05-07
Thank you for reply
I will try follow your instruction. And I'll report after that.

---

### Post by colormoon on 2009-05-07
I follow your instruction but it doesnot work. Maybe I should install 8.10 again. 
I cannot use 9.04 because it show me a bug on booting linux image. Ubuntu 9.04 use linux image 2.6.28-11 that my computer is not afford but linux image 2.6.27 on ubuntu 8.10 is work.
Thank you

---

