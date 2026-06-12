---
title: "How to auto-run a command with authentication?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-10-06
I have to run a command each time a start my Ubuntu deski and that is
```
sudo modprobe -r kvm-intel
```

I want to autorun this command at start-up. I know how to make an entry for running a command or application on start-up which does not require authenticity. But in this command authenticity is required. So how to do that?

Thank you...

---

### Post by ptn107 on 2009-10-06
Just add that module to the blacklist then you won't have to run anything at startup.
```
echo 'kvm-intel' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

