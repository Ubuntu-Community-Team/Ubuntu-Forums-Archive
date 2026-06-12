---
title: "changing permissions"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by stonerrob420 on 2009-02-19
I just recently backed up all my music and video into a a spare drive and then reinstalled ubuntu 8.10. Now all my files in that drive are owned by root. How do I change the permissions on that drive and all the files in that drive that way I can move them back to my music and video folder on new installation of ubuntu 8.10? The spare drive is also formatted as ext3.

---

### Post by Tek-E on 2009-02-19
> **stonerrob420 said:**
> I just recently backed up all my music and video into a a spare drive and then reinstalled ubuntu 8.10. Now all my files in that drive are owned by root. How do I change the permissions on that drive and all the files in that drive that way I can move them back to my music and video folder on new installation of ubuntu 8.10? The spare drive is also formatted as ext3.
```

man chown

```

---

### Post by taurus on 2009-02-19
Assuming you have mounted that drive to /media/share and your login name is rob, you can change the ownership with

```
sudo chown -R rob:rob /media/share
ls -la /media/share
```

---

### Post by iaculallad on 2009-02-19
By using the terminal command chown:

```
sudo chown username:username /media/mountpoint_of_drive
```

and later, you could also set the permission using chmod command:

```
sudo chmod -R 755 /media/mountpoint_of_drive
```

That would do it.

---

### Post by stonerrob420 on 2009-02-19
Hey it worked! I used  sudo chown -R robert:robert /media/disk it worked like a charm. Thanks for all the help.

---

