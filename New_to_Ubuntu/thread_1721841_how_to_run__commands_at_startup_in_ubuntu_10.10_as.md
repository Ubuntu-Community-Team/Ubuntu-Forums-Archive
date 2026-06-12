---
title: "how to run  commands at startup in ubuntu 10.10 as root"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by anjexe on 2011-04-05
how to run this commands at start up inubuntu 10.10

sudo insmod acpi_call.ko

./test_off.sh

tnx

---

### Post by Random_Dude on 2011-04-05
> **anjexe said:**
> 
./test_off.sh


Is this one a script written by you?
If so, you can change it's permissions and run it without needing root.

```
sudo chmod +x test_off.sh
```

---

### Post by sanderj on 2011-04-05
> **anjexe said:**
> how to run this commands at start up inubuntu 10.10

sudo insmod acpi_call.ko

./test_off.sh

tnx

Have you tried putting it in /etc/rc.local ?

---

### Post by anjexe on 2011-04-05
> **sanderj said:**
> Have you tried putting it in /etc/rc.local ?

yes but it dosent work :(

---

### Post by anjexe on 2011-04-05
after login to ubuntu

i open a terminal windows and inter this comand ehith the said order 

sudo insmod acpi_call.ko

and then 

./test_off.sh

---

### Post by anjexe on 2011-04-09
w8ing for help....

---

### Post by hakermania on 2011-04-09
It's pretty easy
Make an executable script in your ~/Documents folder containing (exactly as you see it, just place your login passwd where I say you to)
```

#!/bin/bash
echo "YOUR LOGIN PASSWD HERE" | sudo -S insmod acpi_call.ko
echo "YOUR LOGIN PASSWD HERE" | sudo -S ./test_off.sh
```NOTE: Full path to test_off.sh instead of ./test_off.sh (i.e. /home/$USERNAME/test_off.sh) is preferable
Now, go to System->Preferences->StartUp Applications, click 'Add' and browse to this executable file you created previously. (in the Name and comment field type whatever you wish)
That's all.

---

### Post by anjexe on 2011-04-09
> **hakermania said:**
> It's pretty easy
Make an executable script in your ~/Documents folder containing (exactly as you see it, just place your login passwd where I say you to)
```

#!/bin/bash
echo "YOUR LOGIN PASSWD HERE" | sudo -S insmod acpi_call.ko
echo "YOUR LOGIN PASSWD HERE" | sudo -S ./test_off.sh
```NOTE: Full path to test_off.sh instead of ./test_off.sh (i.e. /home/$USERNAME/test_off.sh) is preferable
Now, go to System->Preferences->StartUp Applications, click 'Add' and browse to this executable file you created previously. (in the Name and comment field type whatever you wish)
That's all.


it is great
tanx a lot :p
i am so happy:lolflag:

also tanx fore nice app wallch ;) so cute

---

### Post by Daniel0108 on 2011-04-09
> **anjexe said:**
> it is great
tanx a lot :p
i am so happy:lolflag:

[Please mark your thread as solved now,]("http://bit.ly/uf-solved")
Daniel

---

