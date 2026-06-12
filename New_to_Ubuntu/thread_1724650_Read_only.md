---
title: "Read only"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by bj218 on 2011-04-08
How can I change a read only document so I can edit it?

---

### Post by cjhabs on 2011-04-08
Select it, right click -> Properties -> Permissions -> Change Access to Read + Write

---

### Post by bj218 on 2011-04-08
> **cjhabs said:**
> Select it, right click -> Properties -> Permissions -> Change Access to Read + Write

I tried that a few minutes ago and it did not work

---

### Post by AlphaLexman on 2011-04-08
Are you the Owner of the file?
What is the output of ```
ls -l filename
```

---

### Post by bj218 on 2011-04-08
> **AlphaLexman said:**
> Are you the Owner of the file?
What is the output of ```
ls -l filename
```

Yes I am the owner.

---

### Post by AlphaLexman on 2011-04-08
Well, you didn't post the output of what I asked, so now please post the output so I can see the permissions of the file, pretty please, with sugar on top!

Else, just try this generic fix:
```
chmod 644 filename
```

---

### Post by bj218 on 2011-04-08
> **AlphaLexman said:**
> Well, you didn't post the output of what I asked, so now please post the output so I can see the permissions of the file, pretty please, with sugar on top!

Else, just try this generic fix:
```
chmod 644 filename
```

root@bill-desktop:/media/miscu# ls -l '/media/miscu/House Heater Inst..odt' 
-rwxrw-rw- 1 bill bill 13955 2011-04-08 11:39 /media/miscu/House Heater Inst..odt

---

### Post by bj218 on 2011-04-08
> **bj218 said:**
> root@bill-desktop:/media/miscu# ls -l '/media/miscu/House Heater Inst..odt' 
-rwxrw-rw- 1 bill bill 13955 2011-04-08 11:39 /media/miscu/House Heater Inst..odt

root@bill-desktop:/media/miscu# chmod 644 '/media/miscu/House Heater Inst..odt' 
root@bill-desktop:/media/miscu# sudo chmod 644 '/media/miscu/House Heater Inst..odt'
root@bill-desktop:/media/miscu#

---

### Post by AlphaLexman on 2011-04-08
> **bj218 said:**
> root@bill-desktop:/media/miscu# ls -l '/media/miscu/House Heater Inst..odt' 
-rwxrw-rw- 1 bill bill 13955 2011-04-08 11:39 /media/miscu/House Heater Inst..odt
Even though you are the owner of the file, you are **NOT** in your $HOME dir, so we need to look at the permissions of the parent directory of the file in question.

Post the output of:
```
echo $PWD; ls -l ..
```

---

### Post by bj218 on 2011-04-08
> **AlphaLexman said:**
> Even though you are the owner of the file, you are **NOT** in your $HOME dir, so we need to look at the permissions of the parent directory of the file in question.

Post the output of:
```
echo $PWD; ls -l ..
```

root@bill-desktop:/media/miscu# echo $PWD: ls -l ..
/media/miscu: ls -l ..
root@bill-desktop:/media/miscu#

---

### Post by AlphaLexman on 2011-04-08
The output you are posting does not look right please use CODE tags!

Here is what you posted:
> root@bill-desktop:/media/miscu# echo $PWD: ls -l ..
/media/miscu: ls -l ..
root@bill-desktop:/media/miscu#

Here is what my output looks like in CODE tags:
```
echo $PWD; ls -l ..
/home/AlphaLexman

total 24
drwxr-x---. 51 AlphaLexman Users  4096 Apr  8 16:26 AlphaLexman
drwxr-x---. 45 cantrell    Users  4096 Apr  5 22:30 cantrell
drwx------.  2 root        root  16384 Oct 30 17:00 lost+found

```

I need to see something like mine!

---

### Post by bj218 on 2011-04-08
I moved the file to /home/bill & I then went to properties & it says I am the owner. 

/home/bill/Desktop/Screenshot.png

root@bill-desktop:/media/miscu# cd /home
root@bill-desktop:/home# echo $PWD: ls -l ..
/home: ls -l ..
root@bill-desktop:/home# /home/bill
bash: /home/bill: is a directory
root@bill-desktop:/home#

called to dinner see U tomorrow!!

---

### Post by bj218 on 2011-04-09
When I moved the prog. to /home/bill the read only disappeared I can now edit it as I wish. I do not want the prog. in /home/bill is there some 
way I can remove the read only when the prog. is in /media/miscu?

---

### Post by AlphaLexman on 2011-04-09
> **bj218 said:**
> is there some 
way I can remove the read only when the prog. is in /media/miscu?
**NO**, You cannot remove 'read only' access you can only **add** write access, which requires root, or owner permissions.

---

