---
title: "ndiswrapper problem"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2008-06-21
I was loading my driver into ndiswrapper and got an error... now I can't get it to remove the errored out driver.

I tried completely removing ndiswrapper and reinstalling it, then installing my driver again and I get an error that says "couldn't open /dir/to/driver/net8187b.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181"

So.... now what?

---

### Post by oodlesOfmoodles on 2008-06-21
> **knottshawk said:**
> I was loading my driver into ndiswrapper and got an error... now I can't get it to remove the errored out driver.

I tried completely removing ndiswrapper and reinstalling it, then installing my driver again and I get an error that says "couldn't open /dir/to/driver/net8187b.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181"

So.... now what?
I'm not exactly sure of your experience but can you post the directory of the driver (what folder it's in)?

Also, can you try to cd to it?

```
cd /dir/to/driver/
```

---

### Post by knottshawk on 2008-06-21
The directory? /etc/ndiswrapper/net8187b

And yes, I can CD to it... I've tried removing it and starting over and I keep getting the same error.

---

### Post by oodlesOfmoodles on 2008-06-21
> **knottshawk said:**
> The directory? /etc/ndiswrapper/net8187b

And yes, I can CD to it... I've tried removing it and starting over and I keep getting the same error.
OK great!

Can you type
```
ls
```

after you have cd'd into it (and post the output)?

---

### Post by knottshawk on 2008-06-21
yeah... ls shows nothing.

But if I try to install again (sudo ndiswrapper -i /dir/to/driver/net8187b.inf) it says driver is already installed... then if I do "sudo ndiswrapper -l" it says "net8187b: invalid driver!".. which isn't true. This is the same driver I have used before on this system.

The mistake I made was I tried to install the .inf file earlier without the accompanying .cat and .sys files in the directory with it... I got an error and now everything is hosed.

---

### Post by knottshawk on 2008-06-22
Fixed... ndiswrapper -e (not -r) removed it... thanks!

---

### Post by oodlesOfmoodles on 2008-06-22
can you type:

```
sudo ndiswrapper -v
```

You may have an obsolete version.

Thanks!

---

