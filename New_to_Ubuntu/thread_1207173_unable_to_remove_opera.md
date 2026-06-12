---
title: "unable to remove opera"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by tchoklat on 2009-07-07
I have opera installed opera alpha (installed with opera-10.00-4102.gcc4-qt4.i386). I want to remove it but cannot. It does not appear in synaptic and the -
<~$ sudo dpkg -r opera> command has no effect.

I am wanting to do this to install the newer beta version which installs and removes through gdebi but when I start it from terminal the earlier 10.00.4102 version starts not the newer beta version.

any thoughts?

---

### Post by wojox on 2009-07-07
Enter this into the terminal

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get update && sudo apt-get remove opera
```

---

### Post by tchoklat on 2009-07-07
> **wojox said:**
> Enter this into the terminal

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get update && sudo apt-get remove opera
```


DONE

Reading state information... Done
Package opera is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly 

ODD as I am using opera now!

---

