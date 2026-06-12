---
title: "Unable to connect to LXDE desktop using X2GO"
date: 2015-12-11
forum: Networking &amp; Wireless
---

### Post by peter1897 on 2015-12-11
I have Ubuntu server 14.04 installed on virtualbox on my laptop with Windows 7. I installed LXDE desktop on the Ubuntu server and i am trying to connect to it with X2GO.

I installed the lxde desktop with this command:
```
sudo apt-get install --no-install-recommends lubuntu-desktop
```

Then i installed the x2go server with these commands:
```
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver x2goserver-xsession
```

I can login in lxde desktop from the virtualbox interface, and i can login to the ubuntu server through ssh (i am using Cygwin).
But if i try to connect with the X2GO client, i am using the client for Windows, it trying to connect but in the end the connection terminates and i get this error: **Unable to execute startlxde**

The session type is LXDE and i tried with different screen resolution options but with no success.

Any idea why X2GO can't connect to the lxde desktop?

---

### Post by peter1897 on 2015-12-11
It seems that the problem was fixed after i run the command:
```
sudo apt-get install --no-install-recommends lxde
```
Now i can connect to the lxde desktop with X2Go.


Can someone explain me what is the difference between these two commands:
```
sudo apt-get install --no-install-recommends lubuntu-desktop
```
and
```
sudo apt-get install --no-install-recommends lxde
```

I thought their are the same.

---

