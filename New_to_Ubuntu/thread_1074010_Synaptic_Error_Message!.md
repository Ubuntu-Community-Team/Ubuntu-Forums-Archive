---
title: "Synaptic Error Message!"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by haziz on 2009-02-18
Each time I try to start synaptic it now reports this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did try to run

sudo dpkg --configure -a

in the terminal but it still did not fix the problem.

Ideas or suggestions?

Thanks.

Sincerely,

Hany.

---

### Post by drs305 on 2009-02-18
We need to see what the errors are to determine why synaptic won't start.

You can first try to fix it with:
```

sudo apt-get install -f

```

See if you get an indications or error messages by running the following:
```

gksudo synaptic
sudo apt-get update
sudo apt-get upgrade

```

---

