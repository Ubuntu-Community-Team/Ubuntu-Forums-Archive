---
title: "Sudden root password changed"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by cyaquino on 2009-09-02
I am completing a fresh Ubuntu 9.04 installation and after the network manual IP4 config and after realizing that the install only took 2GB of disk instead of all available :confused:, suddenly I realizad that the root password is not the same it was :confused:.
As it is a new machine still in configuration, I put the password equal to my username. But now it refuses, telling: "su: Authentication failure".
What could happen? How to fix my root password?
Thanks!

---

### Post by DGortze380 on 2009-09-02
> **cyaquino said:**
> I am completing a fresh Ubuntu 9.04 installation and after the network manual IP4 config and after realizing that the install only took 2GB of disk instead of all available :confused:, suddenly I realizad that the root password is not the same it was :confused:.
As it is a new machine still in configuration, I put the password equal to my username. But now it refuses, telling: "su: Authentication failure".
What could happen? How to fix my root password?
Thanks!

Ubuntu does not use a root password by default. Preface the command you want to run as root with sudo and enter your user password.

It is possible to set the root password, but the forum forbids discussing any reason you might want to do that... haha.

---

### Post by Gaweph on 2009-09-02
By default ubuntu does not have a root password.

The first user has sudo privilages: so you can do:

**sudo COMMAND**

If its a stock install then do:

**sudo psswd**

in order to set teh root password.

Hope that helps

---

### Post by cyaquino on 2009-09-02
Ok, I was confused. So by **sudo passwd** I can finally to go to the # prompt with the command su.
Thanks!
Now I coud install **gparted** and it appear on menu. I will try to increase partition size.

---

### Post by xir_ on 2009-09-02
> **cyaquino said:**
> Ok, I was confused. So by **sudo passwd** I can finally to go to the # prompt with the command su.
Thanks!
And how can I acces the gparted? (does not appear on menus)



```

sudo gparted

```but make sure its installed
```

sudo apt-get install gparted

```

---

### Post by Gaweph on 2009-09-02
System -> Administration -> Partition Manager

If its not there youl have to do 

**sudo apt-get install gparted**

Also i would advise against doing 

**su**

and just use

**sudo COMMAND instead**

doing the sudo method saved your sudop privilages for that session, so further sudo commands dont ask for password anyways, i would **NOT** log in as root, as you mgith forget and accidentally throw in a **rm -rf /** or something silly **(DONT RUN THAT COMMAND)**

---

### Post by DGortze380 on 2009-09-02
> **cyaquino said:**
> Ok, I was confused. So by **sudo passwd** I can finally to go to the # prompt with the command su.
Thanks!
Now I coud install **gparted** and it appear on menu. I will try to increase partition size.

gparted is on the livecd but not installed by default.
install with: sudo apt-get install gparted
Be warned, do not use on a mounted file system.

---

### Post by cyaquino on 2009-09-02
Ok, now the subject changed. It´s best to close this thread. Nevertheless I don´t understand why it suddenly rejected my password in the sudo commands...
Now I set the root password also.
Thanks to all!

---

### Post by Gaweph on 2009-09-02
Check whether your username is defenatelly on hte list of sudoers.

You need to be on the sudoers list in order to run **sudo**

also when you do;

**sudo COMMAND**

you use your own password and not the root password.

---

### Post by bodhi.zazen on 2009-09-02
Ubuntu uses sudo and not su.

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

For a root shell please use ```
sudo -i
```To lock your root account again you can use:

```
sudo usermod -p ! root
```Please also see :

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 
[]("http://ubuntuforums.org/showpost.php?p=5769207&postcount=77")

---

