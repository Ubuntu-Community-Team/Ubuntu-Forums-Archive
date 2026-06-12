---
title: "Make windows partition mount along with Ubuntu's?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Dullstar on 2009-10-23
I'd love it if I didn't have to type my password when I want to access my Windows filesystem.  Not that I have to all the time, but even if it's only every once in a while, it gets annoying.  Can I get it to mount on boot up?
If it helps, the partition I would like to automatically mount is /dev/sda1

---

### Post by OpenGuard on 2009-10-23
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by John Bean on 2009-10-23
> **OpenGuard said:**
> [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

From the above: "If, for some reason, that doesn't work, try rebooting the computer. "
That line in the tutorial is very erm... Windows ;-)

---

### Post by tarps87 on 2009-10-23
How to auto mount other types of drive as well:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by OpenGuard on 2009-10-23
> **John Bean said:**
> From the above: "If, for some reason, that doesn't work, try rebooting the computer. "
That line in the tutorial is very erm... Windows ;-)

fstab is loaded on startup, not every 5 seconds or so. If you change something in it, you need to reload it.

---

### Post by tarps87 on 2009-10-23
> **OpenGuard said:**
> fstab is loaded on startup, not every 5 seconds or so. If you change something in it, you need to reload it.

or
```
sudo mount -a
```
Come to think of it I don't think you even need root privileges

---

### Post by blazemore on 2009-10-23
> **tarps87 said:**
> or
```
sudo mount -a
```
Come to think of it I don't think you even need root privileges

You do, unless the filesystem is mounted in userspace with FUSE

---

### Post by Johan Karl Johansen on 2009-10-23
pysdm has grafical inteface. worked great for me =) search it on synptic

---

### Post by tarps87 on 2009-10-23
> **blazemore said:**
> You do, unless the filesystem is mounted in userspace with FUSE

Good point, I must be going loopy

---

