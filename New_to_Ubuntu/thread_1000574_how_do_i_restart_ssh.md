---
title: "how do i restart ssh"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-03
ive made some changed to ssh_config file, and i need to restart ssh...?
is there a way of doing this without restarting the whole computer?

---

### Post by cariboo on 2008-12-03
Every service can be restarted with out rebooting. To restart ssh, in a terminal type;

```
sudo /etc/init.d/ssh restart
```

Most of the startup scripts are located in /etc/init.d

Jim

---

### Post by jpkotta on 2008-12-03
```
sudo /etc/init.d/ssh reload
```

---

