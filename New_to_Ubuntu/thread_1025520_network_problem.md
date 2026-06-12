---
title: "network problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by ET! on 2008-12-30
im using intrepid ibex (32-bit version).the problem is that every time the system is rebooted the previous lan settings get reset.so i need to manually reconfigure the connection every time...how do i get to save the configuration???:confused:

---

### Post by ET! on 2008-12-30
bump

---

### Post by Big_astur on 2008-12-30
If you are trying to use a static ip, what i did was change the network manager to wicd.

You can get the .deb from here: [http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=521838](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=521838)
Then uninstall the one installed ```
sudo apt-get remove network-manager --purge
```
Now install the .deb u downloaded and just configure it.

You can wait a bit for other answers.

---

### Post by albinootje on 2008-12-30
> **ET! said:**
> im using intrepid ibex (32-bit version).the problem is that every time the system is rebooted the previous lan settings get reset.so i need to manually reconfigure the connection every time...how do i get to save the configuration???:confused:

Try wicd : [http://wicd.sf.net](http://wicd.sf.net) instead of Network Manager.

---

### Post by zika on 2008-12-30
> **ET! said:**
> im using intrepid ibex (32-bit version).the problem is that every time the system is rebooted the previous lan settings get reset.so i need to manually reconfigure the connection every time...how do i get to save the configuration???:confused:

make Your /etc/network/interfaces file look like:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP (uncomment next two lines if You want DHCP)
#auto eth0
#iface eth0 inet dhcp

# The primary network interface static (uncomment next lines if You want static address)
#auto eth0
#iface eth0 inet static
#address ***.***.***.***
#netmask ***.***.***.***
#gateway ***.***.***.***
#broadcast ***.***.***.***

```command for changing this file is, for example:
```
sudo nano /etc/interfaces
```also check if Your /etc/resolv.conf has a line with "nameserver ***.***.***.***" in it ... (***.***.***.*** here should stand for Your router or for DNS of Your provider or for OpenDNS or ...)

do not remove NetworkManager because You might have problems when upgrade comes. this way he will stay out of the loop and once You get Your connection to be OK You can just disable it in System->Preferences->Sessions by un-checking his entry.

---

### Post by albinootje on 2008-12-30
> **zika said:**
>  do not remove NetworkManager because You miight have problems when upgrade comes.

NetworkManager is no longer a dependency on ubuntu-desktop in 8.10 (and also 8.04 afair), so you can safely do :
```

sudo apt-get remove --purge network-manager

```
And then either use wicd, or use plain /etc/network/interfaces depending on the situation and/or taste.

---

### Post by zika on 2008-12-30
> **albinootje said:**
> NetworkManager is no longer a dependency on ubuntu-desktop in 8.10 (and also 8.04 afair), so you can safely do :
```

sudo apt-get remove --purge network-manager

```And then either use wicd, or use plain /etc/network/interfaces depending on the situation and/or taste.

thank You for the correction. I'm cautious by nature ... ;)

---

