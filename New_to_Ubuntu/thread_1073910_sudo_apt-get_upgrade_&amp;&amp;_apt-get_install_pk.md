---
title: "sudo apt-get upgrade &amp;&amp; apt-get install pkg1 OR we should use sudo for 2nd part?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-18
Hi
what is differences between the following two commands? I want to execute them and leave the computer to download and install the packages (unattended) I do not know whether they will ask for password again or not.

```

sudo apt-get upgrade && apt-get install pkg1

```

and
```

sudo apt-get upgrade && sudo apt-get install pkg1

```


Does sudo command time-out? for example if the first part take 4 hours to complete, will it ask for password when it want to execute the second part?

thanks

---

### Post by bodhi.zazen on 2009-02-18
Use sudo ...

You will only have to enter your password once 9unless it times out) ;)

---

### Post by Rolcol on 2009-02-18
The first case will run "sudo apt-get update".  If that program exits without any problems, then the second command will run.  The second command will not be able to execute without root privilages or sudo.  "sudo" will only affect the first command.  The second case will run "sudo apt-get update" and will execute "sudo apt-get upgrade" only if the first one exists without an error.  Since sudo has a 15 min timeout by default, you may have to retype your password.  If all you're going to do is update your packages, you may run the commands as the root user rather than with sudo.

```
sudo -i
# Enter your password and you will be logged in as the root user.
# You'll then be able to run the commands without appending sudo.
# Eg: apt-get update && apt-get upgrade
```

---

### Post by legolas_w on 2009-02-18
Hi

Thank you all,
If I use root to perform this tasks, will the pkg1 installs for my own user too? or somehow it will installs only for root user.

I just remembered that sudo apt-get update will ask for my approval (to download and install the packages) is it possible to pass the *yes* parameter to ensure that it will headlessly porceed and install all required packages?

Thanks.

---

### Post by drs305 on 2009-02-18
> **legolas_w said:**
> 
If I use root to perform this tasks, will the pkg1 installs for my own user too? or somehow it will installs only for root user.
It would install it system wide and be available to you.
> 
I just remembered that sudo apt-get update will ask for my approval (to download and install the packages) is it possible to pass the *yes* parameter to ensure that it will headlessly porceed and install all required packages?

You can append *apt-get* with the "-y" option to apply an automatic "Yes" to all prompts.

---

### Post by oldos2er on 2009-02-18
"apt-get update" updates your sources. "apt-get upgrade" installs any upgrades that may be available after updating.

---

### Post by bodhi.zazen on 2009-02-18
You can use these commands :

```
sudo apt-get update && sudo apt-get install package 1 && sudo -c bash "yes | apt-get dist-upgrade"
```

The first two command should under normal circumstances complete in under teh sudo time out or grace period and the last will automate the upgrade as much as possible.

---

