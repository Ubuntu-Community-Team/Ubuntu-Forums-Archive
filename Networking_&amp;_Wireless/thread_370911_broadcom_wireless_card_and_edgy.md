---
title: "broadcom wireless card and edgy"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by czambran on 2007-02-26
Has anybody been able to have a broadcom based wireless card work on edgy?

---

### Post by ukripper on 2007-02-26
> **czambran said:**
> Has anybody been able to have a broadcom based wireless card work on edgy?

Yes I am using bcm4318 with my laptop. You might need to use ndiswrapper if you trying to install drivers for brodcom chipsets

---

### Post by czambran on 2007-02-26
I tried using ndiswrapper, but that was after I tried using fwcutter, and it didn't work either.  I had no problem having it work using fwcutter under Dapper.

Do you have a link to a good How-To on how to get it to work?

---

### Post by ukripper on 2007-02-26
> **czambran said:**
> I tried using ndiswrapper, but that was after I tried using fwcutter, and it didn't work either.  I had no problem having it work using fwcutter under Dapper.

Do you have a link to a good How-To on how to get it to work?

Do you know the chipset ? Something like bcmxxxx

---

### Post by czambran on 2007-02-26
bcm4306

---

### Post by icantdothatdave on 2007-02-26
I am also unable to get my 4309 working in Edgy. I have been working on this for weeks now, and neither the bcm43xx method, nor the ndiswrapper method works. Please help!

---

### Post by ukripper on 2007-02-27
> **czambran said:**
> bcm4306

Here you go, Below is the most simplest guide to follow to get your 4306 working:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306)

Goodluck.

---

### Post by ukripper on 2007-02-27
> **icantdothatdave said:**
> I am also unable to get my 4309 working in Edgy. I have been working on this for weeks now, and neither the bcm43xx method, nor the ndiswrapper method works. Please help!


Need more information 

Can you paste your iwconfig and ifconfig -a here.

Also paste output of $ sudo gedit /etc/network/interfaces.

---

### Post by TheFourthOne on 2007-03-03
Try this post...

[http://www.ubuntuforums.org/showthread.php?t=336559&highlight=broadcom+4309](http://www.ubuntuforums.org/showthread.php?t=336559&highlight=broadcom+4309)

---

