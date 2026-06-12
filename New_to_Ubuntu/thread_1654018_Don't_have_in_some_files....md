---
title: "Don't have in some files..."
date: 2010-12-27
forum: New to Ubuntu
---

### Post by stamatiou on 2010-12-27
[SIZE=5]**Sorry the subject is don't have !permision!**** to some files**[/SIZE]
 Hey guys, I went to the /var/www directory but I can't touch anything what should I do?

---

### Post by wojox on 2010-12-27
You mean touch command run 

```
sudo touch newfile
```

---

### Post by stamatiou on 2010-12-27
> **wojox said:**
> You mean touch command run 

```
sudo touch newfile
```
I mean that I went to that directory but I couldn't create a text document.

---

### Post by wojox on 2010-12-27
Is this in the terminal or File Manager?

---

### Post by presence1960 on 2010-12-27
To create a new file in terminal do what wojox said. To create a new file from File manager you must use Nautilus (or whatever file manager you are using) as root. open a terminal and run ```
gksu nautilus
```

---

### Post by stamatiou on 2010-12-28
> **presence1960 said:**
> To create a new file in terminal do what wojox said. To create a new file from File manager you must use Nautilus (or whatever file manager you are using) as root. open a terminal and run ```
gksu nautilus
```
Thanks man but I think that there is also another problem, when I type in the terminal su and it asks me for the password, I type the password but the output says:
```
su: Authentication failure

```
I have checked it and the password is fully correct, how can I fix it?

---

### Post by presence1960 on 2010-12-28
> **stamatiou said:**
> Thanks man but I think that there is also another problem, when I type in the terminal su and it asks me for the password, I type the password but the output says:
```
su: Authentication failure

```
I have checked it and the password is fully correct, how can I fix it?

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by stamatiou on 2010-12-28
> **presence1960 said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Yes but ina all of the programs who ask password it works....

---

### Post by mcduck on 2010-12-28
> **stamatiou said:**
> Thanks man but I think that there is also another problem, when I type in the terminal su and it asks me for the password, I type the password but the output says:
```
su: Authentication failure

```
I have checked it and the password is fully correct, how can I fix it?

Use "sudo", not "su".

Su asks for *target user's* password, and you don't actually have a root password (at least you *shouldn't* have one). Sudo on the other hand asks for *your* password and then checks if you have the permissions to run the command as target user.

You should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by matt_symes on 2010-12-28
Hi

Press ALT + F2 to display the run dialog and enter...

```
gksudo nautilus
```

and not

```
gksu nautilus
```

Kind regards

---

### Post by mcduck on 2010-12-28
> **matt_symes said:**
> Hi

Press ALT + F2 to display the run dialog and enter...

```
gksudo nautilus
```

and not

```
gksu nautilus
```

Kind regards

Actually gksu and gksudo are linked to one and the same program, and use "sudo" authentication. So whichever you use makes no difference.

It's only the command-line equivalents, "sudo" and "su", that work differently.

---

### Post by matt_symes on 2010-12-28
Hi

> Actually gksu and gksudo are linked to one and the same program, and use "sudo" authentication. So whichever you use makes no difference.

It's only the command-line equivalents, "sudo" and "su", that work differently.

Cheers. I learn something every day.

```

matthew@matthew-laptop:/usr/bin$ ls -l gk*
-rwxr-xr-x 1 root root 26752 2010-03-05 04:23 gksu
lrwxrwxrwx 1 root root     4 2010-10-14 21:32 gksudo -> gksu
```

Kind regards

---

