---
title: "SystemError: E:Unable to correct problems, you have held broken packa"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Bradtek on 2009-11-04
Ubuntu 9.04
Nvidia GTS 250 1GB

After unsuccessfully trying to get latest Nvidia Driver working 
I un installed all Nvidia drivers in an attempt to start from scratch.
Now the default Restricted Driver shows in  System | Administration | Hardware Drivers, but when tryin to download/install I get this error

SystemError: E:Unable to correct problems, you have held broken packages.

I tried Synaptic Package Manger | Edit | Fix Broken Pacages
but this didnt change the error.

What is the CLI command to fix broken packages and or what else could I try


Thanks in advance.

---

### Post by Bradtek on 2009-11-04
I just tried ```
sudo apt-get install -f

```

It doesn't find any broken packages

---

### Post by Bradtek on 2009-11-04
I seem to have overcome the problem by 
killing X and installing the Nvidia driver manually.

---

### Post by cccy on 2009-11-04
Or you could try reinstalling Ubuntu if you want to be safe . But I think you have solved the problem yourself .

---

### Post by philinux on 2009-11-04
> **cccy said:**
> Or you could try reinstalling Ubuntu if you want to be safe . But I think you have solved the problem yourself .

Re-installing should be considered as a last resort. Most problems can be fixed without resorting to reinstall.

---

