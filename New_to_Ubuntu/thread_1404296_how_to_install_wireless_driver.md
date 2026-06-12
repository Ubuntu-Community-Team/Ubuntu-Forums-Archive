---
title: "how to install wireless driver"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by aab001 on 2010-02-11
i am new with laptop ubuntu
i don't know how can i install the wireless driver for my laptop dell latitude e6400
pls help me

---

### Post by skymera on 2010-02-11
Hi

Can you post the output of ```
 lspci 
``` and ```
 lsusb 
```

---

### Post by 73ckn797 on 2010-02-11
If the above commands show the wireless card you may want to install "ndisgtk" from the Synaptic Package Manager. From that you could try installing the Windows driver from the laptop utility CD, if it has one.

---

### Post by theozzlives on 2010-02-11
I've found with my laptop and Karmic, I had to install plugged in to a wired connection so it can download the drivers.

---

### Post by 73ckn797 on 2010-02-11
> **theozzlives said:**
> I've found with my laptop and Karmic, I had to install plugged in to a wired connection so it can download the drivers.
This also.

---

