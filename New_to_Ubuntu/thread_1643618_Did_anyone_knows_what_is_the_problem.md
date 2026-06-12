---
title: "Did anyone knows what is the problem ?"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by alfamuzjak on 2010-12-12
I'm using ubuntu server 10.10...Until now i installed few things like phpmyadmin and vsftpd.
Problem occurs while trying to start,stop or restart vsftpd service:

command 1
$ **sudo /etc/init.d/vsftpd restart**
appears message...
"Rather than invoking init scripts throught /etc/init.d, use the service( 8 ) utility, e.g service vsftpd restart

Since the script you ae attempting to invoke has been converted to an Upstart job, you nay also use the restart( 8 ) utility, e.g restart vsftpd vsftpd start/running, process 1053"

command 2
$ **service vsftpd restart**
appears...
"restart: Unable to connest to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory"

Anyone knows how to resolve this?

---

### Post by BugBuster on 2010-12-12
In command 2 you are missing sudo, try that again with the sudo!!
```
sudo service vsftpd restart
```

---

### Post by alfamuzjak on 2010-12-12
i tryed that after adding some options in vsftpd.conf and got something like  restart: Unknown ....
BTW i restored vmware in state before vsftp was installed and try with service restart...It works, thx for helping

---

### Post by alfamuzjak on 2010-12-12
Now...how to tag tread as SOLVED?

---

### Post by alfamuzjak on 2010-12-12
nvm..done

---

