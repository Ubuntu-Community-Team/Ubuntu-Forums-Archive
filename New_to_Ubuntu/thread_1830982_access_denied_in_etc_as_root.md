---
title: "access denied in /etc as root"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-08-22
When running this command, do I get access denied. Editing the file with 'vi' as root works fine, but not this.
```

sudo iptables-save -c > /etc/iptables.rules

```Using it to save iptables, taken from this guide. The reason for noticing it, was that new configurations didn't get saved, so the bash script have the same problem.
[https://help.ubuntu.com/community/IptablesHowTo#Solution%20#2%20/etc/network/if-pre-up.d%20and%20../if-post-down.d]("https://help.ubuntu.com/community/IptablesHowTo#Solution%20#2%20/etc/network/if-pre-up.d%20and%20../if-post-down.d")
```

ls -l /etc/iptables.rules
-rw-r--r-- 1 root root 0 2011-08-22 23:00 /etc/iptables.rules

```

---

### Post by sisco311 on 2011-08-22
EDIT:
Yep, that should be:
```
sudo bash -c "iptables-save -c > /etc/iptables.rules"
```

---

### Post by Frozen Forest on 2011-08-22
Thanks, work perfectly

---

