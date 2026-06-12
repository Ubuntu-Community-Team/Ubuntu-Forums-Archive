---
title: "security update error..."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by tongueman on 2009-01-15
complete newbie here, just been going with the flow using ubuntu, installing updates automatically etc. however the latest update returned the following message and will not update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have no idea what this means or what to do. please help.

---

### Post by spikoley on 2009-01-15
Run the command like the error says.

```
sudo dpkg --configure -a
```

Then
```
sudo apt-get update
```

---

### Post by tongueman on 2009-01-15
brilliant!! back on form

thanks a lot spikoley.

think maybe i should be less ignorant and learn a little about linux and ubuntu.

thanks again.

---

