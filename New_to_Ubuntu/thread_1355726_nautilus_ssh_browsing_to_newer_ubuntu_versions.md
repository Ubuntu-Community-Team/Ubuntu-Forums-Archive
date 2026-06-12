---
title: "nautilus ssh browsing to newer ubuntu versions"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by byenary on 2009-12-15
Hello,

Im used to browse other ubuntu machines using nautilus and do something like this in the location bar ssh://root@192.168.123.30 this always worked and is still working but not any longer when the remote machine is a new ubuntu version, got this problem when remote ubuntu version is 8.10 or higher... 
If i use filezilla on port 22 its fine and ssh in terminal is fine to.. any ideas on this ?
Nautilus says Couldn't display "sftp://root@192.186.123.30/"  Error: Timed out when logging in  Please select another viewer and try again.

Thx

---

### Post by lewisforlife on 2009-12-15
Do the remote computers have root accounts enabled?  Here is what I normally do:

```
ssh -X user@ip-address:/
gksudo nautilus
```

If you don't want to run as root, you can just do a nautilus instead of gksudo nautilus.

---

### Post by Tralce on 2009-12-15
Do you have the openssh-server package installed on the new Ubuntu install?

---

### Post by ukripper on 2009-12-15
> **byenary said:**
> Hello,

Im used to browse other ubuntu machines using nautilus and do something like this in the location bar ssh://root@192.168.123.30 this always worked and is still working but not any longer when the remote machine is a new ubuntu version, got this problem when remote ubuntu version is 8.10 or higher... 
If i use filezilla on port 22 its fine and ssh in terminal is fine to.. any ideas on this ?
Nautilus says Couldn't display "sftp://root@192.186.123.30/"  Error: Timed out when logging in  Please select another viewer and try again.

Thx

root account shouldn't be used in first place to connect via ssh. Ubuntu uses sudo policy [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Therefore, you need to use the account with adminstrative priviliges such as account during installation you created,   use this ```
ssh **yourusername**@192.168.123.30
``` to connect to remote machine.

---

### Post by byenary on 2009-12-15
Hi

-gksudo is no option i'm connecting to servers and im not going to install guipackets on them.

-openssh-server package is installed, with the option during installation

-root was bad to use in an example, im not realy using root...

---

### Post by ukripper on 2009-12-15
in terminal can you try this to connect to remote ssh server :
```
ssh your-username-on-remote-machine@remote-machine-ip-address
```

if that works then your ssh server is configured ok.

---

### Post by byenary on 2009-12-15
Yea as i said in my initial mail it does work in a terminal or even filezilla but it just fails when using nautilus and its a pain in the *** cause im used to work like this to edit files and stuff..and filezilla is to slow for such things...

---

### Post by ukripper on 2009-12-15
Click on places-->Connect to server and select appropriate ssh server there. does that work for you?

If it doesn't work. you may want to try sshfs
[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by byenary on 2009-12-15
nope the bitch is refusing....
I actualy had the problem connecting to a 9.04 to but then i removed /home/user/.ssh/known_hosts and that did solve it for that machine but this 8.10 is still refusing

---

