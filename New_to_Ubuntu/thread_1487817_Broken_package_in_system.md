---
title: "Broken package in system"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by W.A on 2010-05-19
Hi!
I tried installing an application through Ubuntu Software Center, but I got an error-message saying that the "Package installation or removal failed".

It told me to run *sudo dpkg --configure -a* and so I did. However it did apparently only solve one problem. I've tried different methods, but I've only gotten so far so I know there is a broken package somewhere. I tried using the synaptic broken filter. After that I don't receive the error-message, but I can still not install anything.

I also tried running *sudo aptitude remove sun-java6-jre *

Some help?

---

### Post by apjone on 2010-05-19
Please try 

```
sudo dpkg-reconfigure -a
```

---

### Post by wojox on 2010-05-19
You could also try:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

A couple of times.

---

### Post by W.A on 2010-05-19
I ran it and a lot of things happened.

When I tried to install new software I received an error-message again.

"E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch): Processing triggers for python-central ..."

---

### Post by W.A on 2010-05-19
Thanks wojox! It worked when I ran 

```
*sudo apt-get install -f*
```

---

### Post by Soul-Sing on 2010-05-19
If you haven't sign the license of sun java your are left with a broken package. You remove it via:

```
sudo dpkg --remove --force-remove-reinstreq sun-java6-jre 
```

---

