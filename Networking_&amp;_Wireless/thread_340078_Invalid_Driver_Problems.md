---
title: "Invalid Driver Problems"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Helgeland on 2007-01-16
ok, I was trying to install the drivers for my gigabyte technology gn-wp01gs, using ndiswrapper, from the disk that came with it. i copied the .inf, .sys, and .bin folders to /home/drivers/ from the Winx64 folder on the disk. I think I should have used the files in the xp2k folder instead because when i tried to install those drivers i got an "invalid driver" error.  so i tried to uninstall the driver i had just installed and here's what it looks like... lol, how do you explain this?

```
andrew@andr3wz-CPU:~$ ndiswrapper -l
Installed drivers:
rt61    invalid driver!
andrew@andr3wz-CPU:~$ ndiswrapper -e rt61.inf
Driver rt61.inf is not installed.Use -l to list installed drivers
andrew@andr3wz-CPU:~$ ndiswrapper -i /home/drivers/rt61.inf
rt61 is already installed. Use -e to remove it
andrew@andr3wz-CPU:~$ ndiswrapper -e /home/drivers/rt61.inf
Driver /home/drivers/rt61.inf is not installed.Use -l to list installed drivers
andrew@andr3wz-CPU:~$ ndiswrapper -l
Installed drivers:
rt61    invalid driver!

```

---

### Post by Helgeland on 2007-01-16
never mind... sorry to waste your time. still having difficulties getting wireless to work though

---

