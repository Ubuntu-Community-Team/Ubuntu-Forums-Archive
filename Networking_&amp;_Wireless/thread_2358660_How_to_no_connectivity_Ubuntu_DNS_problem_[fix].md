---
title: "How to no connectivity Ubuntu DNS problem [fix]"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by jonathonp on 2017-04-16
I installed Ubuntu 17.04 and Ubuntu-Mate 17.04 and found i had no INTERNET access. It looked like a problem with DNS.

Here are some simple solutions to the problem:

**Method 1:**

Open a terminal and copy and paste the following:

```
sudo gedit /etc/resolvconf/resolv.conf.d/tail
```

Add the following:

```
nameserver 8.8.8.8
```
 
Click **Save** and **Restart** your computer.


**Method 2**:

Open a terminal and copy and paste the following:

```
sudo gedit /etc/systemd/resolved.conf
```

Uncomment 

```
#DNS
```

and change it to

```
DNS=8.8.8.8
```

Click **Save** and **Restart** your computer.


**Method 3:**

With Network-manager Click *Edit Connections > Wired Connection >  Edit > Ipv4 Settings > Method: Automatic (DHCP) address only >  DNS servers add 8.8.8.8 > Click Save *

Restart your Network Connection or restart your computer.

With this method, if the connection under "Network Connections" is deleted the user will no longer have INTERNET access so i would not recommended it. Choose method 1 or 2 instead.

---

### Post by tea for one on 2017-04-16
I installed Ubuntu Gnome 17.04 on a spare partition and wired internet did not work.

Method 2 in your post solved the difficulty.


Thank you

---

### Post by yesion on 2017-04-16
Methode nr 1 SOLVED my problem with DNS on Ubuntu 17.04    -------  Thank You very much :)

---

### Post by Bob_Bruce on 2017-04-18
The 2nd method worked for me too. Thanks!

---

### Post by andreic9203 on 2017-04-18
The first method works like a charm. Thanks. 
Can you give a briefly explanation about how it works?

Kind regards!

---

