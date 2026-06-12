---
title: "cannot install programs using apt-get"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-04
Getting error while using apt-get

```
karthick@Ubuntu-desktop:~$ sudo aptitude install aquadreams-theme
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

What is the problem here..?How do i solve..?

---

### Post by Bapun007 on 2010-11-04
This means another program is using root access . Ex - synaptic , software center . Close these programs and try .(works for me)

---

### Post by kroq-gar78 on 2010-11-04
if no other programs are running and you think you closed all of them, just reboot the computer. It's the easiest way to kill everything that's running.

---

### Post by karthick87 on 2010-11-05
> **Bapun007 said:**
> This means another program is using root access . Ex - synaptic , software center . Close these programs and try .(works for me)


i think something is runing in background.How can i close that..?

---

### Post by Gheter on 2010-11-05
You can also try using aptitude instead of apt-get. This worked for me(most of the time).

---

### Post by karthick87 on 2010-11-05
Oke but what is running in background..?How do i find it..?

---

### Post by garvinrick4 on 2010-11-05
system monitor to process's tab.

---

### Post by kroq-gar78 on 2010-11-06
as I said, reboot the computer and it will kill all processes, including the package program that seems to be running

---

### Post by karthick87 on 2010-11-06
Rebooted my system,but still the problem is same..I think thunderbird profile messed up.But i dont know to correct it..

---

### Post by zuerston on 2010-11-06
> **getyourkarthick said:**
> Rebooted my system,but still the problem is same..I think Thunderbird profile messed up.But i dont know to correct it..

If you have rebooted and not started Thunderbird again ,then it is not Thunderbird doing it. as stated above ,,see system monitor ==> processes for your answer.

---

### Post by d8xter on 2010-11-06
> **getyourkarthick said:**
> Getting error while using apt-get

```
karthick@Ubuntu-desktop:~$ sudo aptitude install aquadreams-theme
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```What is the problem here..?How do i solve..?

sudo dpkg --configure -a
sudo rm /var/lib/dpkg/lock

---

### Post by wojox on 2010-11-06
Check the process list (ps aux) for any mention of apt, synaptic, ... - and kill them.

---

