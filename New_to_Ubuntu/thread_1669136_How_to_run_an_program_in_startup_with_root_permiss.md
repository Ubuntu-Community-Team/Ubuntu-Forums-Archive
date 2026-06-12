---
title: "How to run an program in startup with root permission"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by jao_madn on 2011-01-17
Hi,

I would like to ask i someone may know how to run an program with root privileged (ex. Firestarter, GUFW,) i tried in the Preferences>startup Application but failed to exec on start up it and display pup op error stated: me as user dont have permission to start the application. Does it main i would change the permission of the /usr/sbin/firestarter or any program with root privileged to my username if i want to run it on stat up.

Hope u can help me.

Thanks in advance

---

### Post by DOSIX on 2011-01-17
you can try logging in as root (not in a terminal, from the login screen) and doing it from there. that should work. but don't spend too much time fussing around in there. just do that and then log out.

---

### Post by Frogs Hair on 2011-01-17
I think you would have to disable keyring passwords for all programs. This tread my be related.[http://ubuntuforums.org/showthread.php?p=4377271](http://ubuntuforums.org/showthread.php?p=4377271)

---

### Post by jao_madn on 2011-01-17
> **DOSIX said:**
> you can try logging in as root (not in a terminal, from the login screen) and doing it from there. that should work. but don't spend too much time fussing around in there. just do that and then log out.
@dosix: So i need to enable root loging in..is not allowed for logging in by root by dafault.

---

### Post by DOSIX on 2011-01-17
all you have to do is set the root password from the terminal.

```

sudo passwd 

(where it says type in new UNIX password just type in the password you want to use for the account and then retype it when it asks you to)

```
now all you have to do is just log out and log in as root from the login screen

and DO NOT forget that password!!!!! hahaha.

---

### Post by pl@yer on 2011-01-17
you could use crontab and @reboot.

```

sudo -s
crontab -e

```

---

### Post by bodhi.zazen on 2011-01-17
> **jao_madn said:**
> Hi,

I would like to ask i someone may know how to run an program with root privileged (ex. Firestarter, GUFW,) i tried in the Preferences>startup Application but failed to exec on start up it and display pup op error stated: me as user dont have permission to start the application. Does it main i would change the permission of the /usr/sbin/firestarter or any program with root privileged to my username if i want to run it on stat up.

Hope u can help me.

Thanks in advance

You do not need to run either GUFW or Firestarter on startup or login.

First, these are both tools to configure your firewall (iptables). You run them configure your firewall (iptables), and then close them. There is (almost) no reason to run the graphical interface when you boot or log in. Your configuration remains in effect even without the graphical tools running.

Second, firestarter is not actively maintained and conflicts with GUFW, so you should not use both.

I suggest you remove (you need to purge) firestarter

```
sudo apt-get purge firestarter
```

Fior the vast majority of desktop users you do not need a firewall at all, but if you still want to run one:

```
sudo ufw enable
``` is all 99.999% of desktop users will ever need to do.

Third you should NOT use firestarter to monitor your network or fiewall.

Fourth there is a subtle but important difference between running an application or program at boot vs at login.

To run @ boot you either write a boot (init) script or add to /etc/rc.local. To run at login you configue it at startup.

Last, you do not need to set a root password or log in as root, that was just bad advice for your situation.

See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2011-01-17
> **DOSIX said:**
> you can try logging in as root (not in a terminal, from the login screen) and doing it from there. that should work. but don't spend too much time fussing around in there. just do that and then log out.

This advice is simply inappropriate. You do not need to log in as root to configure your firewall.

---

### Post by jao_madn on 2011-01-17
Thanks for all the reply, clarification and information.

---

