---
title: "Cannot open a file in /home directory"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by David-IT on 2009-09-12
Hello guys i can not seem to get .fuppes directory open i have to ctrl+h scince it is a hidden folder but every time i try to open it it tells me > The folder contents could not be displayed
you do not have the permissions necesarry to view the contents of ".fuppes" i have tried to open it through terminal using sudo then it still tell's me i cannot view it i have also tried > david@david-desktop:~$ gksu nautilus
david@david-desktop:~$ gksudo nautilus

 
> then i even tried david@david-desktop:~$ gedit $HOME/.fuppes/Open\ as\ Administratorstill cannot open the file/folder  i am running ubuntu 9.04 please help :D

---

### Post by Rocket2DMn on 2009-09-12
Can you please post the output of
```
ls -al .fuppes
```
We'll see what the permissions currently look like, then we can change them.

---

### Post by David-IT on 2009-09-12
oh wow ty for the quick response and the output it
> david@david-desktop:~$ ls -al .fuppes
ls: cannot open directory .fuppes: Permission denied

then i tried sudo also and the output was 
> david@david-desktop:~$ sudo david@david-desktop:~$ ls -al .fuppes
[sudo] password for david: 
david is not in the sudoers file.  This incident will be reported.


---

### Post by SuperSonic4 on 2009-09-12
What if you preface that command with sudo?

```
sudo ls -Al .fuppes
```

---

### Post by Rocket2DMn on 2009-09-12
> **SuperSonic4 said:**
> What if you preface that command with sudo?

```
sudo ls -Al .fuppes
```

Please use with the lowercase "a" so we can see the . and .. (then we can see the permissions on the parent folder as well).
```
sudo ls -al .fuppes
```
Thanks :)

---

### Post by David-IT on 2009-09-12
hmm i tried lowercase "a" and uppercase "A" still the same output

---

### Post by Rocket2DMn on 2009-09-12
> **David-IT said:**
> hmm i tried lowercase "a" and uppercase "A" still the same output

Can you please copy and paste that output here so we can see it?  Thanks.

---

### Post by arrange on 2009-09-12
You are probably not in the *admin* group. Post the output of ```
id
```

---

### Post by David-IT on 2009-09-12
> **Rocket2DMn said:**
> Can you please copy and paste that output here so we can see it?  Thanks.
i did bro scroll up the output i posted is the same for lowercase a and uppercase  
but just incase i did it wrong here it is again > david@david-desktop:~$ sudo ls -al .fuppes
[sudo] password for david: 
david is not in the sudoers file.  This incident will be reported.
david@david-desktop:~$ sudo ls -Al .fuppes
[sudo] password for david: 
david is not in the sudoers file.  This incident will be reported.
david@david-desktop:~$ 

and the id is here
> david@david-desktop:~$ id
uid=1000(david) gid=1000(david) groups=1000(david)

---

### Post by wojox on 2009-09-12
```
sudo chmod 700 .fuppes
```

---

### Post by David-IT on 2009-09-12
hey guys thank you for taking your time to help me i greatlly appreciate it and wojox when i typed that in i get > david@david-desktop:~$ sudo chmod 700 .fuppes
[sudo] password for david: 
david is not in the sudoers file.  This incident will be reported.



---

### Post by arrange on 2009-09-12
Normally you have to be in the *admin* group to be able to *sudo*. Reboot, go into the recovery mode, then to the root console, and copy there these commands
```
usermod -a -G admin david
reboot
```

---

### Post by David-IT on 2009-09-12
oh ok ty man i will be right back booting into recovery and trying your command :D hope it works!!

---

### Post by Rocket2DMn on 2009-09-12
> **arrange said:**
> Normally you have to be in the *admin* group to be able to *sudo*. Reboot, go into the recovery mode, then to the root console, and copy there these commands
```
usermod -a -G admin david
reboot
```

Beat me to it.  Do what he said in order to setup sudo access for your user "david" ^
:)

Once back into the system with your normal username, run
```
sudo ls -al .fuppes
```
and post the output back here.

---

### Post by SuperSonic4 on 2009-09-12
> **Rocket2DMn said:**
> Beat me to it.  Do what he said in order to setup sudo access for your user "david" ^
:)

Once back into the system with your normal username, run
```
sudo ls -al .fuppes
```
and post the output back here.

Could he not do the same from the recovery console?

---

### Post by David-IT on 2009-09-12
ok sweet i went into recovery went into the consel logged in as root etc.. then i just got back and typed that in i got
> david@david-desktop:~$ sudo ls -al .fuppes
[sudo] password for david: 
total 32
drwxr-x---  2 root  root   4096 2009-09-12 10:29 .
drwxr-xr-x 38 david david  4096 2009-09-12 11:31 ..
-rw-r--r--  1 root  root   7727 2009-09-12 10:29 fuppes.cfg
-rw-r--r--  1 root  root  14336 2009-09-12 10:29 fuppes.db
 i am trying to get to fuppes.cfg at this momment any idea how i can actually get into that file?
i tried > david@david-desktop:~$ /etc/fuppes/fuppes.cfg
bash: /etc/fuppes/fuppes.cfg: Permission denied
 but i am pretty sure that wont get me the file i need anyways lol

---

### Post by arrange on 2009-09-12
For example
```
sudo nano ~/.fuppes/fuppes.cfg
```
or
```
gksudo gedit ~/.fuppes/fuppes.cfg
```

---

### Post by David-IT on 2009-09-12
wow ty arrange i just tried > david@david-desktop:~$ gedit /etc/apt/fuppes.cfg
 because of your fabulous suggestions and i got it!!!!! wooooooot tyyyyyy soo much ubuntu forums community this could not have been acheived without all of your help ty soo much!!!!!

---

### Post by pedro3005 on 2009-09-12
Press ALT F2, type in "gksu nautilus". Press CTRL H then right click .fuppes. On the permissions tab, set whatever you want, should work.

---

### Post by Rocket2DMn on 2009-09-12
> **SuperSonic4 said:**
> Could he not do the same from the recovery console?
Yes, but he wouldn't be able to copy/paste the output back here without an X session, unless he was really good at using the terminal and a terminal-based browser.

> **David-IT said:**
> ok sweet i went into recovery went into the consel logged in as root etc.. then i just got back and typed that in i got
 i am trying to get to fuppes.cfg at this momment any idea how i can actually get into that file?
i tried  but i am pretty sure that wont get me the file i need anyways lol

In order for your user to access the files, you need to chown them to your username/group:
```
sudo chown -R david:david .fuppes
```

Nothing in your home directory should be owned by other users or root.

---

### Post by David-IT on 2009-09-12
> **Rocket2DMn said:**
> Yes, but he wouldn't be able to copy/paste the output back here without an X session, unless he was really good at using the terminal and a terminal-based browser.



In order for your user to access the files, you need to chown them to your username/group:
```
sudo chown -R david:david .fuppes
```

Nothing in your home directory should be owned by other users or root.

holy smokes!! ty sooo much yes with the alt+2 command etc it let me access the file but not neceserally edit it but tyyyyyy so much admin sir! your chown command worked like a charm i can know access it write in it and save it wooot tyyyyyyyyyyyyy!!!!!!!!!!! media server here i come!

---

