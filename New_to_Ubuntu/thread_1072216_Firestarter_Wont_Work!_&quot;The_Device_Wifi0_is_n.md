---
title: "Firestarter Wont Work! &quot;The Device Wifi0 is not Ready&quot;"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by 24/7 on 2009-02-17
My wireless card is installed. Firestarter wont work, just always says device is not ready. Does anyone know how to fix it? I dont want to be unprotected for too long. Even with Linux's already great security.

---

### Post by Tews on 2009-02-17
Just use UFW ( uncomplicated Firewall ) 
Open your terminal .. 

```
 sudo ufw enable
```

Need to open a port?

```
sudo ufw allow xxxxx
```

You can Google for a list and explanations of commands

---

### Post by brian_p on 2009-02-17
> **24/7 said:**
> My wireless card is installed. Firestarter wont work, just always says device is not ready. Does anyone know how to fix it? 

Two ideas:

1. Test with a wired connection
2. Read [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by khelben1979 on 2009-02-17
Join [the Firestarter mailing list]("http://www.fs-security.com/list.php") might be a good idea if you like the firewall.

---

### Post by superprash2003 on 2009-02-17
are you trying to share an internet connection?? this is a typical problem with firestarter.. disabling DHCP for wifi0 and setting up static ip would fix it!!

---

### Post by 24/7 on 2009-02-19
Yeh whatever the first guy said didnt work. ummm... yes, im sharing an internet connection with other people on my wireless network, how do i set it up? Dont have any way to test with a wired connection =).

---

### Post by 24/7 on 2009-02-19
> **superprash2003 said:**
> are you trying to share an internet connection?? this is a typical problem with firestarter.. disabling DHCP for wifi0 and setting up static ip would fix it!!

Sorry, how do i disable DHCP and set up a static IP?

---

### Post by igknighted on 2009-02-19
If you pay attention to what services are running and don't turn on ones you don't need, then there is no reason to run a firewall.  I wouldn't think twice about turning off firestarter, and if you are really concerned, a router would be a cheap (and better, from the sounds of it) solution.  Unless you feel comfortable configuring everyone you share connections with to use a static IP address, firestarter simply wont work for you.  UFW might, but this sounds like a setup that would benefit from a hardware firewall... in this case a router.

---

### Post by superprash2003 on 2009-02-19
you should find it in firestarter's settings itself!!when you go through that wizard!!

---

