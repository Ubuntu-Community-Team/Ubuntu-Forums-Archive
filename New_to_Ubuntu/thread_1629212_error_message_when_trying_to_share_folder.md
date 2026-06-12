---
title: "error message when trying to share folder"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by immac.omnia on 2010-11-23
When I create a folder, right click it, and click "Sharing Options," I get this error message:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

Please advise.

---

### Post by bananas4370 on 2010-11-23
> **immac.omnia said:**
> When I create a folder, right click it, and click "Sharing Options," I get this error message:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

Please advise.

What folder are you trying to share? You could try pressing Alt-F2 and loading nautilus with 

```
gksudo nautilus
```and try sharing that folder again.

Cheers
Patrick

---

### Post by immac.omnia on 2010-11-24
> **bananas4370 said:**
> What folder are you trying to share? You could try pressing Alt-F2 and loading nautilus with 

```
gksudo nautilus
```and try sharing that folder again.

Cheers
Patrick


Yeah, I already tried that.:confused: I am just trying to share a folder on my desktop. Thanks for trying to help, though.

-immac.omnia

---

### Post by bananas4370 on 2010-11-24
> **immac.omnia said:**
> Yeah, I already tried that.:confused: I am just trying to share a folder on my desktop. Thanks for trying to help, though.

-immac.omnia

One other thing I can think of. Press Alt-F2 and type 

```
gksudo gedit /etc/samba/smb.conf
```

Click Run to open, add password. Look for the [global] tag and under the global section add

```
usershare owner only = False
```

Save the file, reboot and try again. If that doesn't work, then I have no more ideas.

Cheers
Patrick

---

### Post by immac.omnia on 2010-11-24
> **bananas4370 said:**
> One other thing I can think of. Press Alt-F2 and type 

```
gksudo gedit /etc/samba/smb.conf
```

Click Run to open, add password. Look for the [global] tag and under the global section add

```
usershare owner only = False
```

Save the file, reboot and try again. If that doesn't work, then I have no more ideas.

Cheers
Patrick

Thanks, but the line was already there. :(

---

### Post by bananas4370 on 2010-11-24
> **immac.omnia said:**
> Thanks, but the line was already there. :(

Happy to have helped. Hopefully someone else knows a solution.

Cheers
Patrick

---

### Post by yankysunny on 2010-11-24
If you are using a same version of Ubuntu in [http://ubuntuforums.org/showthread.php?t=796106](http://ubuntuforums.org/showthread.php?t=796106) then you can get some hint. otherwise I would suggest to reinstall the packages required to run samba

---

