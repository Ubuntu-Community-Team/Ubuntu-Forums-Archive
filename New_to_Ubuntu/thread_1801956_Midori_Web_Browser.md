---
title: "Midori Web Browser"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by Old-un on 2011-07-11
Have downloaded the Midori web browser from Synaptic and when i try to open Midori i get the following error message:

Error - file:///usr/share/ubuntu-artwork/home/index.html

The page 'file:///usr/share/ubuntu-artwork/home/index.html' couldn't be loaded.

Error opening file: No such file or directory

---

### Post by abybaddi on 2011-07-11
> **Old-un said:**
> Have downloaded the Midori web browser from Synaptic and when i try to open Midori i get the following error message:

Error - file:///usr/share/ubuntu-artwork/home/index.html

The page 'file:///usr/share/ubuntu-artwork/home/index.html' couldn't be loaded.

Error opening file: No such file or directory

That; in my opinion might be the home-page of the browser. Try changing it.

---

### Post by sanderd17 on 2011-07-11
> **abybaddi said:**
> Try changing it.

Or create the file:

```

sudo touch /usr/share/ubuntu-artwork/home/index.html

```

---

### Post by philinux on 2011-07-11
> **sanderd17 said:**
> Or create the file:

```

sudo touch /usr/share/ubuntu-artwork/home/index.html

```

This file /usr/share/ubuntu-artwork/home/index.html is the Ubuntu welcome screen.

 I just installed midori it displays fine. OP have you got java installed ok?

---

### Post by abybaddi on 2011-07-11
> **sanderd17 said:**
> create the file.


What? You expect him to make the **whole** html page???

---

### Post by philinux on 2011-07-11
> **abybaddi said:**
> What? You expect him to make the **whole** html page???

If his file is missing here it is. I've just changed the file extension to upload it. Would need changin back to html

---

### Post by abybaddi on 2011-07-11
Rename index.txt to index.html and then,
```

sudo cp -t "address of index.html" /usr/share/ubuntu-artwork/home/

```

---

### Post by sanderd17 on 2011-07-11
> **abybaddi said:**
> What? You expect him to make the **whole** html page???

An empty file would display an empty page, at least midori would not complain and you can change the homepage afterwards. In a lot of cases, placing an empty substitute file to get around an error can help.

But off coarse, you could put the html page there like said in the two previous posts.

---

### Post by BillB0B on 2012-08-26
> **sanderd17 said:**
> Or create the file:

```

sudo touch /usr/share/ubuntu-artwork/home/index.html

```

Thanks work like a charm !


Thank you for you time and effort\\:D/

---

### Post by ubudog on 2012-08-26
Old thread closed.

---

