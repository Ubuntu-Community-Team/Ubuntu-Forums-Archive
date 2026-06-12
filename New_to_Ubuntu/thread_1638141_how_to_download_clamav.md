---
title: "how to download clamav"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by mayt on 2010-12-05
i want to download clamav but when i search it in the software i several packages that say clamav which do i download? also is there a firewall i can download or any other anti virus software

---

### Post by coffeecat on 2010-12-05
Before you decide whether or not you need antivirus and/or a configurable firewall, please read this sticky on security written by one of the forum admins. Please do read it; it will clarify some of the preconceptions you may have brought over from Windows.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by arjunlalb on 2010-12-05
to download clamav

go to terminal and type

' sudo apt-get install clamav '

You will have to enter ur password when using sudo command

Firestarter is a good firewall for ubuntu
 
You can install it by.

Go to terminal; type 

' sudo apt-get install firestarter'

All the best.

---

### Post by MrWES on 2010-12-05
The standard/default firewall is ufw (uncomplicated firewall), and the GUI is gufw.

You can install them from the Software Center or from the terminal:

```
sudo apt-get install ufw
```
and
```
sudo apt-get install gufw
```

Bill

---

