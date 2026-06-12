---
title: "No wireless on my Acer 5520 w/Ubuntu 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by TommyIndep on 2008-10-30
Hello all!

After having no luck with getting wireless to work properly with Ubuntu 8.04, I was really having high hopes for 8.10, now that I've downloaded though, I don't have any wireless whatsoever! I have an Acer 5520 with a broadcom bcm4311 wirless card, and no matter which driver I enable in "hardware drivers", I can't seem to get wireless working, so please, can anybody help me?

---

### Post by ahlenius on 2008-11-01
Hi there.

I my self have a Acer Aspire 5021 with a Broadcom bcm4318 and Ubuntu 8.10 and have experience the same problem. But now i'm using the wireless to connect to the world.

My solution to activate the wireless card is by using the following code:
```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```

And to make sure it's always activated when I start-up I added that line to the /etc/rc.local file, by opening a editor ```
sudo gedit /etc/rc.local
``` so it's locks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo echo 1 > /sys/devices/platform/acer-wmi/wireless
exit 0
```

I hope it helps you to.

---

### Post by TommyIndep on 2008-11-04
> **ahlenius said:**
> Hi there.

I my self have a Acer Aspire 5021 with a Broadcom bcm4318 and Ubuntu 8.10 and have experience the same problem. But now i'm using the wireless to connect to the world.

My solution to activate the wireless card is by using the following code:
```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```

And to make sure it's always activated when I start-up I added that line to the /etc/rc.local file, by opening a editor ```
sudo gedit /etc/rc.local
``` so it's locks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo echo 1 > /sys/devices/platform/acer-wmi/wireless
exit 0
```

I hope it helps you to.



Hi ahlenius! And thanks for trying to help me, after I ran those commands my wireless light lit up, although no access points showed up when I clicked the NetworkManager icon. Perhaps if I try a clean install of Intrepid Ibex it'll work, I've done quite a lot of tweaking, without any luck though.

Thanks again! :)

---

### Post by gcalpacket on 2009-02-05
> **ahlenius said:**
> Hi there.

I my self have a Acer Aspire 5021 with a Broadcom bcm4318 and Ubuntu 8.10 and have experience the same problem. But now i'm using the wireless to connect to the world.

My solution to activate the wireless card is by using the following code:
```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```

And to make sure it's always activated when I start-up I added that line to the /etc/rc.local file, by opening a editor ```
sudo gedit /etc/rc.local
``` so it's locks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo echo 1 > /sys/devices/platform/acer-wmi/wireless
exit 0
```

I hope it helps you to.

hey ahlenius,

thanks a ton man.....me and my roomie had big trouble trying to activate wirless button and your post madeour life so easy.........3 cheers man...ta:popcorn:

---

### Post by dark_333 on 2009-02-11
> **ahlenius said:**
> Hi there.

I my self have a Acer Aspire 5021 with a Broadcom bcm4318 and Ubuntu 8.10 and have experience the same problem. But now i'm using the wireless to connect to the world.

My solution to activate the wireless card is by using the following code:
```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```

And to make sure it's always activated when I start-up I added that line to the /etc/rc.local file, by opening a editor ```
sudo gedit /etc/rc.local
``` so it's locks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo echo 1 > /sys/devices/platform/acer-wmi/wireless
exit 0
```

I hope it helps you to.


thks, it worked perfectly for me

---

