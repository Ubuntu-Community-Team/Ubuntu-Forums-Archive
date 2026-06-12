---
title: "sudo commnads"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-15
Is there a list of the different sudo commands? I am at complete loss about this. Any reading material?

Thanks

---

### Post by alwayshere on 2009-11-15
[https://help.ubuntu.com/community/RootSudo#Background%20Information](https://help.ubuntu.com/community/RootSudo#Background%20Information)

---

### Post by mathfreak123 on 2009-11-15
I would think that any command there is, you can use sudo on it. You should only use sudo when you need to, though.

To start, I think reading up on what the commands do would be good. However, since there are so many commands, knowing all of them would be nigh impossible. Instead, you can use the "man" (for "manual") command to learn what all the commands do.

examples:

man wget
man ls
man shutdown

Man basically shows you the guide to all the commands, so it's very useful.

---

### Post by theozzlives on 2009-11-15
> **daniell59 said:**
> Is there a list of the different sudo commands? I am at complete loss about this. Any reading material?

Thanks

Any command can be a sudo command. all sudo does is give you root access to files and stuff, example: if you want to copy a file to a folder owned by root, you would do:
```
sudo cp <source> <destination>
```

or if you want to edit a file owned by root:
```
gksudo gedit <filename>
```

note: the gk is used when you want to use a GUI application.

---

### Post by alwayshere on 2009-11-15
[http://www.vogella.de/articles/Ubuntu/article.html](http://www.vogella.de/articles/Ubuntu/article.html)

---

### Post by nitstorm on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)  

Try that thread, found it very useful, lots of reading material there, newbie here and found it pretty good :D

---

### Post by nitstorm on 2009-11-15
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  found this the most useful link of them all :)

---

### Post by Wim Sturkenboom on 2009-11-15
I think that your question is not so much about sudo, but about the commandline. [http://www.tldp.org/](http://www.tldp.org/) might be a start

And below a list of commands extracted from my history
locate
vi
cd
ls
echo
grep
reset
exit
man somecommand
file
reset
df
du
stat
cp
mkdir
mv
sh
which
tree
nano
tracert
visudo
cat
ln
touch
su
gcc
fdisk
dmesg
lspci
hexdump
find
iptables
mount
lsusb
history

---

### Post by lisati on 2009-11-15
Have a look here for information on using sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As someone else has already commented, I don't think you should use sudo unless you have to, because "super user" privileges give you great power to do many things, including seriously hurting your system when you make a typo.

---

### Post by daniell59 on 2009-11-15
Thanks to all. Your replies illustrate the fact that I know even less than I thought I did. I really need to know the basics. So far Ubuntu 9.10 is working great. My previous version of 9.04 gave me problems. Recently, I found that the problem was not Ubuntu, rather my memory. The voltage and timings needed to be changed. Once done, everything improved.

---

