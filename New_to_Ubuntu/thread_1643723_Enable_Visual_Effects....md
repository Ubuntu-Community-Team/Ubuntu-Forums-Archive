---
title: "Enable Visual Effects..."
date: 2010-12-12
forum: New to Ubuntu
---

### Post by ramoj02 on 2010-12-12
I installed Ubuntu Netbook 10.10 on my netbook but I didn't like the new "Unity" thing. So I switched the environment to Ubuntu Desktop. The only thing I can't do on Ubuntu Desktop is change the visual effect to 'Normal' from 'None'... because it's like disabled. So, how do I enable it without re-installing Ubuntu Desktop?

---

### Post by sikander3786 on 2010-12-12
Which graphics card is there?

```
lspci | grep VGA
```

Are the proper drivers installed (if available)? Look under System > Administration > Additional Drivers.

---

### Post by ramoj02 on 2010-12-12
> **sikander3786 said:**
> Which graphics card is there?

```
lspci | grep VGA
```

Are the proper drivers installed (if available)? Look under System > Administration > Additional Drivers.

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

And yes, the proper drivers are installed.

---

### Post by sikander3786 on 2010-12-12
> **ramoj02 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

And yes, the proper drivers are installed.
Intel drivers don't need to be installed separately. Did you install some? What is being listed under Additional Drivers?

---

### Post by ramoj02 on 2010-12-12
> **sikander3786 said:**
> Intel drivers don't need to beinstalled separtaly. Did you install some? What is being listed under Additional Drivers?

I'm sorry about the confusion...

I didn't actually install any driver for my graphics card. And there's nothing listed under Additional Drivers.

---

### Post by sikander3786 on 2010-12-12
It is netbook edition so compiz might not be installed by default.

Applications > Accessories > Terminal

```
sudo apt-get install compiz
```

---

### Post by ramoj02 on 2010-12-13
> **sikander3786 said:**
> It is netbook edition so compiz might not be installed by default.

Applications > Accessories > Terminal

```
sudo apt-get install compiz
```

That was easy. :) Thanks!

---

