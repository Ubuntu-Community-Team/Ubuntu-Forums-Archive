---
title: "sudo nano in shell?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-30
I was making some changes to my /etc/fstab while in Ubuntu so I could force a mount of my external harddrive.  When I rebooted I got an error saying it can't mount to the folder specified (I made a mistake and forgot to create the directory).  My only option was to try again or enter the command shell (I'm not real comfortable working in this environment but I figured what the heck)

I did:

[code]sudo nano /etc/fstab

then I made my necessary changes to the fstab file but when I tried to save it I got an error saying it's Read Only.  Isn't that why I did SUDO?  What am I missing here? I can't boot into Ubuntu so I'm a little stuck at the moment

---

### Post by Jordanwb on 2009-12-30
Try 

```
sudo chmod 0744 /etc/fstab
```

to make it writable by root and try to edit it again.

---

### Post by cartisdm on 2009-12-30
> **Jordanwb said:**
> Try 

```
sudo chmod 0744 /etc/fstab
```

to make it writable by root and try to edit it again.

I ended up booting up a liveCD and making the changes to my /fstab file then rebooting but thanks for the chmod advice.  I will use that next time!

---

### Post by Jordanwb on 2009-12-30
Are you sure you used sudo when you tried to edit the file with nano?

---

### Post by cartisdm on 2009-12-30
> **Jordanwb said:**
> Are you sure you used sudo when you tried to edit the file with nano?

positive, I even tried it twice just to be sure.  I also tried to

```
sudo mkdir
```

and create the directory that I needed to mount to

---

### Post by Jordanwb on 2009-12-30
> **cartisdm said:**
> ```
sudo mkdir
```

and create the directory that I needed to mount to

/etc already exists. :confused:

---

### Post by cartisdm on 2009-12-30
> **Jordanwb said:**
> /etc already exists. :confused:

I had set my harddrive to mount to /media/Big_Rig

but I never created "/media/Big_Rig"  I was hoping that I could just create the directory and then be back in shape

---

