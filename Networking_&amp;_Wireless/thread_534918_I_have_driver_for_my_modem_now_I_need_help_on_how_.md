---
title: "I have driver for my modem now I need help on how to dial my internet connection!"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by s3a on 2007-08-25
The title says it pretty much but, to be more specific, I have two files "gnome-ppp_0.3.23-1_i386.deb" as well as my driver. I have the driver installed succesfully, however, now I am stuck into what to do next. Someone please tell me _exactly_ where to click, etc. I am using Ubuntu 7.04 (Feisty Fawn) 32-bit.

Thanks in advance!

---

### Post by Bachstelze on 2007-08-25
If you don't say which driver and how you instaled it, I'm afraid no one can help...

---

### Post by Patrick793 on 2007-08-25
> **s3a said:**
> The title says it pretty much but, to be more specific, I have two files "gnome-ppp_0.3.23-1_i386.deb" as well as my driver. I have the driver installed succesfully, however, now I am stuck into what to do next. Someone please tell me _exactly_ where to click, etc. I am using Ubuntu 7.04 (Feisty Fawn) 32-bit.

Thanks in advance!

I don't know about dial up, but if you have a PPPoE connection, type this in the terminal.
```
sudo pppoeconf
```

---

### Post by s3a on 2007-08-25
> **HymnToLife said:**
> If you don't say which driver and how you instaled it, I'm afraid no one can help...

I put the driver in my sig!

Thanks!

---

### Post by s3a on 2007-08-25
> **Patrick793 said:**
> I don't know about dial up, but if you have a PPPoE connection, type this in the terminal.
```
sudo pppoeconf
```

What's a PPPoE connection and how to I find out whether I have such a connection or not?

Thanks!

---

### Post by Bachstelze on 2007-08-25
> **s3a said:**
> What's a PPPoE connection and how to I find out whether I have such a connection or not?

You don't. Please open a terminal, run *sudo wvdialconf /etc/wvdial.conf* and paste what you get.

---

### Post by Patrick793 on 2007-08-25
*removed by poster*

---

### Post by s3a on 2007-08-25
> **HymnToLife said:**
> You don't. Please open a terminal, run *sudo wvdialconf /etc/wvdial.conf* and paste what you get. I am waiting for files to copy to other HDD and it'll take a couple hours because I am using USB 1.1. And, I'm in Windows XP Pro... So, I'll check back as soon as it's done!

Thanks!

---

