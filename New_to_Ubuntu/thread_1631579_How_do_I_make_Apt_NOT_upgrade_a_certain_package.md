---
title: "How do I make Apt NOT upgrade a certain package"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by hovzio on 2010-11-26
Hi, 

    I just did a fresh install (10.10) and got everything set up, everything works great except ettercap. (Crashes as soon as I scan hosts) So I got a different deb from somewhere within launchpad and it works like a charm.. the problem is every time I do an update it also updates ettercap to the unwanted version (the one I'm using is an older version but it works) How do I prevent Apt from updating this package?

---

### Post by bananas4370 on 2010-11-26
> **hovzio said:**
> Hi, 

    I just did a fresh install (10.10) and got everything set up, everything works great except ettercap. (Crashes as soon as I scan hosts) So I got a different deb from somewhere within launchpad and it works like a charm.. the problem is every time I do an update it also updates ettercap to the unwanted version (the one I'm using is an older version but it works) How do I prevent Apt from updating this package?

You should be able to find the package you installed in synaptic. Highlight it and go to Package and tick Lock Version

Cheers
Patrick

---

### Post by wilee-nilee on 2010-11-26
> **bananas4370 said:**
> You should be able to find the package you installed in synaptic. Highlight it and go to Package and tick Lock Version

Cheers
Patrick

+1 that is the answer.;)

---

### Post by hovzio on 2010-11-26
Thanks:) how would I do this on my server, no X running? I assume it would involve dpkg or so but I'm not really finding it. Thanks again

---

### Post by bananas4370 on 2010-11-26
> **hovzio said:**
> Thanks:) how would I do this on my server, no X running? I assume it would involve dpkg or so but I'm not really finding it. Thanks again

I haven't done it this way, but this community documentation on [pinning]("https://help.ubuntu.com/community/PinningHowto") may help.

Cheers
Patrick

---

### Post by hovzio on 2010-11-26
Thanks bannanas, pinning seems to be the key word here, from what I can tell this is what needs to be done:
as root

```
echo [Package Name] hold | dpkg --set-selections
```

---

### Post by bananas4370 on 2010-11-26
> **hovzio said:**
> Thanks bannanas, pinning seems to be the key word here, from what I can tell this is what needs to be done:
as root

```
echo [Package Name] hold | dpkg --set-selections
```

I just tried with

```
echo [Package Name] hold | sudo dpkg --set-selections
```

and then using --get-selections, the package showed hold next to it.

Cheers
Patrick

---

