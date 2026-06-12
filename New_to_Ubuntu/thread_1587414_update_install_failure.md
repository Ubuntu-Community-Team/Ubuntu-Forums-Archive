---
title: "update install failure"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by boyealexzoe on 2010-10-03
when i try to install update in terminal using "apt-get update" command , i get the message:
 "E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory".
can anyone please help me on what to do?
Also, what does root mean?
thanx

---

### Post by drs305 on 2010-10-03
Normally this message is created when another app is also accessing APT. See if Synaptic, Software Sources, and perhaps Software Center are open. If they are, close them and it will refresh the 'lock' file which is creating the error messages. 

If the message still occurs, the next safe thing to do is to try rebooting to ensure all the apps that APT monitors are closed. If you still get the message, let us know.

---

### Post by boyealexzoe on 2010-10-03
am still getting the same error message...

---

### Post by Hippytaff on 2010-10-03
```

sudo apt-get update

```
try this

---

### Post by wojox on 2010-10-03
Are you using sudo

```
sudo apt-get update
```

---

### Post by drs305 on 2010-10-03
Ok, first ensure the normal APT programs are closed:

```
sudo killall apt-get
sudo killall aptitude
sudo killall synaptic
sudo killall update-manager
sudo apt-get update

```

If it still doesn't work, rename the lock file. It will be recreated. This bypasses a corrupted *lock* file. It's not the desired method of clearing this problem, but it should solve it:
```
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.bad
sudo apt-get update

```


Note: You can use "sudo -i" before the first command and not have to type "sudo" for any of the other commands. If you do so, type "exit" at the end to return to the normal user prompt.

---

### Post by boyealexzoe on 2010-10-04
thanks sooo much guys. using the code ```
sudo apt-get update 
```, i was able to install the updates but i dont understand why it finished withn a short time but using update manager takes such a long time

---

### Post by emoguitarist06 on 2010-10-04
> **boyealexzoe said:**
> 
Also, what does root mean?
thanx

We forgot to address the last questions. Someone else may be better at explaining this but Root is the super user or administrator of Linux Operating Systems. Automatically when you install Linux and you create your username Linux will always automatically create root. This is one reason why Linux is so safe because you're not the administrator and to make any big changes you must run something as root and in the terminal "sudo" makes you root for a short period of time :)

---

### Post by drs305 on 2010-10-04
> **boyealexzoe said:**
> thanks sooo much guys. using the code ```
sudo apt-get update 
```, i was able to install the updates but i dont understand why it finished withn a short time but using update manager takes such a long time

Just so we're clear: *apt-get update* merely refreshes the respository listings from what you have in your sources.list file and sources.list.d folder. It isn't installing any software. I ended my list of commands at that point because I believe that the error you were getting would have been triggered by that command.

To actually install updates you should run the following, which will take longer if you have a lot of packages that need updating to the most recent version:
```
sudo apt-get *upgrade*
```

---

### Post by boyealexzoe on 2010-10-05
ok. i think i understand this better now. so, is it really necessary for me to install all those updates before i can get the best out of ubuntu?
@ emoguitarist06...thanx 4 the explanation of root but then who is the administrator in a particular linux system?

---

### Post by Hippytaff on 2010-10-05
I 
```

sudo apt-get update && sudo apt-get upgrade

```
 
to keep everything up to date

---

### Post by drs305 on 2010-10-05
Here is the community doc explaining 'root':
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

