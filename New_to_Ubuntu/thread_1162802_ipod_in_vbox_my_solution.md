---
title: "ipod in vbox my solution"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by powel212 on 2009-05-18
I couldn't get xp to mount my ipod in vbox so I read a bunch of threads and found no clear solution. It seems vbox needs greater permissions to gain access to the ipod. I found some threads that talked about how to fix this but none of the threads offered details as to why I needed to modify fstab and sudo edit other config files.

All I did to solve my problem was launch vBox as admin. 

This may or may not be dangerous. I don't know what the consequences are to giving vbox these kind of elevated privileges but it was a very fast way of enabling ipod syncing within vbox without having to modify config files.

If anyone knows specific reasons for not wanting to give Vbox these permissions please post here. And if anyone has clear information on how where and why someone might need to edit config files in order for vbox to properly mount ipods without giving it sudo power please post here.

Powel

---

### Post by kpkeerthi on 2009-05-18
What groups you belong to? Post the output of
```
groups
``` command.

---

### Post by powel212 on 2009-05-18
```
user adm dialout cdrom floppy audio dip video plugdev lpadmin sambashare scanner admin

```

---

### Post by kpkeerthi on 2009-05-19
You need to install the closed source edition (PUEL) of VirtualBox for USB support. Instructions available [here]("http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html").

After installing proceed with the following:

1. ```
sudo gpasswd -a <your-user-id> vboxusers
```
and logout and log back in.

2. Add the below line to /etc/fstab of your **host**:
```
none      /proc/bus/usb usbfs     auto,busgid=[COLOR="Red"]108[/COLOR],busmode=0775,devgid=[COLOR="Red"]108[/COLOR],devmode=0664 0 0
```
*Replace the gid highlighted in red with that from the output of the below command:
```
grep vboxusers /etc/group
```

3. Reboot your **host**

Once your guest is up in VirtualBox, you may plugin in your USB device and then choose Device -> USB from VirtualBox menu.

---

### Post by albinootje on 2009-05-19
Which version of VirtualBox are you running by the way ?

---

### Post by powel212 on 2009-05-19
Thanks for the clear information and instructions.

I am pretty sure I am running version 2.2_2 for Jaunty x64 

P

---

### Post by albinootje on 2009-05-19
> **powel212 said:**
> Thanks for the clear information and instructions.

I am pretty sure I am running version 2.2_2 for Jaunty x64 

P

Okay, for 2.2.2 you shouldn't need to alter your /etc/fstab.
After adding your user to the vboxusers group, make sure to log out  
(logout, not reboot), and then log in again.
Then check whether your user is in the vboxusers group with :
```

groups

```
or 
```

id

```

---

### Post by powel212 on 2009-05-19
That was the magic. Worked perfectly. No need to modify fstab.

Thank you very much

Powel

---

### Post by kpkeerthi on 2009-05-19
Glad it worked for you without the need for the fstab tweak. I run Ubuntu Server as a guest on vbox2.2.2 and I had to do this as suggested in [vbox manual]("http://www.virtualbox.org/manual/UserManual.html#id2661849") to get USB working in the guest.

---

