---
title: "fdisk"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by maclover on 2010-09-30
hey
i installed fdisk and i dont know where it was put at and i would like to know where to go and use it since i dont know where it was placed at.:confused::confused::confused::?:?:?

---

### Post by crf on 2010-09-30
It's run from a terminal.
To open a terminal go to Applications menu --> accessories --> terminal.
the command is fdisk.
Try fdisk -h first, to read the help. Or run *man fdisk* in a terminal.

---

### Post by cj.surrusco on 2010-09-30
Not exactly sure what you are asking...

Fdisk is installed by default, and can be run by typing 'fdisk' in the command line. Type 'man fdisk' to find out more info on how to use the command.

---

### Post by srs5694 on 2010-09-30
If you installed the package called gnu-fdisk, I recommend you uninstall it. That package contains GNU fdisk, which is based on libparted, the same library that's at the core of GNU Parted, GParted, and several other tools. Although this works fine for many purposes, libparted is riddled with bugs and limitations when it comes to dealing with problem configurations. It's best to have Linux fdisk for such situations, but GNU fdisk overrides Linux fdisk, so installing GNU fdisk has the effect of making it harder to deal with certain disk partitioning problems.

As cj.surrusco says, Linux fdisk is installed by default. It's installed in a package called util-linux, at least on my Ubuntu 9.10 system. Crf's instructions will get you started with using it; or you can try an online tutorial [like this one.](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html) (It's just one of many that turned up when I did a Web search; there are plenty more.)

---

### Post by maclover on 2010-10-01
ok thanks that helps me bunch and i dont have GNU fdisk i have linux fdisk for what i am doing it says i need to do the following:

# fdisk /dev/sdb   Command (m for help): p 



but i get a error saying:
fdisk command: p
Error: Could not stat device command: - No such file or directory.        
   r   Retry                                                              
   c   Cancel



so i edit some of it using the "command(m for help): p" and i get a similar error saying:
bash: syntax error near unexpected token `('
as you can tell i am new to this and need help

---

### Post by psusi on 2010-10-01
The command is just fdisk /dev/sdb.  It prints the command prompt asking you to give it further instructions.

---

### Post by maclover on 2010-10-01
it says Error: Error opening /dev/sdb: Permission denied                          
   r   Retry                                                              
   c   Cancel

---

### Post by cj.surrusco on 2010-10-01
you need to use sudo with that command. 

```
sudo fdisk /dev/sdb
```

---

### Post by maclover on 2010-10-03
ok thnx its now working

---

