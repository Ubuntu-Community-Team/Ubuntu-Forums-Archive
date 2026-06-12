---
title: "Permissions problem: su cannot write"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Franz01 on 2011-01-02
I logged as a normal user (not root) and then I tried to write to a directory
 
I try with 

```
user@Workstation:/mnt$ any command > test.log
```

but I cannot write

```
bash: fat32.log1: Permission denied
```

Then I try with

```
user@Workstation:/mnt$ sudo + the same command as above > test.log
```

And I get the same error

```
bash: fat32.log1: Permission denied
```

Anybody can explain to me why I cannot write? If I go to /home/user and then I run the same command it works. And then I am able to move the file to /mnt without sudo... so why I cannot write directly to /mnt?

Thank you for your comments.

---

### Post by matt_symes on 2011-01-02
Hi

/mnt is owned by root so you do not have permission to write to it. What commands are you trying to run? There are a couple of ways to do these things depending on the command you are trying to run. Here's one for ls.

```
ls | sudo tee test.log 
```

whereas 

```
matthew@matthew-laptop:/mnt$ sudo ls > test.log
bash: test.log: Permission denied
```

(as you can see) does not work. This is because only *ls* is given sudo privileges, not the redirection to the file (and that is what you want to have the sudo privileges).

You can, of course, just write it to your home directory.

```
matthew@matthew-laptop:/mnt$ ls > ~/test.log
matthew@matthew-laptop:/mnt$
```

Others can be of the form sudo bash .....

Kind regards

---

### Post by cogier on 2011-01-02
I had the same issue when I tried this but was able to create a file in Nautilus when run from Terminal with ```
gksu nautilus
```.

---

