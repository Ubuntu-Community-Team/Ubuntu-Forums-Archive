---
title: "File permission help"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mvalviar on 2009-02-23
I'm the only one using my computer so I don't give file permissions that much attention. Not until this morning when I got a pop up before I reach the desktop when I turned my computer on. It says something about the .dmrc file. It says that .dmrc must have a 644 permission and that my home folder must be r/w only to me, the owner and it should be read only to others. When I checked the permissions of my home folder it is r/w to all. I don't mess with permissions and my mask is 0022 so how can this be?

---

### Post by sisco311 on 2009-02-23
[thread]976610[/thread]

---

### Post by Liviu-Theodor on 2009-02-23
I don't know what happened but you can solve this way: open the Properties->Permissions window for the folder, and change accordingly.
Alternate, enter in the command line:
```
sudo chmod u+rwx, go+r, go-wx /home/*homefolder*
```

---

### Post by mvalviar on 2009-02-23
Yea I already solved the problem by chmoding. What I wanted to know is how it happened in the first place. I haven't used chmod since I installed ibex.

---

### Post by mvalviar on 2009-03-05
Like I mentioned I fixed the permission issue using  chmod and I just noticed that every time I try to open a plain text file I am given a prompt saying that the file is an executable and gives me options if I want to run it in the terminal or display its contents. Checking under properties the check box for "allow executing file as a program" doesn't have a check meaning it doesn't have execute permision (ls also says so). Although the box doesn't have a check mark it has focus or highlight. When I check and uncheck the box the focus disappears and the gui no longer erroneously reports that the file is an executable. I have lots of text files like this that got this permission issue and I am wondering if someone out there got the same issue and has a quick fix for it. Thanks in advance.

---

### Post by shredder12 on 2009-03-06
well you can use chmod again... for this purpose..
if all your text files are in the same folder. then you can probably the following command..
```
sudo chmod 644 *.txt
```
actually you might have used 7 in place of 6 because of this you might have give executable permission to these files..
even though they are not executing..
7=4(open)+2(write)+1(execute)
this is how permissions are given...
hope this helps..

---

