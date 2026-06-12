---
title: "'apt-get -f install' ?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-16
I just tried installing real player for Linux. When running

```
sudo dpgk -i RealPlayer11GOLD.deb
```

I got an error telling me I had broken dependencies, and told me to try 'apt-get -f install'. When I ran it, it seems like it installed 1000 packages or something. What did I just do?

---

### Post by Elep.Repu on 2009-07-16
> **m_ad said:**
> I just tried installing real player for Linux. When running

```
sudo dpgk -i RealPlayer11GOLD.deb
```I got an error telling me I had broken dependencies, and told me to try 'apt-get -f install'. When I ran it, it seems like it installed 1000 packages or something. What did I just do?

```
man apt-get
```
-f, --fix-broken

---

### Post by m_ad on 2009-07-16
> **Elep.Repu said:**
> ```
man apt-get
```
-f, --fix-broken

I guess my question is, why were they broken in the first place?

---

### Post by Elep.Repu on 2009-07-16
> **m_ad said:**
> I guess my question is, why were they broken in the first place?

That answer is a variable sir,
which depends on your own computer usage behavior.
Impossible for me to answer.

[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)

---

### Post by mcduck on 2009-07-16
> **m_ad said:**
> I guess my question is, why were they broken in the first place?

The realplayer package you installed probably had some dependencies, and since dpkg doesn't automatically install them the package was installed but broken.

Running "sudo apt-get -f install" then fixed the situation by installing the missing dependencies for your realplayer package.

---

### Post by philinux on 2009-07-16
> **m_ad said:**
> I just tried installing real player for Linux. When running

```
sudo dpgk -i RealPlayer11GOLD.deb
```

I got an error telling me I had broken dependencies, and told me to try 'apt-get -f install'. When I ran it, it seems like it installed 1000 packages or something. What did I just do?

You could have asked here first re realplayer. The easiest way is to enable medibuntu. Click link below for info. Realplayer is then available in synaptic or add/remove. No dependency problems this way.

Forget windows ways of downloading stuff from the net.

---

### Post by bodhi.zazen on 2009-07-16
> **philinux said:**
> Forget windows ways of downloading stuff from the net.

+1

In addition to some the the dependency issues, installing packages from untrusted sources is a security risk.

---

### Post by m_ad on 2009-07-16
Thank you guys.

---

### Post by Jeff250 on 2009-07-16
Use:
```
sudo gdebi foo.deb
```
...instead of:
```
sudo dpkg -i foo.deb
```
...if you want to automatically install dependencies of a local .deb package.

---

