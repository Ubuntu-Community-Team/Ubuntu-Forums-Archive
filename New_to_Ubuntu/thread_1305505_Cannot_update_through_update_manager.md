---
title: "Cannot update through update manager"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-10-29
I get to update 2 and it just stall, will not download, speed drops to unknown.

Is there any way to work around this?

Mick

EDIT oh yes I upgraded to 9.10 five days ago

---

### Post by collinp on 2009-10-29
I need some more information:

What are you trying to do in Update Manager? Upgrade?

And, what is update 2?

---

### Post by Mick8882003 on 2009-10-29
I upgraded on monday? Now I cannot update any packages, I think it has broken virtual box as well.

---

### Post by collinp on 2009-10-29
You said it is stalling on "Update 2", what exactly is "Update 2"?

---

### Post by Mick8882003 on 2009-10-29
Checkbox.

---

### Post by Mick8882003 on 2009-10-30
I am still having trouble updating from update manager.

---

### Post by philinux on 2009-10-30
Open a terminal, Apps>Access>terminal.

Run these two commands one at a time and post back the full errors.
```

sudo apt-get update

then

sudo apt-get upgrade
```

---

### Post by Mick8882003 on 2009-10-30
mickpc@ubuntu:~$ sudo apt-get update
[sudo] password for mickpc: 
Sorry, try again.
[sudo] password for mickpc: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_AU 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_AU   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_AU 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources           
56% [Connecting to au.archive.ubuntu.com (32.1.3.136)]^Z                    
[1]+  Stopped                 sudo apt-get update
mickpc@ubuntu:~$ 

It hung on the last line, I ^z'd out of it.


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mickpc@ubuntu:~$

---

### Post by philinux on 2009-10-30
Close synaptic, update manager and add remove. 

Run the commands again, sometimes the servers are slow.

If you get the same error reboot and then try them.

---

### Post by Mick8882003 on 2009-10-30
Tried it many times now, with a few reboots inbetween. The upgrade is fine, just not the update, still hangs.

Mick

Oh btw im using 64 bit

---

### Post by philinux on 2009-10-30
The problem is the lock file then.


Try this first.

```
sudo dpkg --configure -a
```

If that comes back with errors.

```
sudo lsof /var/lib/dpkg/lock
```

Post back the errors from both the above commands.

---

