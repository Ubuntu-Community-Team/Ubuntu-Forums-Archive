---
title: "sudo to change dir?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by minsf on 2009-03-10
first let me say that i like the sudo model and i'm not looking for root shell solutions as sudo -i or anything like that.
my problem is that when a directory somedir has permissions 770 and is owned by root:root, then "sudo cd somedir" does not work for me. i can of course, use sudo to change the permissions to 777, and then i can cd into it, but than everyone can cd into it... so i wounder if there is a better solution. 
thanks for your help

---

### Post by BrandonBan6 on 2009-03-10
Hi Minsf,

How about changing the the group of the directory? So the directory is owned by root:<shared group>, given you access and keeping others out (unless you add them to your group).

---

### Post by Nxion on 2009-03-10
> **minsf said:**
> first let me say that i like the sudo model and i'm not looking for root shell solutions as sudo -i or anything like that.
my problem is that when a directory somedir has permissions 770 and is owned by root:root, then "sudo cd somedir" does not work for me. i can of course, use sudo to change the permissions to 777, and then i can cd into it, but than everyone can cd into it... so i wounder if there is a better solution. 
thanks for your help



Can you elaborate on what directory? I have never seen that problem before. Is this on only one directory or mutiple?

---

### Post by LowSky on 2009-03-10
What directory is causing the issue, you should be albe to move to any directory, just not use the files contained

you can always add the folder to the sudo group, or even to your users name so sudo/root access isn't always needed.

---

### Post by Flimm on 2009-03-10
For directories, the execute permission actually means the permission to cd to it. So what you want is 771, and 775 if you want to be able to view its contents.

---

### Post by scphan on 2009-03-10
here's a link to a chmod tutorial with numbers [http://catcode.com/teachmod/]("http://catcode.com/teachmod/"), you can also 'sudo chown <user>:<group> dir' to change ownership

---

### Post by Tibuda on 2009-03-10
You may cd to that directory within "sudo su"

---

### Post by minsf on 2009-03-10
first, thanks everyone- you guys are the best.

the reason why i cannot cd to this directory, is because it is owned by user root and group root. it does not matter what directory. try for instance "sudo mkdir somedir" and then "sudo chmod 770 somedir". then try to cd into somedir...

when i think about it, there may be a _security problem_. if "sudo cd somedir" was allowed for me, then when the command was done i would no longer be root, and i would have find myself in a directory where i am not supposed to be (as minsf is not allowed in 770 owned by root). for instance, try "sudo bash" and then "cd somedir" and then exit the root shell with "exit". you'll be thrown back to the parent directory. but this is not a real problem for me, since ideally i would run: sudo "cd && somecommand", and after all is done, i'd be thrown back to the parent- no problem, except this does not work...

it seems like the _real problem_ is that cd is not a real command, and therefore sudo cannot execute it. from what i understand (and that's not much...LOL) cd is more like a bash internal shortcut that changes the path momentarily so all your commands will be run with this extra path. following this logic, i tried "sudo bash cd somedir" but this generates an error... 

_regarding your permission suggestions:_ thanks for the link about permissions, though i'm familiar with them- i probably dont want 771 or 775 (i may be paranoid, but why would i let everyone in the world to cd to this dir?). changing the group seems to be the easiest workaround as suggested in post #2. _is there something like a "sudo" group, or should i just use the "admin" group?_

---

### Post by Flimm on 2009-03-11
You can't sudo cd into anything, no matter what the permissions of the directory are, because as soon as the command has finished executing, the terminal goes back to the previous cwd. This is always the case, and one of the main reasons for sudo -i.

---

### Post by BrandonBan6 on 2009-03-11
> **minsf said:**
>  changing the group seems to be the easiest workaround as suggested in post #2. _is there something like a "sudo" group, or should i just use the "admin" group?_

You can create a group with "groupadd", or you can use the group that your username is in. 

Something like this  should change the group to yours:
```
sudo chgroup -hR <new group name> <directory name> 
```

---

### Post by bodhi.zazen on 2009-03-11
Just a passing comment ...

You need to use Encryption, Apparmor or SElinux if you wish to restrict root, otherwise you can will always be able so "sudo cd" or otherwise access the directory / file with root powers, regardless of ownership or permissions.

---

