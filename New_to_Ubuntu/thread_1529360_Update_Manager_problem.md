---
title: "Update Manager problem"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by milanfcb on 2010-07-12
UM worked fine, without problems, but now, it won't start..
I run UM, it checks available packages, I go to install updates, enter the admin pass, and instead of starting the update, it returns again to checking the packages... and it goes all around in circle..
What's the problem?

---

### Post by jtarin on 2010-07-12
Have your tried the same thing in Synaptic?

---

### Post by philinux on 2010-07-12
> **milanfcb said:**
> UM worked fine, without problems, but now, it won't start..
I run UM, it checks available packages, I go to install updates, enter the admin pass, and instead of starting the update, it returns again to checking the packages... and it goes all around in circle..
What's the problem?

Open a terminal, Apps>Access. Copy and the paste the command below.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any errors.

---

