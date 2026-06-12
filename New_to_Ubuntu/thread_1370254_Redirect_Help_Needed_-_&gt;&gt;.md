---
title: "Redirect Help Needed - &gt;&gt;"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by spikoley on 2010-01-02
I am trying to append a file from my home directory to a log file in /var and keep receiving permission issue when using sudo.

```

sudo less apache.log >> /var/log/apache2/apache.log 
-bash: /var/log/apache/apache.log: Permission denied

```

Any ideas?

---

### Post by jonest1 on 2010-01-02
You should do something like the following for your command.

```
sudo bash -c "less apache.log >> /var/log/apache2/apache.log"
```

This creates a subshell where the entire command is used as root.  Otherwise, the less is done as root and the redirect is as your user account.

---

### Post by spikoley on 2010-01-07
> **jonest1 said:**
> You should do something like the following for your command.

```
sudo bash -c "less apache.log >> /var/log/apache2/apache.log"
```

This creates a subshell where the entire command is used as root.  Otherwise, the less is done as root and the redirect is as your user account.

Thanks man, it worked!  I learned something new.

---

