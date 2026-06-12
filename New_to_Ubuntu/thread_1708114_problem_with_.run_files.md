---
title: "problem with .run files"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by BinaryEnCoder on 2011-03-16
Hello everyone! 
I had several problems on installing a run file. Its weird because 
on ubuntu 9 i just ./file.run and it would installed fine 
whats the problem ? 

```
root@hemicranea:/home/it03# wget [http://updates.metasploit.com/data/releases/framework-3.6.0-linux-full.run](http://updates.metasploit.com/data/releases/framework-3.6.0-linux-full.run)
--2011-03-16 08:43:08--  [http://updates.metasploit.com/data/releases/framework-3.6.0-linux-full.run](http://updates.metasploit.com/data/releases/framework-3.6.0-linux-full.run)
Resolving updates.metasploit.com... 184.154.104.2
Connecting to [updates.metasploit.com]("http://updates.metasploit.com/")|184.154.104.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 156587790 (149M) [application/octet-stream]
Saving to: `framework-3.6.0-linux-full.run'

100%[======================================>] 156,587,790 3.65M/s   in 41s     

2011-03-16 08:43:50 (3.60 MB/s) - `framework-3.6.0-linux-full.run' saved [156587790/156587790]

root@hemicranea:/home/it03# chmod +x framework-3.6.0-linux-full.run 
root@hemicranea:/home/it03# ./framework-3.6.0-linux-full.run 
bash: ./framework-3.6.0-linux-full.run: No such file or directory
root@hemicranea:/home/it03# 

```

---

### Post by gandaran on 2011-03-16
> bash: ./framework-3.6.0-linux-full.run: No such file or directory
where is the file, in the downloads folder? if correct cd to the downloads folder first or move the file to home.
one trick that always work is to just type ./ or sh in terminal then drag the file with mouse to inside terminal and hit enter.

---

### Post by BinaryEnCoder on 2011-03-16
i've done that also, didnt work
i did then chmod 777 and was executable by anybody 
but still didnt work
them i copied to the / folder
and tried to execute from there but it still didnt work :S

i'm kinda angry now because its very simple, i used to install it very quickly

anyway 
any ideas ?

---

### Post by gandaran on 2011-03-16
> **BinaryEnCoder said:**
> i've done that also, didnt work
i did then chmod 777 and was executable by anybody 
but still didnt work
them i copied to the / folder
and tried to execute from there but it still didnt work :S

i'm kinda angry now because its very simple, i used to install it very quickly

anyway 
any ideas ?
try using [COLOR="Red"]sh[/COLOR] instead ./, using sh you don't need to chmod the file.
or install this nautilus script package, with this nautilus script you can run any .run or .bin file.
[http://hacktolive.org/wiki/App_Runner](http://hacktolive.org/wiki/App_Runner)

edit: try double clicking the .run file and choose run, it should work if you haven't changed the nautilus file run default settings.

---

### Post by BinaryEnCoder on 2011-03-16
i've tried the sh in the beginning but it sayed an error like "syntax error '(' " 
anyway i'll try the nautilus plugin
when i doubleclick it nothing happens 
i;ve installed it from a tall bar for now because i needed it quicly 
thnx for your help anyway :)

---

### Post by oldos2er on 2011-03-16
This error could be caused by trying to run a 32-bit executable in a 64-bit environment. What does f**ile framework-3.6.0-linux-full.run** say?

---

### Post by oldos2er on 2011-03-16
This error could be caused by trying to run a 32-bit executable in a 64-bit environment. What does **file framework-3.6.0-linux-full.run** say? And if you are running 64-bit Ubuntu, you'll need to install ia32-libs to run 32-bit programs.

---

