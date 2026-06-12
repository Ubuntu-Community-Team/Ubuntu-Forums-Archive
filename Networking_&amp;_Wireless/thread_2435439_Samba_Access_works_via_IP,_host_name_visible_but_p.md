---
title: "Samba: Access works via IP, host name: visible but password doesn't work"
date: 2020-01-20
forum: Networking &amp; Wireless
---

### Post by idodat on 2020-01-20
I am using Ubuntu Server 18.04 LTS.

I have samba configured and I can access shares via the IP address from windows 10 in the form \\w.x.y.z\ShareName.   It requests login information, and when entered it works fine.

When I try to access the same server via address \\servername it shows the appropriate shares.  But when I click into \\servername\ShareName it requests a password but never accepts it.  I have looked online for solutions and see plenty where the server is not accessible at all via hostname, but not where it is accessible but won't take the password, yet works via IP.

Any help would be appreciated. 

Thanks

John

---

### Post by Morbius1 on 2020-01-21
That is a rather odd symptom.

I would suggest trying to access the Server by it's mDNS name ( host name with a .local attached at the end ) to see if that works.

You need to install avahi on the server first:
```
sudo apt install avahi-daemon
```
Then restart smbd:
```
sudo service smbd restart
```
On the Win10 machine access the server this way:
```
\\servername.local\ShareName
```

---

### Post by idodat on 2020-01-24
> **Morbius1 said:**
> That is a rather odd symptom.

I would suggest trying to access the Server by it's mDNS name ( host name with a .local attached at the end ) to see if that works.

You need to install avahi on the server first:
```
sudo apt install avahi-daemon
```
Then restart smbd:
```
sudo service smbd restart
```
On the Win10 machine access the server this way:
```
\\servername.local\ShareName
```


That was it!  I can access it using name.local (already had the avahi daemon installed).  All I had to do was remove local from the domainname, and all is right with the world :)  Thank you for the help!

John

---

