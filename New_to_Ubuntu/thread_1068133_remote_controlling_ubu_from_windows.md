---
title: "remote controlling ubu from windows"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by dieter964 on 2009-02-12
Is there a way to remotely control my Ubu server from my windows desktop on my local network, similar to running remote desktop in the windows environment?

---

### Post by thegreenblob on 2009-02-12
You could use SSH.

```
sudo apt-get install ssh
```

And then you could use [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") on windows to connect to it.

---

### Post by kanikilu on 2009-02-12
System > Preferences > Remote Desktop

More information on VNC: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by dieter964 on 2009-02-12
I have read the documentation on VINO and realvnc viewer (windows), made the config changes in Remote Desktop, but my realvnc client wont connect to the server. 

I'm on a local network, so the router does not come into play (i can ftp from my windows computer to my Ubu server).

Do i have to do anything special to run the Vino server?  Do i need to run the RealVNC server on the Ubu box?

---

### Post by bodhi.zazen on 2009-02-12
How are you trying to connect ?

ipaddress:5900

ie connect to port 5900.

I second the suggestion of ssh ;)

---

### Post by HermanAB on 2009-02-12
The best way is to install ssh-server on Linux and xming with putty on windows.

Cheers,

Herman

---

