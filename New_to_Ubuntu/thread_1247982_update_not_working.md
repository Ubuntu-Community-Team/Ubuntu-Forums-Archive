---
title: "update not working"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-23
Hi.

when I try to run update 

apt-get update 

I am getting this 
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
``` 

How can i fix it ? because there's a tutorial to update FF and I can't update it without doing this step.

Thanks

---

### Post by bapoumba on 2009-08-23
> **~The~Killer~ said:**
> Hi.

when I try to run update 

apt-get update 

I am getting this 
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
``` 

How can i fix it ? because there's a tutorial to update FF and I can't update it without doing this step.

Thanks
Please close any other package manager (synaptic for ex) and run
```
sudo apt-get update
```

---

### Post by zkriesse on 2009-08-23
The code your running is wrong, the actual command is, WITHOUT QUOTES!!!! 'sudo apt-get update' The command you're trying to run is a root command and without 'sudo' in front of it, it thinks that you are not the root user...so type that command, it will ask you for your password. But when you type your password you WILL NOT see it. This is normal. Just make sure your password is correct or it will say it's wrong. You can type it again of course it's just time consuming. Let me know how it turns out. After you do sudo apt-get update do sudo apt-get upgrade. This will also help. Let me know if you need additional info.

---

