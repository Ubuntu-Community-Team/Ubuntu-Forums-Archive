---
title: "What is synaptic trying to tell me?"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Jonas thomas on 2011-06-06
Hello,
I've been getting this message when I've been trying to download wine.
I think this is an issue on the the server side.  Is that correct?



```
W: Duplicate sources.list entry http://packages.medibuntu.org/ lucid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ lucid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_non-free_binary-amd64_Packages)
```

---

### Post by TBABill on 2011-06-06
I haven't seen that message before, but have you looked in /etc/apt/sources.list to see if maybe those same repos are listed more than once?

---

### Post by jtarin on 2011-06-06
Your /etc/apt/sources.list has duplicate entries.

---

### Post by lan3y on 2011-06-06
```
gksu gedit /etc/apt/sources.list
```

use this command to take a look and edit out any duplicate entries.

lan3y

---

### Post by jtarin on 2011-06-06
Get the idea yet?:p

---

### Post by Jonas thomas on 2011-06-06
> **jtarin said:**
> Get the idea yet?:p

yep.. (just bock from work).
I'm not sure how that happened..
Thanks

---

