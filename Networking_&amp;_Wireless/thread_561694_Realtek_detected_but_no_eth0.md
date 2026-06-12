---
title: "Realtek detected but no eth0"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Nha-Krul on 2007-09-27
Hello. I have changed my old network card by a hardware fault. After the change I could not use the network anymore.
If I run the lspci command, I can see that the system detect the new Realtek 8139 network card. Using modconf I installed 8139cp and 8139too driver without any problem. But I can't find the eth0 to use. I have ran the system administrator under gnome and there is the Network card, but no eth0. When I use the ifconfig command there is the local loop and my 2 vmware virtual network boards. I think that the OS is doing the hardware autodetect at the start time, but I relly not sure.

Thanks for the help

---

### Post by blu3ness on 2007-09-27
Not sure if you have similar problem as me
but check out 
[http://ubuntuforums.org/showthread.php?t=561556](http://ubuntuforums.org/showthread.php?t=561556)

I found a fix by modifying a configuration file in 
/etc/network/interfaces

---

### Post by Nha-Krul on 2007-09-28
Thanks for your help. I saw in the forum that some people have the same problem after update  some package. So maybe I have this problem and that´s why when I bought the new network card the OS did not start the network. I have to try your solution, but I do not know the new MAC address to add it in the /etc/network/interfaces. My original idea was to dpkg-reconfigure some pakage, from the ubuntu-minimal, to autodetect my hardware again,but i do not know wich one.  if the problem is the updated package I don´t  know how to return and what package I have to downgrade.

Thanks again

Sorry for my bad english, I´m from argentina and I am out of practice

---

### Post by noob12 on 2007-09-28
Run this and see if it is there with a different logical name, perhaps eth1.  
Unless it is UNCLAIMED, the driver should be listed in the configuration line.
```

sudo lshw -C network

```

See if it shows up in this:
```

ifconfig -a

```

If it shows up, you can get it to be renamed eth0 by editing the **/etc/iftab** and associating eth0 to the HWAddr MAC address seen in the above and rebooting.

Check that there is link detected  (use the appropriate interface name that you find)
```

sudo ethtool eth1

```

---

