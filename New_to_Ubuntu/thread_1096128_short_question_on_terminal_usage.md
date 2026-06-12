---
title: "short question on terminal usage"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by stoppage on 2009-03-14
Hi, just a quick question...if I'm in recovery mode on bootup and using terminal commands, I have no mouse to mark text, so how can I save terminal output please?

---

### Post by mvalviar on 2009-03-14
you can redirect the output of the command to a file. Like if you want to save the output of the ls command to a text file use
```
ls > output.text
```

---

### Post by sisco311 on 2009-03-14
> **stoppage said:**
> Hi, just a quick question...if I'm in recovery mode on bootup and using terminal commands, I have no mouse to mark text, so how can I save terminal output please?

You can redirect the output to a file:
```
command > /home/username/filename
```
to append the file:
```
command2 >> /home/username/filename
```

---

### Post by stoppage on 2009-03-14
Thank you for such a prompt reply....one more question...the "cat" command in terminal, will it only read .txt files? I  tried to read an oo file, its rubbish, looks like ASCII

---

### Post by Kareeser on 2009-03-14
Only plaintext files, yes.

---

### Post by stoppage on 2009-03-14
Obliged

---

### Post by Miljet on 2009-03-14
For clarification, the file names do not need to end with .txt. Almost all configuration files such as /boot/grub/menu.list or /etc/fstab can be read with the cat command.

---

### Post by mvalviar on 2009-03-14
> **Miljet said:**
> For clarification, the file names do not need to end with .txt. Almost all configuration files such as /boot/grub/menu.list or /etc/fstab can be read with the cat command.

Amen. GNU/Linux doesn't care how you name files with the exception of files staring with a "." (dot files). They are treated as hidden files. You may cat any file to the screen but if its not meant to be read or has some kind of formatting to be read by another application you'll just see a screen full of ascii garbage.

---

