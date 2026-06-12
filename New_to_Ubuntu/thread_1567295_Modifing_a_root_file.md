---
title: "Modifing a root file"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by seattle vic on 2010-09-03
I'm trying to install a program in /etc and make a mod to a conf file, but can't, even if I use sudo.

For example, if I create a directory and file: /etc/test/testfile using sudo, I can read the file, edit the file and delete the file, but what I can't seem to do is:

> sudo echo 'this is a test' > testfile

The result is:

bash: testfile: Permission denied

Here are the permissions:

drwxr-xr-x   2 root root  4096 2010-09-03 11:28 .
drwxr-xr-x 166 root root 12288 2010-09-03 10:43 ..
-rw-r--r--   1 root root    20 2010-09-03 11:28 testfile



What am I missing here?  I thought that as sudo I can do anything?

---

### Post by Smart Viking on 2010-09-03
Weird same happens to me.

But i could do this though:

```
[smartviking@localhost test]$ sudo su
[root@localhost test]# ls
testfile
[root@localhost test]# echo 'this is a test' > testfile 
[root@localhost test]# exit

```:)

---

### Post by da burger on 2010-09-03
sudo will allow you to do anything, BUT sudo applies to only the command, not the bash piping and such. If you give me a minute or two I'll try and remember a way to get around this.

EDIT, Couple of other things, @SM what you did worked because sudo su launches bash as root meaning everything is run with privileges including piping. And for future reference I believe is is advised to use sudo -i instead of sudo su.

EDIT2 Found a way of doing it. Run the command ```
echo "stuff" | sudo tee filename
``` to replace piping with >. To replace piping with >> add the -a option to tee. This will also produce output on stdout as well as in the file. If this is problematic for some reason just add ```
>/dev/null
``` to the end.

Angus.

---

### Post by seattle vic on 2010-09-03
OK, now I understand.

Thank you...

---

### Post by ranch hand on 2010-09-03
I am not sure you want the work test in there as it is a built in command in bash.

---

