---
title: "upgrade from 8.04 to 9.10"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by ZootHornRollo on 2009-10-24
Hi,

I am trying to upgrade my 8.04 installation to 9.10 RC.

I have run ```
update-manager -d
``` but it tells me the available upgrade is 8.10.

Any way to overide this?

---

### Post by sliketymo on 2009-10-24
> **ZootHornRollo said:**
> Hi,
 
I am trying to upgrade my 8.04 installation to 9.10 RC.
 
I have run ```
update-manager -d
``` but it tells me the available upgrade is 8.10.
 
Any way to overide this?
 
To upgrade,you have to go to 8.1,then upgrade to 9.o4,then upgrade to 9.10 RC.Might be quicker to dl,and burn the .iso and do a fresh install.Backup home first.:guitar:

---

### Post by empty_spaces on 2009-10-24
I'm pretty sure that you cannot do a direct upgrade. You have to do 8.04 -> 8.10 -> 9.04 -> 9.10.
You are better off doing a fresh install.
Edit: Guess I'm a slow typer

---

### Post by Konbuntu on 2009-10-24
newbie question: how do you backup "home" if you want to install a fresh copy of ubuntu?

---

### Post by ZootHornRollo on 2009-10-24
thanks,

i'll just do a fresh install without backing up home as i have had nothing but bother in the past when doing so.  Also, it's only media that is stored on the machine in question and i have all that backed up on a second HD.

Thank you.

---

### Post by ZootHornRollo on 2009-10-24
> **Konbuntu said:**
> newbie question: how do you backup "home" if you want to install a fresh copy of ubuntu?

save a copy of your home folder on either a partition you will not be reformatting, a cd, usb stick...  etc etc.

Then replace the home folder on your new install when ready.

---

### Post by lovinglinux on 2009-10-24
> **ZootHornRollo said:**
> save a copy of your home folder on either a partition you will not be reformatting, a cd, usb stick...  etc etc.

Then replace the home folder on your new install when ready.

If you don't have a separate partition for home, I strongly advise you create one, so you can do fresh install without loosing settings and personal files. See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Paqman on 2009-10-24
> **ZootHornRollo said:**
> 
Then replace the home folder on your new install when ready.

After you import the contents of the folder back in, you'll probably have to claim ownership of the contents (unless your UID's happen to match, for example if you only ever had one user on both systems)

To take ownership:
```
sudo chown -R username:username /home/username
```

---

### Post by Konbuntu on 2009-10-24
thanks guys!

---

