---
title: "Root User Name and password"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by rajendran_babu on 2009-01-02
Hi,
  i recently installed ubuntu 8.04 in my laptop..the installation process, created a username with administrator rights..but i want to login as root user, as i want to drag and drop files to fonts folder.. 
The installation process didnt ask for any root password while installing ..

is there a default password for the root ?

---

### Post by Joeb454 on 2009-01-02
Hit Alt+F2 and enter ```
gksu nautilus
``` to run nautilus with root permissions.

As always, be careful what you move/delete when running things as root.


And by default Ubuntu uses sudo instead of root, which is a little more secure :)

---

### Post by snowpine on 2009-01-02
Hi Rajendran,
Ubuntu differs from many other Linux distributions in that the root account is locked. You should preface a command with 'sudo' (for command line) or 'gksu' (for GUI applications). When you are prompted for a password, enter your user password.

For example, 'gksu nautilus' will open a file browser as root so that you can drag the files to your fonts folder.

---

### Post by spcwingo on 2009-01-02
In Ubuntu the root account is disabled by default.  If you need to do anything as root you have to use sudo.  To do what you are talking about just do:

```
gksu nautilus
```

and drag/drop away!;)  If this is unacceptable for you just change the root password via the terminal.  I won't go in to detail on how to do it here...just Google it.  That's how I found out how to do it.

---

### Post by freak42 on 2009-01-02
Hello,

logging in and working as root is not recommended as it breaks the whole security model to a certain extent.

To temporarily get a nautilus (file explorer) instance with root rights into which you can drag&drop files with root rights type
```
sudo nautilus
``` into a console or alternatively
type alt-f2 and write gksudo nautilus into the 'run application' line

hth

---

### Post by doug1212 on 2009-01-02
Hi,
Here is some more info:

[HTML]https://help.ubuntu.com/community/RootSudo[/HTML]

Doug.

---

### Post by Joeb454 on 2009-01-02
> **freak42 said:**
> type
```
sudo nautilus
``` into a console or alternatively
type alt-f2 and write gksudo nautilus into the 'run application' line

Even if you use a terminal to enter the command, you should still run ```
gksu nautilus
``` :)

---

### Post by igknighted on 2009-01-02
If you install ubuntutweak (get it on getdeb) it can install an option in nautilus to right click -> browse as root.  Or you can launch nautilus from the terminal as stated above.  However, while what you describe is possible, it is a violation of forum policy for anyone to explain to you how to do it here.  If you still want to do this, search on google.

---

