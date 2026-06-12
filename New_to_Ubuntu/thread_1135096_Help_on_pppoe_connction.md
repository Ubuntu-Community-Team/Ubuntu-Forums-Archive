---
title: "Help on pppoe connction"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by daie3 on 2009-04-24
Hi i installed ubuntu with windows xp i have broadband connection from windows i connect to internet but when i switch to ubuntu i cant i put my user name and passwd but it refused from the isp plzz help

---

### Post by duanedesign on 2009-04-24
> **daie3 said:**
> Hi i installed ubuntu with windows xp i have broadband connection from windows i connect to internet but when i switch to ubuntu i cant i put my user name and passwd but it refused from the isp plzz help

Open a terminal (Applications &#8594; Accessories &#8594; Terminal)

In the terminal, type

```
sudo pppoeconf
```

A text-based menu program will guide you through the following steps:

   1.Confirm that your Ethernet card is detected.

   2.Enter your username.

   3.Enter your password.

   4.If you already have a PPPoE Connection configured, you will be asked if it may be modified.

   5. Popular options: you are asked if you want the “noauth” and “defaultroute” options and to remove “nodetach”- Choose Yes.

   6.Use peer DNS - choose Yes.

   7. Limited MSS problem - choose Yes.

   8. When you are asked if you want to connect at start up, you will probably want to say yes.

   9. Finally you are asked if you want to establish the connection immediately.

If that does not work here is a troubleshooting guide:

[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

---

### Post by daie3 on 2009-04-24
Hi thanks i do it before but when i type blog it come the connction terminated from the host could it be because of my intelpro100ve network card mac address does it cahnge from windows platform to ubuntu

---

