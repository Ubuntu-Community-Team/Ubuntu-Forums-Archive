---
title: "kernel proplem"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Ghost M.D on 2009-02-11
hi all

yesterday my kernel lost some files after I delete KDE 4.1

because I after I install it my coumputer gets unstable

however I tried to reinstall it after I longed on form another kernel ((older one ))

I wrote this for reinstalling 

```
sudo apt-get --reinstall kernel 2.6.27-11-generic
```

but the E was

```
E: Invalid operation kernel
```

what I can do  

can I delete it & update

I tried & 

```
 sudo apt-get remove kernel 2.6.27-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel

```

so what I do now..??

---

### Post by drs305 on 2009-02-11
The command would be:
```
sudo apt-get **install --reinstall linux-image-2.6.27-11-generic**
```

For an apt-get command, you need the *install* portion of the command. Generally, "--xxxxx" is a switch which adds options to the original command. In this case, you are asking apt-get to *install*, with an option (--reinstall) to reinstall a package. In this case, the linux kernel is designated as "linux-image-xxxxx".

---

### Post by compiledkernel on 2009-02-11
There is a dash after kernel I believe.

---

### Post by Ghost M.D on 2009-02-11
> **drs305 said:**
> The command would be:
```
sudo apt-get **install --reinstall linux-image-2.6.27-11-generic**
```

For an apt-get command, you need the *install* portion of the command. Generally, "--xxxxx" is a switch which adds options to the original command. In this case, you are asking apt-get to *install*, with an option (--reinstall) to reinstall a package. In this case, the linux kernel is designated as "linux-image-xxxxx".

thank you so much the kernel back to work

& thanks for the new information

---

