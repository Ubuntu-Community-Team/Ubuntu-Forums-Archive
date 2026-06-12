---
title: "How can I get Unity in 10.04"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Mindswap1 on 2011-01-26
Hi guys! How can I get Unity in Ubuntu 10.04? I don't want to use the netbook remix version. I tried adding it from the following ppa but it doesn't work any other options.
> 
sudo apt-add-repository ppa:canonical-dx-team/une

---

### Post by davidmohammed on 2011-01-26
unity is only available for natty - or you can use the new 2D version of unity via a ppa for maverick.

---

### Post by wojox on 2011-01-26
```
sudo apt-get update && sudo apt-get install unity
```

---

### Post by Mindswap1 on 2011-01-26
I tried sudo apt-get update and sudo apt-get install Unity but it doesn't work. It says no such package found.

---

### Post by wojox on 2011-01-26
I didn't see davidmohammed's post. I guess you can't download it with out une.

```
sudo apt-get install ubuntu-netbook-unity-default-settings
```


> I don't want to use the netbook remix version

It's the same thing. :P

---

