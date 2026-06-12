---
title: "server mounting external HDD by Maxtor"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by breeness on 2010-06-27
Hi guys,

thanks so far for all the help so far!!

So, I have this external hard drive and I am trying to mount it, but I don't think ubuntu server is able to "see" it. When I do command: "df" or "fdisk -l", I don't see my 250gig hard drive listed.

I don't know what's wrong? Please help me mount this disk :D thanks!

---

### Post by nhasian on 2010-06-27
we'll need a bit more info to help you.  do you have the make/model of the external drive you are trying to mount? Is it USB, eSATA, firewire? does it require external power and if so, is it plugged in and on?

if its a usb external drive, see if its detected with the following terminal command:

```
lsusb
```

then please give us the output of the following terminal commands:

```
sudo blkid
```

```
sudo fdisk -l
```

```
mount
```

---

### Post by CharlesA on 2010-06-27
Yup need more info. I've hooked up USB drives to my box running 10.04 Server and it sees the drive immediately.

---

### Post by breeness on 2010-06-27
I just lost my install or something. I couldn't get back iinto the ubuntu server terminal, even right at the linux box...

last thing I did was sudo reboot :(

---

### Post by CharlesA on 2010-06-27
What does it do?

---

