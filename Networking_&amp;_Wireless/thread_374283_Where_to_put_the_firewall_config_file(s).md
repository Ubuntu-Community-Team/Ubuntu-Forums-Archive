---
title: "Where to put the firewall config file(s) ?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by mcrib on 2007-03-02
I am using 6.10 server. Where should I put the iptables config script ?

/etc/init.d/ ...?
How can I be sure that it comes up together with the interfaces ? Does update-rc.d know what script this is ?

/etc/network/interfaces ...?

Is there an official rule ?

Thanks,

M.

---

### Post by halfvolle melk on 2007-03-02
> **mcrib said:**
> /etc/init.d/ ...?
Yep. You can call it whatever you want /etc/init.d/iptables would be the obvious choice. It will start at boot, like all other stuff in init.d.

---

### Post by mcrib on 2007-03-02
[/etc/rc2.d] $ ls
K80mysql            S19cupsys         S20powernowd   S91apache2
S05vbesave          S19mysql-ndb-mgm  S20rsync       S91apache-ssl
S10acpid            S20apmd           S20xinetd      S98usplash
S10powernowd.early  S20hotkey-setup   S21mysql-ndb   S99acpi-support
S10sysklogd         S20iptables       S23ntp-server  S99rc.local
S11klogd            S20laptop-mode    S25mdadm       S99rmnologin
S12dbus             S20makedev        S50freeradius  S99stop-readahead
S13gdm              S20no-ip          S89anacron
S14ppp              S20nvidia-kernel  S89atd
S18hplip            S20postfix        S89cron

iptables is started after cupsys ? - doesn't make much sense to me. Firewall has to be started when is interfaces are coming up....!

---

### Post by mcrib on 2007-03-07
OK. according to 'man interfaces'  the file(s) should go to /etc/network/if-pre-up.d
However the scripts do not seem to get processed. According the the man page the scripts should be invoked for every interface. Since my fw script didn't seem to get executed I wrote this little test script

```

**# cat /etc/network/if-pre-up.d/test**
#!/bin/sh

touch /tmp/$0.${IFACE}

```

chmod 777 it and rebooted the machine - not entries in /tmp

Do I have the Disneyland Edition ?

---

