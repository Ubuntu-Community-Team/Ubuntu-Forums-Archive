---
title: "can't connect to my ubuntu using hostname"
date: 2005-09-28
forum: Networking &amp; Wireless
---

### Post by edeaux on 2005-09-28
I'm having a hard time looking for a solution on my problem regarding connection to my ubuntu using hostname. There's nothing wrong when I use its IP but when I use the hostname that I assigned it won't connect to mysql, ftp or even i can't ping it. Anyway, I'm using private IP (10.0.0.60). Anybody here can help me?

---

### Post by adwait on 2005-09-28
Check the /etc/hosts file on the pc from where you are trying to connect? It should have your IP and hostname...
```

sudo vi /etc/hosts

```

---

### Post by edeaux on 2005-09-28
[QUOTE=adwait]Check the /etc/hosts file on the pc from where you are trying to connect? It should have your IP and hostname...
```

sudo vi /etc/hosts

```[/QUOTE]

127.0.0.1 localhost.localdomain localhost Server-02
the above line is the original setting in my hosts file. I omitted posting here the IPV6 settings. Server-02 is my hostname. 

I added this line to my hosts file -> "10.0.0.3 Server-02" and removed the Server-02 in the original line of 127.0.0.1. The added line didn't solve my problem. :( 

Another question. How to change from DHCP to static IP. I installed my Ubuntu using server installation so no GUI to change it.

---

### Post by edeaux on 2005-09-29
bump

---

### Post by adwait on 2005-09-29
I meant  that you should alter the /etc/hosts of the computer on which you are trying to ACCESS this computer (ie: server-02).

---

### Post by heimo on 2005-09-29
[quote=edeaux]
Another question. How to change from DHCP to static IP. I installed my Ubuntu using server installation so no GUI to change it.[/quote] 
Edit /etc/network/interfaces (see *man interfaces *for syntax).
```
iface eth0 inet static
        address 10.0.0.3
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.1

``` modify to reflect your correct settings

---

### Post by edeaux on 2005-09-29
[QUOTE=adwait]I meant  that you should alter the /etc/hosts of the computer on which you are trying to ACCESS this computer (ie: server-02).[/QUOTE]

yes. I alteration I've made is on the PC (Server-02) that i'm talking about.

---

### Post by edeaux on 2005-09-30
bump!

---

### Post by lobner on 2007-04-16
Why is it nessesary to add the hostname to the hosts file?

Can't Ubuntu find out via DHCP which computeres are on the LAN?

I know its an old thread... it was just the answer I sought though :)

-Søren

---

