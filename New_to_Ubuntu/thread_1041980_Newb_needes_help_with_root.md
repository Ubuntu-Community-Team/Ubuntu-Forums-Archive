---
title: "Newb needes help with root"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by LibertiORDeth on 2009-01-17
When  I go into terminal and try to log in as root it doesn't let me type on the "password" line.  What's wrong?

---

### Post by treesurf on 2009-01-17
That's normal.  When you type your password in the terminal the characters don't appear, but they are being input anyways.  Just type your password and press enter, and it should work fine.

---

### Post by LibertiORDeth on 2009-01-17
Alright, even so when I put in the password (I assume it's the one I set as log in to my computer) it says something along the lines of unable to authenticate, incorrect password.

---

### Post by talsemgeest on 2009-01-17
For root, you must have root privilages (are you on the account that was used to set up the computer?). If you are, you are typing the wrong password, so make sure you have all the capitals correct.

---

### Post by nhasian on 2009-01-17
the user root is disabled by default.  if you want to run a command with super user privileges just precede it with sudo. for example:

```
sudo lshw
```

If you would like to enable the root account you just need to set a password for it by using the command:

```
sudo passwd root
```

---

### Post by talsemgeest on 2009-01-17
> **nhasian said:**
> the user root is disabled by default.  if you want to run a command with super user privileges just precede it with sudo. for example:

```
sudo lshw
```

If you would like to enable the root account you just need to set a password for it by using the command:

```
sudo passwd root
```
Ah, sorry, I wasn't paying close enough attention. Yes, you need to precede the commands with sudo.

Also, enabling the root account is not supported by ubuntu as it is a potential security risk.

---

### Post by redseventyseven on 2009-01-17
Root is disabled by default in Ubuntu in order to make it less likely that the user will leave themselves running the whole system as root, then execute a damaging command willy-nilly (or have a malicious hacker do so) and cause some serious damage to your system. It's part of its security model.

The "sudo" command (which stands for "Super User - DO") is there to give a user temporary root privileges to run one specific command and then quickly close the door on the root account to prevent anything else from doing any damage.

I understand it causes some initial frustration not to have a root account but in my opinion it's better to learn how to live without it as you soon discover that you don't need it. If you're still not convinced then the beauty of Linux is that you don't just have to use Ubuntu - there are other distros out there (which are by no means inferior) which do have root accounts enabled, such as PCLinuxOS ([www.pclinuxos.com](www.pclinuxos.com)).

---

### Post by ronbrooks on 2009-01-17
If someone does enable root how would you disable it again after you do what you have to do.

---

### Post by vanadium on 2009-01-17
You should never enable root. Use "sudo <command>" to perform actions that require root permissions. Only advanced and very experiences users might (sometimes) really need a root account.

---

### Post by thezood on 2009-01-17
> **ronbrooks said:**
> If someone does enable root how would you disable it again after you do what you have to do.

Here's a tip: if you want to do file operations as root and don't want to use the terminal, you can run:
```

sudo nautilus

```
...and you'll get a file manager with superuser rights. 

However be warned that you'll then have total access to all files and folders on all your drives. So if you accidentally delete a system folder or something, it will be gone immediately without warning. Also, all files you create with that file manager will be owned by root and thus unusable to everyone else until you change ownership, which can be a pain. Also, don't forget to close that nautilus window after you're done so that you don't use that for other things by mistake.

**In short: always be careful with the root account.** :)

---

