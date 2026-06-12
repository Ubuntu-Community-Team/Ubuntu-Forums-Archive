---
title: "How to run a command as root?"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by egruber on 2010-12-07
I need to run the following as root using terminal.

echo enable,0x00ffffff > /proc/acpi/ibm/hotkey


But it says Permission Denied.  How do I run it as root?

Thanks!!

---

### Post by sisco311 on 2010-12-07
```
echo enable,0x00ffffff | sudo tee -a /proc/acpi/ibm/hotkey
```

See: [uhelp]community/RootSudo[/uhelp]

---

### Post by surfer on 2010-12-07
you can. but be sure you know what you are doing!

```
$ echo enable,0x00ffffff | sudo tee -a /proc/acpi/ibm/hotkey
```
and enter your user password.

```
sudo -s
```
will give you a root shell.

---

### Post by endotherm on 2010-12-07
in that case, run 
```

sudo -i

```
before running your command. then type exit wen you are done to stop running as root
```

user@Lucid:~$ whoami
user
user@Lucid:~$ sudo -i
[sudo] password for user: 
root@Lucid:~# whoami
root
root@Lucid:~# pwd
/root
root@Lucid:~# echo ~
/root
root@Lucid:~# exit
logout
user@Lucid:~$ 

```

or if you need to maintain your users environment settings, use sudo -s
```

user@Lucid:~$ sudo -s
root@Lucid:~# pwd
/home/user
root@Lucid:~# echo ~
/home/user
root@Lucid:~# exit
exit
user@Lucid:~$ 

```

---

### Post by egruber on 2010-12-07
That worked!  Many thanks!!

---

