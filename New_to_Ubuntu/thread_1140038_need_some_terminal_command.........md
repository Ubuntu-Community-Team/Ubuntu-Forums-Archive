---
title: "need some terminal command........"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by saikat_tapu on 2009-04-27
[SIZE=3][COLOR=Navy][FONT=Comic Sans MS]hey friends i need some terminal commands.......

1. how to create or remove virtual drives?
2. how to mount/ unmount drives?
3. how can i connect a nokia 6680 as a modem through bluetooth?
4. how to install files which have extension like tar.gz????
5. and describe a command so that i can understand meaning of most of the commands in ubuntu terminal.

thanks to all.[/FONT][/COLOR][/SIZE] ....

---

### Post by Spiritous on 2009-04-27
Type

```
help
```

Into Terminal for a full list of commands.

---

### Post by saikat_tapu on 2009-04-27
> **Spiritous said:**
> Type

```
help
```

Into Terminal for a full list of commands.
i am finding it quite difficult to understand. i m a newbie to ubuntu/linux. hope u understand that.

---

### Post by cariboo on 2009-04-27
I would suggest you download and read [The Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/"), it is free, and gives you the basics you need for running Ubuntu. I would suggest your friend read it also.

---

### Post by oldos2er on 2009-04-27
> **saikat_tapu said:**
> [SIZE=3][COLOR=Navy][FONT=Comic Sans MS]hey friends i need some terminal commands.......

1. how to create or remove virtual drives?
2. how to mount/ unmount drives?
3. how can i connect a nokia 6680 as a modem through bluetooth?
4. how to install files which have extension like tar.gz????
5. and describe a command so that i can understand meaning of most of the commands in ubuntu terminal.
  [/FONT][/COLOR][/SIZE]

 For help with commands, use "man" or "info"
```
man <command>
info <command>
``` where <command> is the command you need help with.

 tar.gz file are archives (similar to .zip files); how you deal with them depends on what they contain.

 ```
mount <device>
umount <device>
```will mount and unmount drives. Run
```
man mount
```for more info.

---

### Post by TheLions on 2009-04-27
> **saikat_tapu said:**
> [SIZE=3][COLOR=Navy][FONT=Comic Sans MS]hey friends i need some terminal commands.......

1. how to create or remove virtual drives?
2. how to mount/ unmount drives?
3. how can i connect a nokia 6680 as a modem through bluetooth?
4. how to install files which have extension like tar.gz????
5. and describe a command so that i can understand meaning of most of the commands in ubuntu terminal.

thanks to all.[/FONT][/COLOR][/SIZE] ....

for 1. install cdemu
go to [https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

copy apt sources.list entries into your repository (System->Administration->Software repository, 2nd tab)

then in Terminal (Programs->Accesories->Terminal) type 'sudo apt-get install gcdemu' then reboot, after reboot click on upper gnome panel and press 'ADD to pannel' and click on 'gcdemu applet'. 
To add image ->left click on that applet:)

---

### Post by Tibuda on 2009-04-27
> **saikat_tapu said:**
> 4. how to install files which have extension like tar.gz????
First, I have to say the best way to install software is through Ubuntu package manager, not from the software website. See [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Those tar.gz files are source code archives. Many source packages are installed with these three commands in the extracted directory:
```
./configure
make
sudo make install
```
But not all applications are installed with them. Look for the INSTALL or README file inside the package for instructions.

---

