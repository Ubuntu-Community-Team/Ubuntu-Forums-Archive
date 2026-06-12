---
title: "Samba Deactivated"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by CheShA on 2007-06-21
Hi folks,

I'm using samba and gsambad along with firestarter.  I have them all configured to work fine together, but after the PC has booted, gsambad shows status of samba as "deactivated" ad I have to manually "activate" samba every time.  The boot process shows "Starting Samba daemons"  as "OK".  

Is this normal? Can somebody please tell me the way to change this so samba is activated all the time?

Thanks in advance.

Cris.

---

### Post by ookadoo on 2007-06-21
How does gsambad show the status?  What does a  `ps aux | grep smb` show?

---

### Post by CheShA on 2007-06-22
Hi Man,

gsambad shows status as "Deactivated" until i manually click the "activate" button.

ps aux shows nothing at first :

```
root@chesha:~# ps aux | grep smb
root      1684  0.0  0.0   5032   824 pts/0    S+   17:54   0:00 grep smb

```
Then after being manually activated, it shows as normal: 

```
root@chesha:~# ps aux | grep smb
root      1706  0.0  0.1  72568  2348 ?        Ss   17:55   0:00 smbd -D -s /etc/samba/smb.conf
root      1709  0.0  0.0  72568  1092 ?        S    17:55   0:00 smbd -D -s /etc/samba/smb.conf
root      1710  0.0  0.0  52472  1232 ?        Ss   17:55   0:00 nmbd -D -s /etc/samba/smb.conf
root      1716  0.0  0.0   5036   824 pts/0    S+   17:55   0:00 grep smb
```

---

### Post by ookadoo on 2007-06-22
Ok, then I think your startup script is not working correctly.  In a terminal try `sudo invoke-rc.d samba restart` and if you get errors try to troubleshoot them or post here.

---

### Post by CheShA on 2007-06-22
Nope works fine.  This was straight after a fresh bootup:
```

root@chesha:/var/log# sudo invoke-rc.d samba restart
 * Stopping Samba daemons...                                                    start-stop-daemon: warning: failed to kill 5928: No such process
                                                                         [ OK ]
 * Starting Samba daemons...                                             [ OK ] 
root@chesha:/var/log# sudo invoke-rc.d samba restart
 * Stopping Samba daemons...                                             [ OK ] 
 * Starting Samba daemons...                                             [ OK ] 


```

So the script itsself is working fine, it just isn't getting called on bootup (?) I will keep poking, I'm new to upstart so will need to figure out where and how it does its thang.

---

### Post by ookadoo on 2007-06-22
A link to /etc/init.d/samba should be in /etc/rc5.d/S20samba.  Try `ls -al /etc/rc5.d/S20*` you should see:

S20samba -> ../init.d/samba

if not you can ln -s /etc/init.d/samba /etc/rc5.d/S20samba

---

### Post by CheShA on 2007-06-22
Thanks for your time,i edited /etc/init.d/samba and added the following line:
```

case "$1" in
        start)
                log_daemon_msg "Starting Samba daemons..."
                [COLOR="Red"]**sleep 30**[/COLOR]
                # Make sure we have our PIDDIR, even if it's on a tmpfs
                install -o root -g root -m 755 -d $PIDDIR

```

Which has made it work - for some reason delaying the start of the samba service makes it work. presumably something it is dependent on hasn't yet started (surely this can't be affecting everyone??) . I had originally tried moving samba init from S20samba to S99samba but this hadn't worked.

Thanks again.

Cris

---

