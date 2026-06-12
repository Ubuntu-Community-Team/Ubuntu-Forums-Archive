---
title: "Updating from synaptic"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by phil66 on 2009-07-21
Ubuntu Hardy

When updating files from synaptic on certain files I get  a 404 error:

[Http://archive.ubuntu.com/ubuntu/pool/main](Http://archive.ubuntu.com/ubuntu/pool/main)

When I add as listed in sources.list I get a malformed line error.

What is the proper script for this repository

---

### Post by ~sHyLoCk~ on 2009-07-21
> **phil66 said:**
> Ubuntu Hardy

When updating files from synaptic on certain files I get  a 404 error:

[Http://archive.ubuntu.com/ubuntu/pool/main](Http://archive.ubuntu.com/ubuntu/pool/main)

When I add as listed in sources.list I get a malformed line error.

What is the proper script for this repository
Shouldn't it be "http" instead of "Http" ?

And your sources are added as ```
deb http://packages.medibuntu.org/ jaunty free non-free
```

---

### Post by phil66 on 2009-07-21
> **~sHyLoCk~ said:**
> Shouldn't it be "http" instead of "Http" ?

And your sources are added as ```
deb http://packages.medibuntu.org/ jaunty free non-free
```

I had deb and http in the code and that did not work

Added your code and still getting the error file not found. With the code as in my first post above.

---

