---
title: "Internet connecion on startup"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by alket on 2008-12-30
Everytime that i turn on my PC
firstly I must change my Mac Address
```
sudo ifconfig eth1 down
sudo ifconfig eth1 hw ether 00:00:!!:!!:!!..
sudo ifconfig eth1 up
sudo pppoeconf
```

then i must configure
pppoeconf

in order to connect in internet

How can i make like
when i start my pc, it automatically to connect
or just with one click
???

---

### Post by ET! on 2008-12-30
what version of ubuntu you use??

---

### Post by alket on 2008-12-30
> **ET! said:**
> what version of ubuntu you use??

The last version, and i have all last updates

---

### Post by zika on 2008-12-30
several ideas:

1. if You are using NetworkManager correct the MAC address in the options therein
2. make an entry in System->Preferences->Sessions with a command line looking as: ```
ifconfig eth1 down && ifconfig eth1 hw ether 00:00:!!:!!:!!.. && ifconfig eth1 up && pppoeconf 
``` that way You could turn it on/off on will.
3. put ```
ifconfig eth1 down
ifconfig eth1 hw ether 00:00:!!:!!:!!..
ifconfig eth1 up
pppoeconf
```in Your /etc/rc.local
4. make an Application Launcher (either on Desktop or on one of the panels) with the command line looking as:```
sudo ifconfig eth1 down && sudo ifconfig eth1 hw ether 00:00:!!:!!:!!.. && sudo ifconfig eth1 up && sudo pppoeconf 
```... maybe this will do ... :)
(I did not check for validity of sintax of commands since You said they work ...)

---

### Post by alket on 2009-03-12
It works but im really tired of this,
I need it on startup or in one click
because with that method, i still must configure the pppoeconf

---

### Post by zika on 2009-03-12
> **babaroga said:**
> It works but im really tired of this,
I need it on startup or in one click
because with that method, i still must configure the pppoeconf
did You try editing the file */etc/ppp/peers/dsl-provider or /etc/ppp/peers/provider?* if You make it right You could wipe the line pppoeconf and ...
also see *man pppd*.

---

### Post by alket on 2009-03-12
i opened first one
/etc/ppp/peers/dsl-provider

it shows some lines and in the end my username
```
user "xxx"
```

is it possible to add password there ?

---

### Post by zika on 2009-03-12
> **babaroga said:**
> i opened first one
/etc/ppp/peers/dsl-provider
it shows some lines and in the end my username
```
user "xxx"
```is it possible to add password there ?
I've never tried anything regarding pppd so that is why I pointed to **man pppoeconf** and **man pppd**. there is a description how to use files */etc/ppp/pap-secrets*  and  */etc/ppp/chap-secrets  *and that might help You.

---

### Post by alket on 2009-03-15
No it didnt help me, can anyone tell me how ?

---

