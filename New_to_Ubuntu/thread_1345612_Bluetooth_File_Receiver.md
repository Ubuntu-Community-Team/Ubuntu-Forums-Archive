---
title: "Bluetooth File Receiver"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by lotharmat on 2009-12-04
Hello everyone,

I used to have an application in Jaunty that when ran, would put a little bluetooth Icon in the notification area and basically put my laptop into Bluetooth receive mode (The icon was a little like the shape of a keyhole!)

Since I installed Karmic - clean install, I have been unable to find this fantastic application and am limited to 'Browse Files on Device'

Which although has its uses is not quite as good as 'pushing' a file to my laptop.

Please help.

Thanks.

---

### Post by Excedio on 2009-12-04
I believe that the application you're thinking of is called BlueZ. Check in the Synaptic Package Manager if you have that installed.

---

### Post by lotharmat on 2009-12-04
Cheers!

I removed a lot of the bluetooth utilz and reinstalled Bluez and hey presto!

Some of the lib....etc's are depended upon by a lot of apps!!!

Scared me to death when I marked them for removal! I very quickly un-marked them!

---

### Post by Excedio on 2009-12-04
Glad everything is working for you now. :-)

---

### Post by Excedio on 2009-12-04
Oh and open up a Terminal and type in:
 
```
sudo apt-get autoremove
```
This code will remove any/all unneeded libraries from your system. :-)

---

