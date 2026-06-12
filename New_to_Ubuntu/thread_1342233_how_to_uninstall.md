---
title: "how to uninstall"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by manny43 on 2009-11-30
Need help on how to remove Mythtv completely.THANKS

---

### Post by arochester on 2009-11-30
Connect to the Internet. Open a Terminal. Issue the command: > sudo apt-get remove mythtv

---

### Post by ktmom on 2009-11-30
or --  sudo apt-get purge mythtv

> 
       remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.

       purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).


---

### Post by Virtual Liberty on 2009-11-30
Or ..

```
dpkg -r <application>
```
```
sudo make uninstall
```

---

### Post by Paqman on 2009-11-30
Or open up Synaptic, search for mythtv, right click > uninstall completely > apply.

---

### Post by mikodo on 2009-11-30
> **ktmom said:**
> or --  sudo apt-get purge mythtv

Would this remove dependencies for other apps?

Thanks.

---

### Post by manny43 on 2009-11-30
sudo apt-get remove mythtv did it for me thanksssss

---

### Post by ktmom on 2009-12-01
> **mikodo said:**
> Would this remove dependencies for other apps?

Thanks.

I think you need to use autoremove to remove the dependencies that got installed if they are no longer needed by anything.

---

