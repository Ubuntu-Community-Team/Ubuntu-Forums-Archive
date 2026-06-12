---
title: "NEED HELP for CANON IP1000 in UBUNTU8.10"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by rawrico on 2009-04-21
Hi,i try to install the driver i get from canon or somewhere,while i going to install the .deb installation files
it shows up
"dependency not satisfiable: libglib 1.2"
what should i do?
i google it and i found that intrepid is using the libglib1.2-"something else" to have it install,but still not work for me to install the canon ip1000 printer

guys,any solution?

---

### Post by finer recliner on 2009-04-21
type this in the terminal:

```
sudo apt-get install libglib1.2ldbl
```
this will install the package you need (unless its already installed).

if that doesnt work, try installing this one as well:
```
sudo apt-get install libglib1.2-dev
```

hope this helps you install your printer

---

### Post by rawrico on 2009-04-22
I've tried
Not working,the installer still pops up said that dependency not satisfiable.

is this because the intrepid totally not support the CANON IP1000 ,or what?

---

### Post by finer recliner on 2009-04-22
i think i suggested the wrong pacakge earlier by accident. try this one:

```
sudo apt-get install libglib1.2
```

and then try running your print .deb installer again.

sorry about the mix up.

---

### Post by halitech on 2009-04-22
check here: [http://openprinting.org/show_printer.cgi?recnum=Canon-pixma_ip1000](http://openprinting.org/show_printer.cgi?recnum=Canon-pixma_ip1000)

---

### Post by rawrico on 2009-04-26
> **finer recliner said:**
> i think i suggested the wrong pacakge earlier by accident. try this one:

```
sudo apt-get install libglib1.2
```

and then try running your print .deb installer again.

sorry about the mix up.

i tried that as well
not work
it turn the result after the command is
libglib1.2ldbl
but the libglib1.2ldbl i already install

---

