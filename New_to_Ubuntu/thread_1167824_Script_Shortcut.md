---
title: "Script Shortcut"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by akkad on 2009-05-23
say i have a script ".sh" some where in my home directory "/home/myuser/somedire/myscript.sh", is it possible to set a short hand command for this script so i can execute it directly may be by one word like "myscript" from the command line?

something like those standard commands like "apt-get", u can execute it without telling where it is, if possible, how can i make sure that i will not mismatch with already assigned commands like apt and others?

---

### Post by jakupl on 2009-05-23
If you put the script in /bin then you will only need to write the filename to execute it.

---

### Post by akkad on 2009-05-23
i found that also bin can include links to script too right? so i created a link using the following command:
sudo ln -s ~/myscript.sh /bin/myscript

then i rebooted the system, but when i execute the command "myscript" it tells command not found, did i make any mistake ?

---

### Post by Volt9000 on 2009-05-23
> **akkad said:**
> i found that also bin can include links to script too right? so i created a link using the following command:
sudo ln -s ~/myscript.sh /bin/myscript

then i rebooted the system, but when i execute the command "myscript" it tells command not found, did i make any mistake ?

That looks right.
Do an ls of your /bin dir to see if you still have the symbolic link.

---

### Post by akkad on 2009-05-23
i swear the link is there.

---

### Post by akkad on 2009-05-23
by the way am using ubuntu server, does it matter?

---

### Post by Volt9000 on 2009-05-23
I don't think so; a symlink is a symlink, regardless of the version of Linux you're using.

Please humour me and paste the complete output of

```

ls /bin -l

```

---

### Post by akkad on 2009-05-23
here you go, this is the symbol i have there :
lrwxrwxrwx 1 root root      36 2009-05-23 19:59 tomstop -> apache-tomcat-6.0.18/bin/shutdown.sh

---

### Post by Volt9000 on 2009-05-23
> **akkad said:**
> here you go, this is the symbol i have there :
lrwxrwxrwx 1 root root      36 2009-05-23 19:59 tomstop -> apache-tomcat-6.0.18/bin/shutdown.sh

Ok it looks like you've set up a relative link, not an absolute one, so the "tomstop" command will only work if you're in the parent directory of apache-tomcat-6.0.18.

First remove the current link

```

sudo rm /bin/tomstop

```

Now re-create the link using the FULL PATH to the script. So for example if this script is in /usr/share/apache-tomcat-6.0.18/bin/ then you would type

```

sudo ln -s /usr/share/apache-tomcat-6.0.18/bin/shutdown.sh /bin/tomstop

```

As an added note: This is where coloured output comes in handy.
If you type

```

ls /bin -l --color=yes

```

you'll see your text become coloured, and any symbolic links that are invalid will appear in red text.

---

### Post by akkad on 2009-05-23
you are right, now its working.
thanks volt, you are the man :D

---

