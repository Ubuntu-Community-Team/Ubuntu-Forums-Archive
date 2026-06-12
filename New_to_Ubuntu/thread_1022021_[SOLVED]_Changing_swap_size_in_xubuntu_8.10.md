---
title: "[SOLVED] Changing swap size in xubuntu 8.10"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by dapissarenko on 2008-12-26
Hello!

I want to install Oracle 10 Express edition on my xubuntu 8.10 computer.

The installation fails because I have approx. 600 MB of swap space instead of required 723 MB.

How can I increase the swap partition without re-installing my system?

Thanks

Dmitri

---

### Post by ibutho on 2008-12-26
You could create a swap file. There are instructions [here]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") and [here]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html").

---

### Post by albinootje on 2008-12-26
> **dapissarenko said:**
>  I want to install Oracle 10 Express edition on my xubuntu 8.10 computer.

The installation fails because I have approx. 600 MB of swap space instead of required 723 MB.

How can I increase the swap partition without re-installing my system?


You can temporarily use a swapfile.
```

sudo dd if=/dev/zero of=/swapfile-1 bs=1024 count=500k
sudo swapon /swapfile-1
free -m

```

---

### Post by gn2 on 2008-12-26
You could boot either a Gparted Live CD or an Ubuntu Live CD and use the partition editor.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Remember to back-up first.

---

### Post by dapissarenko on 2009-01-06
Hello!

> **albinootje said:**
> You can temporarily use a swapfile.
```

sudo dd if=/dev/zero of=/swapfile-1 bs=1024 count=500k
sudo swapon /swapfile-1
free -m

```

When I do this, I get following error message:

```
$ sudo swapon -v /swapfile-1 
swapon on /swapfile-1
swapon: /swapfile-1: Invalid argument

```

What am I doing wrong?

TIA

Dmitri

---

### Post by albinootje on 2009-01-06
> **dapissarenko said:**
> 
```
$ sudo swapon -v /swapfile-1 
swapon on /swapfile-1
swapon: /swapfile-1: Invalid argument

```


Excuse me, missed something. Please try :
```

sudo mkswap /swapfile-1
sudo swapon -v /swapfile-1

```

---

### Post by dapissarenko on 2009-01-06
Hello!

Thanks! Now it worked!

Best regards

Dmitri

---

