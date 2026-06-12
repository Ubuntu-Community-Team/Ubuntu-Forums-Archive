---
title: "Disable Network-manager notifications or Network-manager"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-01-09
I'm setting up a computer for some new Ubuntu users, and I want it to be as simple as possible. They use DSL via ethernet, so they are always connected and really have no need for Network-Manager. However, I'm not sure how to configure Ubuntu for DHCP without Network-Manager. 

My question is how do I get rid of the notification when a user logs in that says "The wired connection is now connected" (it might differ slightly)? Removing Network-manager would be fine as well. 

I checked gconf-editor and couldn't find anything for NM. 

Thanks for the help.

---

### Post by hyper_ch on 2009-01-09
well, I'd replace the default network manager with WICD then you shouldn't get those messages anymore.

---

### Post by aheckler on 2009-01-09
Go into **System > Preferences > Sessions** and uncheck Network Monitor. That does the trick for me.

---

### Post by zika on 2009-01-09
> **jbrown96 said:**
> However, I'm not sure how to configure Ubuntu for DHCP without Network-Manager. 

> **aheckler said:**
> Go into **System > Preferences > Sessions** and uncheck Network Monitor. That does the trick for me.
these two messages miss one thing in order not to be contradicting each other:```
 **gksudo gedit /etc/network/interfaces **
```... ;)

it should look something like (get the right numbers from **ifconfig** while You have working connection) (remove "#" in lines You want active (depending You want DHCP or static IP)):

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
#auto eth0
#iface eth0 inet dhcp

# The primary network interface static
#auto eth0
#iface eth0 inet static
#   address ***.***.***.***
#   netmask ***.***.***.***
#   gateway ***.***.***.***  
#   broadcast ***.***.***.***
 
```

to **jbrown96**:since You want just DHCP You could go with:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```

---

