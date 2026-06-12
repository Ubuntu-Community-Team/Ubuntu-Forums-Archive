---
title: "Need help changing Ethernet configuration"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by Catsworth on 2007-03-16
Hey Guys,

Whenever I boot Ubuntu it hangs half way through the boot process, waits a few minutes, then continues.

I'm almost 100% sure this is because my ethernet adaptor is sending DHCP requests, but it isn't plugged in to anything that can satisfy them.

For that reason I would like to accomplish the following:

1.  Delete any configuration information for the ethernet adaptor (gateway, DNS, etc) and set it to do a DHCP request on boot to gain all that information (I *think* that some of this information may have already been set to fixed values).

2.  Permenantly disable the ethernet adaptor, and prevent it from being started at boot (I know I can do *sudo eth0 down* but I want it always to be disabled and only to be re-enabled when I specifically choose).

3.  Create a script that I can click on from within a menu that will bring the ethernet adaptor up and start the DHCP request process.

Any help with the above would be gratefully received.

Thanks.

---

### Post by louis_nichols on 2007-03-16
You can do all that under System>Administration>Networking. There, every network card has a check box called "enabled". If you uncheck that, the card won't be activated at startup. Then, to activate it manually, just go to that menu option again, select the card and click "Activate".

---

### Post by Catsworth on 2007-03-16
Hmmm.....

I'm sure I must have tried that but it didn't seem to have the desired result.....I'll take another look though - thanks.

---

### Post by dbott67 on 2007-03-16
> **Catsworth said:**
> Hey Guys,

Whenever I boot Ubuntu it hangs half way through the boot process, waits a few minutes, then continues.

I'm almost 100% sure this is because my ethernet adaptor is sending DHCP requests, but it isn't plugged in to anything that can satisfy them.

For that reason I would like to accomplish the following:

1.  Delete any configuration information for the ethernet adaptor (gateway, DNS, etc) and set it to do a DHCP request on boot to gain all that information (I *think* that some of this information may have already been set to fixed values).

2.  Permenantly disable the ethernet adaptor, and prevent it from being started at boot (I know I can do *sudo eth0 down* but I want it always to be disabled and only to be re-enabled when I specifically choose).

3.  Create a script that I can click on from within a menu that will bring the ethernet adaptor up and start the DHCP request process.

Any help with the above would be gratefully received.

Thanks.

My solutions may not be elegant, but they will certainly show you where the specific settings are stored.

For #1, all DHCP configuration settings are stored in a file called **/etc/dhclient.conf**.  This file determines what settings are requested from the DHCP server, etc.

The actual assigned settings to a specific interface are stored in **/var/lib/dhcp3/dhclient.leases**: 
```
dbott@thedrake:/var/lib/dhcp3$ cat dhclient.leases
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 604800;
  option routers 192.168.1.1;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  renew 2 2007/3/20 00:47:03;
  rebind 4 2007/3/22 18:32:22;
  expire 5 2007/3/23 15:32:22;
}
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.1;
  option domain-name-servers 192.168.1.1;
  renew 1 2007/3/19 16:24:00;
  rebind 4 2007/3/22 18:34:20;
  expire 5 2007/3/23 15:34:20;
}
```

You could always delete this file.

For #2, you can also do this:
```
dbott@thedrake:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR=Red]**# **[/COLOR]auto eth0 [COLOR=Blue]*<--- add a # to the beginning of this line to disable automatic configuration*[/COLOR]
iface eth0 inet dhcp
```

For #3, you could:
1. Create a file:
```
nano ~/network.sh
```
2. Add the following lines:

```
#!/bin/bash
sudo ifup eth0 
sudo dhclient eth0
```

3. Save it.

4. Make it executable:
```
chmod +x network.sh
```

5. Run it as desired:
```
dbott@thedrake:~$ ./network.sh
ifup: interface eth0 already configured
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 262180 seconds.
```

Hope this helps.

-Dave

---

### Post by Catsworth on 2007-03-16
Thanks Dave, I'll give that a go.

---

### Post by darkborg on 2007-04-01
> **dbott67 said:**
> My solutions may not be elegant, but they will certainly show you where the specific settings are stored.

For #1, all DHCP configuration settings are stored in a file called **/etc/dhclient.conf**.  This file determines what settings are requested from the DHCP server, etc.

The actual assigned settings to a specific interface are stored in **/var/lib/dhcp3/dhclient.leases**: 
```
dbott@thedrake:/var/lib/dhcp3$ cat dhclient.leases
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 604800;
  option routers 192.168.1.1;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  renew 2 2007/3/20 00:47:03;
  rebind 4 2007/3/22 18:32:22;
  expire 5 2007/3/23 15:32:22;
}
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.1;
  option domain-name-servers 192.168.1.1;
  renew 1 2007/3/19 16:24:00;
  rebind 4 2007/3/22 18:34:20;
  expire 5 2007/3/23 15:34:20;
}
```

You could always delete this file.

For #2, you can also do this:
```
dbott@thedrake:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR=Red]**# **[/COLOR]auto eth0 [COLOR=Blue]*<--- add a # to the beginning of this line to disable automatic configuration*[/COLOR]
iface eth0 inet dhcp
```

For #3, you could:
1. Create a file:
```
nano ~/network.sh
```
2. Add the following lines:

```
#!/bin/bash
sudo ifup eth0 
sudo dhclient eth0
```

3. Save it.

4. Make it executable:
```
chmod +x network.sh
```

5. Run it as desired:
```
dbott@thedrake:~$ ./network.sh
ifup: interface eth0 already configured
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 262180 seconds.
```

Hope this helps.

-Dave



Dave,

Your answer is awesome I have the same issue let me explain,
I have wrt54g linksys using wpa and dhcp...I been told
dhcp does not like wpa but for me is fine, now I do have
to restart manually the interface every time I restart my laptop,
any ideas how can I load your awesome script during the boot process?
Sounds kind of lazy, but hey scripts are designed to make our job much easier!

Thanks!

---

### Post by dbott67 on 2007-04-01
You can add the script (any program, for that matter) to the "Sessions" applet in "Preferences (**SYSTEM > PREFERENCES > SESSIONS**).

Click on the **STARTUP** tab and add the script there.

-Dave

---

