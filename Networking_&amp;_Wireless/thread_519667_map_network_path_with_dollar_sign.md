---
title: "map network path with dollar sign?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by jenast on 2007-08-07
My server share at work has a path with a dollar sign in it which I cannot figure out how to express.

It's in the form:
//network-server-name/directory$/employees/me

But so far I have only been able to map to .../directory$ and not the whole way to my directory. I currently use a workaround with a symbolic link but I would like to know how to map it directly.

I have tried an \ before the $ sign as well as '-brackets around the whole network path name but no luck.

Any ideas?

---

### Post by dmizer on 2007-08-07
try adding the "mapchars" option to your mount line like so:

```
mount -t cifs //network-server-name/directory$/embloyees/me /mount/point -o [COLOR="Red"]mapchars[/COLOR],username=winusername,password=winpassword,file_mode=0777,dir_mode=0777
```

if that doesn't work, try wrapping the location in quotes like so:
//network-server-name/"directory$"/employees/me

---

### Post by jenast on 2007-08-08
Thanks for the reply,

Did try that just now but it did not work.
I also read that "mapchar" handles other special characters (nut not $) somewhere.

Will continue to try different things if no one has another idea...

---

### Post by jose1711 on 2008-02-05
replace $ with \044 and you are all set.

jose

---

