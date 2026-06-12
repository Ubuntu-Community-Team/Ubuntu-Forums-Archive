---
title: "realplayer.bin problem"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-15
i downloaded realplayer.bin from real.com , i dont know how to install it........
and i need terminal tutorials

---

### Post by aravindc26 on 2009-05-16
pls anyone........help

---

### Post by zeroseven0183 on 2009-05-16
Hi!

You can install RealPlayer in Ubuntu. It's very simple.

1. Open Terminal from **Applications** > **Accessories** > **Terminal**
2. Enter the following command into the **Terminal**
      ```
sudo gedit /etc/apt/sources.list
```
3. Add the line below to the end of the /etc/apt/sources.list file and then save:
```
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
```
4. Type the commands into the Terminal
    ```
sudo apt-get update
sudo apt-get install realplayer
```

5. Run RealPlayer on the command line by typing
    ```
realplayer
```
or open it at **Applications** > **Sound & Video** > **RealPlayer 11**


Sorry for not directly answering your question. Hope that helps.

---

