---
title: "how to change drivers used by ndiswrapper"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by luvit on 2008-03-23
I would like to change the driver used by ndiswrapper.
Can someone provide complete steps to ensure I won't miss a required steps or file edit?

Thank you so much. My eyes are bugging out from all my wireless trouble.

**[COLOR="Red"]EDIT: My problem is solved in another thread... so no answer to this is required, but an answer would be valuable.[/COLOR]**

---

### Post by coolbrook on 2008-03-23
In terminal...

```

sudo ndiswrapper -r  unwanteddriver.inf
sudo ndiswrapper -i  /pathto/wanteddriver.inf
```

check with 

```
ndiswrapper -l
```

---

