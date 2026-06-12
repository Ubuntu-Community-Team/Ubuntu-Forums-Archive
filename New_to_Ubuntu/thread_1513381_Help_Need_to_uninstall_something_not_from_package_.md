---
title: "Help: Need to uninstall something not from package manager"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-06-19
I installed ruby1.9.1 from source using ```
sudo make install
```. How can I uninstall this? Basically I just don't want 'ruby' to map to ruby1.9.1, but instead the default 1.8.7....

---

### Post by TurnOfTide on 2010-06-19
Anyone can help here? :confused::confused:

---

### Post by oldos2er on 2010-06-19
Go back into the source folder and run **sudo make uninstall**

---

### Post by TurnOfTide on 2010-06-19
This doesn't seem to work :(


```
windsor@windsor-desktop:~/Desktop/ruby-1.9.1-p378$ sudo make uninstall
[sudo] password for windsor: 
make: *** No rule to make target `uninstall'.  Stop.
windsor@windsor-desktop:~/Desktop/ruby-1.9.1-p378$ 


```

---

### Post by gandaran on 2010-06-19
> **TurnOfTide said:**
> This doesn't seem to work :(


```
windsor@windsor-desktop:~/Desktop/ruby-1.9.1-p378$ sudo make uninstall
[sudo] password for windsor: 
make: *** No rule to make target `uninstall'.  Stop.
windsor@windsor-desktop:~/Desktop/ruby-1.9.1-p378$ 


```

you have to run exactly the same commands you used to build the package in same order, only when it comes to make install you change to make uninstall instead.

---

### Post by HermanAB on 2010-06-19
Read the makefile, see where it installed the schtuff to and delete it.

---

