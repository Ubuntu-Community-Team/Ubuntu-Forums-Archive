---
title: "trying to copy files into filesystem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by stalkier on 2009-03-22
Hello. I am trying to copy some files into user/share/gnomenu/themes/buttons. I have the files extracted onto my desktop but I also have the tarball. When I try to copy the files into the directory it says that I do not have permission. I understand I need to be logged into as a super-user. How can this be done? GUI/terminal is fine but I need commands. Thanks for the help.

---

### Post by Volt9000 on 2009-03-22
Press Alt+F2 and type in:

```

gksu nautilus

```

You will then be asked for your account password. Type it in and now you have an instance of Nautilus (the file browser) running with admin rights.

---

### Post by halitech on 2009-03-22
in the terminal
```
sudo cp /location/of/files /location/you/want/files
```
or you can press ALT-F2 and run
```
gksudo nautilus
```
this will give you a "root" nautilus, but be very careful you don't do anything you don't plan on doing as you can really mess up your system with this.

---

### Post by sisco311 on 2009-03-22
> **stalkier said:**
> Hello. I am trying to copy some files into user/share/gnomenu/themes/buttons. I have the files extracted onto my desktop but I also have the tarball. When I try to copy the files into the directory it says that I do not have permission. I understand I need to be logged into as a super-user. How can this be done? GUI/terminal is fine but I need commands. Thanks for the help.

You need root privileges.

[uhelp]community/RootSudo[/uhelp]


to copy all the files from ~/Desktop/dir to /usr/share/gnomenu/themes/buttons:
```
sudo cp ~/Desktop/dir/* /usr/share/gnomenu/themes/buttons
``` 

to start the file manager as root:
```
gksu nautilus
```be very careful, as root you can damage your system.

EDIT: d'oh, i'm slow. :)

---

### Post by stalkier on 2009-03-22
Thanks so much guys! This worked perfect. I am going to write these down for future reference. Thanks agian guys for the super fast response.

---

