---
title: "Starting Services at Boot"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by buee on 2009-09-25
I have two scripts that need to be run at boot time as root.  /etc/init.d/mediatomb start and /etc/init.d/3dm2 start

They supposedly start themselves, but neither of them want to start at boot time and I must always start them manually.  I have checked all the /etc/rc* and each has an entry for both.  What am I doing wrong?

---

### Post by mikewhatever on 2009-09-25
Take a look at /etc/rcS.d. There is an informative readme file in there.
cat /etc/init.d/README

---

### Post by scorp123 on 2009-09-25
> **buee said:**
> /etc/init.d/mediatomb start and /etc/init.d/3dm2 start ```
man update-rc.d
```

... or you place those commands into **/etc/rc.local** (before the line that says "exit 0")

---

### Post by buee on 2009-09-25
> **scorp123 said:**
> ```
man update-rc.d
```

... or you place those commands into **/etc/rc.local** (before the line that says "exit 0")

I tried both of these and neither did anything for either service.

---

### Post by scorp123 on 2009-09-25
> **buee said:**
> I tried both of these and neither did anything for either service. You added the two services with the update-rc.d command? Can you show me the output of:

```
ls -al /etc/rc2.d/
```

---

### Post by buee on 2009-09-25
> **scorp123 said:**
> You added the two services with the update-rc.d command? Can you show me the output of:

```
ls -al /etc/rc2.d/
```

```
total 20
drwxr-xr-x   2 root root  4096 2009-09-24 22:16 .
drwxr-xr-x 145 root root 12288 2009-09-24 23:01 ..
-rw-r--r--   1 root root   556 2009-03-31 04:02 README
lrwxrwxrwx   1 root root    19 2009-07-31 12:42 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root    15 2009-07-31 12:42 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root    18 2009-07-31 12:42 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root    15 2009-07-31 12:42 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root    14 2009-07-31 12:42 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root    13 2009-07-31 13:31 S16ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root    23 2009-08-11 20:12 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx   1 root root    19 2009-08-11 20:12 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx   1 root root    15 2009-08-11 20:12 S19mysql -> ../init.d/mysql
lrwxrwxrwx   1 root root    16 2009-07-31 12:42 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root    22 2009-07-31 12:42 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root    19 2009-08-04 17:00 S20mediatomb -> ../init.d/mediatomb
lrwxrwxrwx   1 root root    23 2009-09-24 22:16 S20nagiosgrapher -> ../init.d/nagiosgrapher
lrwxrwxrwx   1 root root    17 2009-08-17 18:46 S20postfix -> ../init.d/postfix
lrwxrwxrwx   1 root root    15 2009-07-31 13:35 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    15 2009-08-10 19:36 S20snmpd -> ../init.d/snmpd
lrwxrwxrwx   1 root root    16 2009-08-26 16:38 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root    22 2009-08-17 01:46 S20zabbix-agent -> ../init.d/zabbix-agent
lrwxrwxrwx   1 root root    23 2009-08-17 01:46 S20zabbix-server -> ../init.d/zabbix-server
lrwxrwxrwx   1 root root    13 2009-08-17 01:24 S23ntp -> ../init.d/ntp
lrwxrwxrwx   1 root root    13 2009-07-31 12:42 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root    19 2009-07-31 12:42 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    13 2009-07-31 12:42 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    17 2009-08-17 18:46 S30nagios3 -> ../init.d/nagios3
lrwxrwxrwx   1 root root    22 2009-07-31 12:42 S50avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root    14 2009-07-31 12:42 S50cups -> ../init.d/cups
lrwxrwxrwx   1 root root    24 2009-07-31 12:42 S50NetworkManager -> ../init.d/NetworkManager
lrwxrwxrwx   1 root root    20 2009-07-31 12:42 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root    15 2009-07-31 12:42 S50rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2009-07-31 12:42 S50saned -> ../init.d/saned
lrwxrwxrwx   1 root root    31 2009-07-31 12:42 S50system-tools-backends -> ../init.d/system-tools-backends
lrwxrwxrwx   1 root root    21 2009-07-31 12:42 S70bootlogs.sh -> ../init.d/bootlogs.sh
lrwxrwxrwx   1 root root    19 2009-07-31 12:42 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx   1 root root    18 2009-07-31 12:42 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx   1 root root    17 2009-07-31 12:42 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2009-07-31 12:42 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2009-07-31 12:42 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    24 2009-07-31 12:42 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    17 2009-08-10 19:36 S91apache2 -> ../init.d/apache2
lrwxrwxrwx   1 root root    17 2009-07-31 12:42 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    14 2009-07-31 22:06 S993dm2 -> ../init.d/3dm2
lrwxrwxrwx   1 root root    22 2009-07-31 12:42 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2009-07-31 12:42 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2009-07-31 12:42 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx   1 root root    18 2009-07-31 12:42 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2009-07-31 12:42 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root    24 2009-07-31 12:42 S99stop-readahead -> ../init.d/stop-readahead
lrwxrwxrwx   1 root root    18 2009-07-31 19:10 S99webmin -> /etc/init.d/webmin

```

---

### Post by scorp123 on 2009-09-25
> **buee said:**
> ```

...
lrwxrwxrwx   1 root root    19 2009-08-04 17:00 S20mediatomb -> ../init.d/mediatomb
lrwxrwxrwx   1 root root    14 2009-07-31 22:06 S993dm2 -> ../init.d/3dm2
...

```

OK ... they are there. What happens if you launch them manually from that location and thus simulate what would actually happen during a system boot? e.g. you'd open a terminal and type this:
```
sudo /etc/rc2.d/S20mediatomb
sudo /etc/rc2.d/S993dm2

```

Do they spit out any error messages?

---

### Post by wojox on 2009-09-25
Try:

```
sudo update-rc.d mediatomb defaults
```

---

### Post by scorp123 on 2009-09-25
> **wojox said:**
> Try:

```
sudo update-rc2.d mediatomb start
``` 

It's "update-rc.d" ... not "update-rc2.d" ;)

---

### Post by buee on 2009-09-25
> **scorp123 said:**
> OK ... they are there. What happens if you launch them manually from that location and thus simulate what would actually happen during a system boot? e.g. you'd open a terminal and type this:
```
sudo /etc/rc2.d/S20mediatomb
sudo /etc/rc2.d/S993dm2

```

Do they spit out any error messages?

Yes, usage syntax.  Like it's looking for 'start' at the end.

---

### Post by scorp123 on 2009-09-25
> **buee said:**
> Yes, usage syntax.  Like it's looking for 'start' at the end. Then those two scripts in /etc/init.d/ are at fault. They should normally check how they're being called and then adjust automatically.

Plan B:

What if you add the two lines to rc.local (like I suggested in my first posting?)

```
/etc/init.d/mediatomb start
/etc/init.d/3dm2 start

```

Does that work?

---

### Post by buee on 2009-09-25
> **scorp123 said:**
> Then those two scripts in /etc/init.d/ are at fault. They should normally check how they're being called and then adjust automatically.

Plan B:

What if you add the two lines to rc.local (like I suggested in my first posting?)

```
/etc/init.d/mediatomb start
/etc/init.d/3dm2 start

```

Does that work?

That's actually been in there from me trying to figure it out, that isn't working either.

---

### Post by scorp123 on 2009-09-26
> **buee said:**
> That's actually been in there from me trying to figure it out, that isn't working either. Are those scripts executable? Just to be sure ... ?

---

### Post by buee on 2009-09-27
> **scorp123 said:**
> Are those scripts executable? Just to be sure ... ?

They're symbolic links to the scripts that I run manually anyway, so yes, they must be executable.  Just to be sure....

```
-rwxr-xr-x 1 root root  750 2006-06-05 13:24 3dm2
-rwxr-xr-x 1 root root 5.0K 2009-08-28 21:54 mediatomb
```

---

### Post by buee on 2009-09-29
No other ideas here?

---

### Post by MadCatmkII on 2009-10-04
I've spent the evening trying to get Mediatomb to start at bootup as well. Just now I was going through the /etc/default/mediatomb configfile and found this at the end:

```
# The user and group that MediaTomb should be run as.
USER="mediatomb"
GROUP="mediatomb"
```

So just for kicks I checked to see if my server had the user 'mediatomb'. It did. It also had the usergroup. I did however discover that user wasn't part of the group. Someone needs to spank whoever wrote the installation script ;)

So, long story short: Add the user 'mediatomb' to the usergroup 'mediatomb' and it should work without additional poking around.

```

sudo adduser mediatomb mediatomb
Adding user mediatomb to group mediatomb

```

---

