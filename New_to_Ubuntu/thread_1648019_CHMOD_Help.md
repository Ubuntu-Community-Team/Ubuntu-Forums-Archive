---
title: "CHMOD Help"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Halifaxlad on 2010-12-18
Before I put my head through the wall can someone please help me?

I use LastPass as my Password Manager, now what I want to do is install a small program that adds an extra layer of security however I cant seem to follow what look like easy instructions

> Install instructions:

1. Right-click the download button and choose 'Save Link As'
2. Run 'chmod +x sesame' or 'chmod +x sesame_x64' so it can be run
3. Run 'sudo apt-get install ca-certificates' to update your ca-certificates package

What is chmod how do I do steps 2 & 3, I have done step 1 and thats sat in My Downloads would I need to do anything with this file?

---

### Post by Wtower on 2010-12-18
I assume that sesame is a file downloaded in some directory. I have no knowledge of this particular piece of software, so I also assume that you trust it. So in order for you to do step 2 you need to open terminal (alt+f2), cd to the directory that you downloaded it, as for example: ```
cd ~/Downloads
``` and then ```
run chmod +x sesame
``` (or alternatively you can run directly following the previous example ```
chmod +x ~/Downloads/sesame
``` . This command gives permission to execute that file. To execute it run ```
./sesame
```. Finally, the last command again should be issued within terminal.

Regards

---

### Post by sanderd17 on 2010-12-18
CHMOD changes the "modifiers" of a file. The modifiers are some bits used to know who has which rights on the file. If you do the command 

```

ls -l

```

you will see things like

```

drwxr-xr-x user usergroup Documents
-rw-r--r-- user usergroup myTextDucument.txt
...

```

The "rwx" sequences are the modifiers. The first sequence stands for the owner (user in this case), he has the rights "rwx" for the directory which is "Read, Write and eXecute", for the file he has "Read and Write" rights. The second sequence are the rights for the group (usergroup in this case) en the last for everyone else.

To change the modifiers, you need to use the "chmod" command:

```

chmod +x sesame

```

will place the "x" bit in all sequences for the file sesame.

If you want more info about chmod: see the linux command wibsite: [http://linuxcommand.org/](http://linuxcommand.org/)

EDIT: If you want to change the modifiers of files which you don't own, you need to go in superuser mode by placing a "sudo" in front of the command.

---

### Post by sanderd17 on 2010-12-18
@Wtower: ALT+F2 isn't the standard shortcut for the terminal, you need to open the terminal via the menu, or press ALT+F2 and execute the command "gnome-terminal".

---

### Post by Wtower on 2010-12-18
> **sanderd17 said:**
> @Wtower: ALT+F2 isn't the standard shortcut for the terminal, you need to open the terminal via the menu, or press ALT+F2 and execute the command "gnome-terminal".

Of course, my mistake. I have changed the defaults and get confused. I believe it should also be alt+ctrl+t, shouldn't it. Pardon me.

---

### Post by sanderd17 on 2010-12-18
I agree that ALT+CTRL+T isn't a good shortcut, I've set it to ALT+F3. I find it more logical: ALT+F2 to execute GUI apps and ALT+F3 to execute terminal apps.

---

