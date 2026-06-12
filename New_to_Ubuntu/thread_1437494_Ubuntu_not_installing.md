---
title: "Ubuntu not installing"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by cityydude on 2010-03-24
**I figured out what the problem was.  I seems the one system does not like to read the CD burned on the other system. I swapped out the CD drives so its reading from the same one it was burned on. That solved the problem and the system was installed.**
  ** **
  **However I ran into a few other problems after the installation was complete. I installed Apache, Mysql and Php5 just fine.  But in order to make the system more secure I needed to change a few settings in each of these systems. I was able to change the php5 :**
  ** **
  **expose_php =on to off just fine.**
  ** **
  **But I was not able to locate the two settings I needed to change in apache. I need to change these two settings:**
  ** **
  **ServerTokensFull to ServerTokensProd **
  **ServerSigatureOn to ServerSignatureOff**
  ** **
  **I tried searching for these strings but nothing came up. Any idea where to find these settings and how to change them?**
  ** **
  **I then tried to install the firewall as per these instructions:**
  ** **
  **Sudo aptitude install shorewall**
  ** **
  **But it comes back saying it cannot find this file to install it. Any idea where it’s supposed to be or has it been replaced by some other firewall program?**
  ** **
  **Any help with these problems would be appreciated.**
  ** **
  **Thanks.**

---

### Post by wojox on 2010-03-24
You'll find 
[B]
ServerTokensFull to ServerTokensProd
ServerSigatureOn to ServerSignatureOff
[/B]

```
cd /etc/apache2/conf.d
```

```
sudo nano security
```

As far as a firewall, **UFW** is installed it just needs to be enabled.

[uhelp]community/UFW[/uhelp]

---

