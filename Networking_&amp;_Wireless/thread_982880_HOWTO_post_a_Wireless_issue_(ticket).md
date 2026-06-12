---
title: "HOWTO post a Wireless issue (ticket)"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by gnusci on 2008-11-15
Please take a while for the **title** of the thread. Do not write things like "Help wireless" and "Can't wireless". Think a little bit more, a good title can increase the chances to get help. For instance, add the **Wireless brand**/**Ubuntu version**/**Machine Brand and Model**.

Please, provide details about you Wireless. The diagnoses of your problem can be easer and the solution faster.

Here is a list of Wireless related information with their respective commands. Some commands give you a lot of output, so will be nice to include in the post only the information regarding the Wireless. You can cut it or use tools like **grep**, or whatever you like.

**1 ) Machine Brand and Model (PC/Laptop)**:
```
Get it from your product information.
```

**2 ) Wireless Brand, Model and Wireless Chipset:**
```
$ lspci
$ lsusb
```
([COLOR=Red]hint[/COLOR]) use **grep** to get only information about the Wireless
```
$ lspci -nn | grep 'Wireless Brand'
```

**3 ) check interface:**
```
$ ifconfig
$ iwconfig
```
([COLOR=Red]hint[/COLOR]) if the Wireless interface name is wlan0 you can also use
```
$ iwconfig wlan0
```

**4 ) Check for modules:**
```
$ lsmod
```
([COLOR=Red]hint[/COLOR]) search for the Wireless module
```
$ lsmod | grep "wlan_module_name"
```

**5 ) Kernel boot messages**
```
$ dmesg
```
([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
```
$ sudo lshw -C network
```

**7 ) Scan for networks:**
```
$ iwlist scan
```
([COLOR=Red]hint[/COLOR]) the same as in (3)
```
$ sudo iwlist wlan0 scan
```

**8 ) Ubuntu Version: **
```
$ lsb_release -d
```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
$ uname -mr
```

**10 ) Restarting the network:**
```
$ sudo service networking restart
```

Add this information to the post, even is the output is and error, and more if you have, and describe your issue. Please use CODE tags around the output when posting.

---

