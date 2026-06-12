---
title: "ufw gives a scary warning. What to do?  9.04"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by robert shearer on 2009-05-30
just checked the status of ufw and got this output.

 sudo ufw status
WARN: / is world writable!
WARN: / is group writable!
Status: active


is that scary or what??
Closing down this compy and will check back here from another.

So far googles and site searches have found nothing either helpful or reassuring.

rkhunter checks out all ok other than the usual unhide warningd, so what gives?

---

### Post by k3lt01 on 2009-05-30
At least yours is active. I just checked mine and it come back Inactive. Still I'm not worried.

---

### Post by Didius Falco on 2009-05-30
Hi,

I've found several bug reports on Launchpad referencing this. They reference Samba, but are also pointing at file permissions being set wrong. In 37186, the last poster says: > It looks like adding a missing smb.conf to /etc/samba/ solved the problem.Unfortunately, he doesn't offer any more information than that. Perhaps you could contact him for more information:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/371876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/371876)

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/371530](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/371530)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357131)
 

I hope this helps,

Regards,

Didius

---

### Post by 3rdalbum on 2009-05-30
If you open your filesystem with Nautilus so you can see /bin, /usr, /lib etc, and right-click to create a folder, will it let you do it?

If it will let you create a folder there and you are not logged in as root, then that is highly unusual and possibly worrying. If it won't let you create the folder, then you can disregard the error message that ufw gave you.

---

### Post by robert shearer on 2009-05-31
> **3rdalbum said:**
> If you open your filesystem with Nautilus so you can see /bin, /usr, /lib etc, and right-click to create a folder, will it let you do it?

If it will let you create a folder there and you are not logged in as root, then that is highly unusual and possibly worrying. If it won't let you create the folder, then you can disregard the error message that ufw gave you.

OK, thanks for that, tried as you suggest and cannot create folders:D

Now posting from my 8.04 hardy install and when checking ufw status it gives this output

 sudo ufw status
[sudo] password for : 
ERROR: / is world writable!

and no status!
 Then when I try sudo ufw enable it returns the same.:(

So no status and no enabling. 

Wondering what use ufw is ???

Should I just use something else like firestarter or guarddog??


> I hope this helps,

Regards,

Didius 

Thanks, I will check out the links.

> At least yours is active. I just checked mine and it come back Inactive. Still I'm not worried. 


I even doubt that now! If it reports everything else wrong then is it really active??

---

