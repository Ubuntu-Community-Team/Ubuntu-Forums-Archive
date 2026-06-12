---
title: "xubuntu and vsftpd"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by John_51 on 2009-10-10
Is it possible to install vsftp on xubuntu. I tried sudo apt-get install vsptpd but it didn't work. Also it is not listed in synaptic.

---

### Post by swoody on 2009-10-13
> **John_51 said:**
> I tried sudo apt-get install vsptpd
The package I think you're looking for is vsftp and it's available in the Ubuntu main repository. In the 'Software Sources' app, make sure your repos are all enabled. Then  in a terminal run:
```
sudo apt-get update && sudo apt-get isntall vsftp
```

---

### Post by pricetech on 2009-10-13
You don't say which version of the XUbuntu you are using so I didn't include a link, but the Official Documentation has a couple of pages on vsftp that covers it all.

For me it's been one of those things that "just works"

---

