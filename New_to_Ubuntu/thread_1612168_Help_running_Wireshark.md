---
title: "Help running Wireshark"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by DFord425 on 2010-11-02
I install Wireshark and i followed their directions so that i can run it with my username, not root. But now when i try to run it and start a capture, i get this message:
```
Couldn't run /usr/bin/dumpcap in process: Permission Denied
```
What could be stopping me from starting the capture, do i need to change the permissions on the interface?
This might help
```
dford@speed6:/usr/bin$ ls -l dumpcap
-rwxrwxr-- 1 root wireshark 54540 2010-10-03 18:52 dumpcap
dford@speed6:/usr/bin$ groups dford
dford : dford adm dialout cdrom plugdev fuse netdev lpadmin admin sambashare wireshark
dford@speed6:/usr/bin$
```

---

### Post by DFord425 on 2010-11-03
Anyone have any ideas?

---

### Post by rcayea on 2010-11-03
You could kill that process then try again. 

Use the System Monitor found under System-->Administration

---

### Post by A_M_S on 2010-11-03
Why don't you run it with admin privileges using the command gksu wireshark ?

It works well for me.

---

### Post by Zzl1xndd on 2010-11-03
> **A_M_S said:**
> Why don't you run it with admin privileges using the command gksu wireshark ?

It works well for me.

+1 for this, always worked for me.

---

### Post by ArgusVision on 2010-11-03
Your user dford is in the wireshark group, so it looks like it should work... 'course that doesn't mean it's working. 
You could change ownership to dford and see how that works for you.

```
sudo chown dford:wireshark /usr/bin/dumpcap
```

But since it's a bin file being called up by an app I can't help but wonder, is it calling it up using your permissions or its own?

I personally just run with admin privileges and havn't had a problem.

---

### Post by DFord425 on 2010-11-03
starting from the command line with sudo works. Changing the owner of dumpcap did not work. I think i have to change the permission on the interface.

---

### Post by PanamaJack on 2011-01-29
I just ran it with:
sudo wireshark

and this worked for me, 
Thanks

---

### Post by corysober on 2012-11-03
The problem is caused by a permissions issue in /usr/sbin. To fix it so that all users can run Wireshark without having to be root, change the permissions like this:

First, change the owner of these two files like this:

```
sudo chown your.username /usr/sbin/wireshark
sudo chown your.usrname /usr/sbin/dumpcap
```

Then, change the file permissions so that all users can access the files:

```
sudo chmod 777 /usr/sbin/wireshark
sudo chmod 777 /usr/sbin/dumpcap
```

After doing this, your error will go away, but you may not see any interfaces in your configuration. If this happens, do the following:

```
sudo groupadd wireshark
sudo usermod -a -G wireshark YOUR_USER_NAME
sudo chgrp wireshark /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo getcap /usr/bin/dumpcap
sudo chmod +xs /usr/bin/dumpcap
```

---

### Post by Old_Grey_Wolf on 2012-11-03
Old thread.

Closed.

---

