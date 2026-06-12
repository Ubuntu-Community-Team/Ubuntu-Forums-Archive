---
title: "Need help with system administration"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by MrLowEnd on 2009-02-05
I'm having trouble putting myself as an administrator on the system. I'm trying to be able to add files to certain directories, but I can't seem to get it right. Can somebody help me? I would like a process step-by-step, that'd be greatly appreciated.

---

### Post by SteveNorman on 2009-02-05
mv filename.xxx directory_name

example, to move a file called poo.txt into the directory called toilet

```
mv poo.txt toilet
```

if the file is far away from the directory, you may have to use full pathnames

if poo is in your home directory, and toilet is in another place, either change to the toilet directory or give the full pathname

toilet is in /house/bathroom/toilet

then the command is ```
mv poo.txt /house/bathroom/toilet
```

or change to the toilet directory first, then give the full pathname to poo.txt

```

cd toilet
mv /body/intestines/poo.txt toilet
```

hope that helps

---

### Post by SteveNorman on 2009-02-05
Oh BTW I found this to be very helpful when learning the command line:

[HTML]http://www.ee.surrey.ac.uk/Teaching/Unix/[/HTML]

---

### Post by SteveNorman on 2009-02-06
Im gonna post this in case anyone else has this question as well'

when ever you change a root file you need to use sudo or gksudo before all commands.

so ```
mv file.xxx /
```

will be

```
sudo mv file.xxx /
```
You can manipulate your sudoers file so you dont have to type your password all the time, and you can also log in as root. both of these situations invite trouble for you, as it becomes easier to hack your box. It also becomes easier for you to make a mistake. Its better to use sudo till you get all guru and stuff.

[http://www.easy-ubuntu-linux.com/ubuntu-root-access.html](http://www.easy-ubuntu-linux.com/ubuntu-root-access.html)

---

### Post by carml on 2009-02-06
The site linuxcommand.org may help,you can also look at System->Help & Support for a brief guide to commands.:)

---

