---
title: "Read Only"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by bj218 on 2010-11-10
I was printing a bunch of replies from ? the I had asked on the internet.
I have about 6 pages so far but the last 1 that I copied changed my 
document to Read Only & know I am unable to make changes or corrections.
How do I get read of read only?

---

### Post by Crusty Old Fart on 2010-11-11
Assuming the name of the file is: **filename**
From within the directory where **filename** resides, issue the following command:
```

chmod 700 **filename**

```

---

### Post by llamabr on 2010-11-11
sometimes it's also as simple as saving a new copy with a new name in your home directory.  When you open a new file with openoffice, for example, it will save in /tmp and open read only.  Saving a copy in your /home/dir will fix that.

---

### Post by bj218 on 2010-11-12
> **Crusty Old Fart said:**
> Assuming the name of the file is: **filename**
From within the directory where **filename** resides, issue the following command:
```

chmod 700 **filename**

```

/home/bill/Desktop/Screenshot.png
After using the above command I now can not view this document? I also had a copy
in home/bill and I can not view it there either?

---

### Post by Crusty Old Fart on 2010-11-12
Oh...I see.

Well, Bill...I had assumed that you (as user: bill) were the owner of the file and that the permissions were messed up. That may have been the case. But there may be another problem in that user: bill doesn't seem to own the file.

You can fix that with the following command:
```

sudo chown bill **[B]filename**[/B]

```That should do it.

Sorry for my oversight.

If you still have problems with it please post the output that you get from the following command:
```

ls -l **filename**

```That should show us the permission levels and ownership of the file so we can see exactly what needs to be done rather than guessing.

Good luck.

---

### Post by bj218 on 2010-11-13
> **Crusty Old Fart said:**
> Oh...I see.

Well, Bill...I had assumed that you (as user: bill) were the owner of the file and that the permissions were messed up. That may have been the case. But there may be another problem in that user: bill doesn't seem to own the file.

You can fix that with the following command:
```

sudo chown bill **[B]filename**[/B]

```That should do it.

Sorry for my oversight.

If you still have problems with it please post the output that you get from the following command:
```

ls -l **filename**

```That should show us the permission levels and ownership of the file so we can see exactly what needs to be done rather than guessing.

Good luck.

The first command removed the X so I can again at least read the document.
I can not do the 2nd command can you tell me if I doing something wrong?
root@bill-desktop:/home/bill# sudo chown bill '/media/test my data/My  Notes 1.odt' 
root@bill-desktop:/home/bill# ls -l  '/media/test my data/My  Notes 1.odt' 
-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt
root@bill-desktop:/home/bill#  ls -l  '/media/test my data/My  Notes 1.odt' 
-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt
root@bill-desktop:/home/bill# ls -l "'/media/test my data/My  Notes 1.odt'"
ls: cannot access '/media/test my data/My  Notes 1.odt': No such file or directory
root@bill-desktop:/home/bill# 
I think I attached something that I should not have  please ignore it.

---

### Post by bj218 on 2010-11-13
> **llamabr said:**
> sometimes it's also as simple as saving a new copy with a new name in your home directory.  When you open a new file with openoffice, for example, it will save in /tmp and open read only.  Saving a copy in your /home/dir will fix that.

Thanks your suggestion worked I sure learned something very useful to day.

---

### Post by Crusty Old Fart on 2010-11-13
> **bj218 said:**
> The first command removed the X so I can again at least read the document.
I can not do the 2nd command can you tell me if I doing something wrong?
root@bill-desktop:/home/bill# sudo chown bill '/media/test my data/My  Notes 1.odt' 
root@bill-desktop:/home/bill# ls -l  '/media/test my data/My  Notes 1.odt' 
-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt
root@bill-desktop:/home/bill#  ls -l  '/media/test my data/My  Notes 1.odt' 
-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt
root@bill-desktop:/home/bill# ls -l "'/media/test my data/My  Notes 1.odt'"
ls: cannot access '/media/test my data/My  Notes 1.odt': No such file or directory
root@bill-desktop:/home/bill# 
I think I attached something that I should not have  please ignore it.
Howdy Bill:

Thank you for posting your output, especially since you thought the second command wasn't working. It worked the first time, and the second time, but it didn't work the third time because you had wrapped your file name in too many quotation marks. Let's take a look at what happened the first time you entered the command:
```

[COLOR=Green]***~~~ You entered: ~~~***[/COLOR]
 ls -l  '/media/test my data/My  Notes 1.odt' 
[COLOR=Red][I][B]
~~~ output ~~~
[/B][/I][/COLOR]-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt

```Perhaps you didn't think it worked because you only got one line of output. But that's because the **ls -l** command was only given one file to list, _as intended_.

Now, let's focus on the first part of the line of output, which is marked up in different colors below:[INDENT][SIZE=1][COLOR=Red]**[COLOR=Black]-[/COLOR][COLOR=Blue]rwx[/COLOR][COLOR=Green]---[/COLOR]---**[/COLOR][COLOR=Black] 1 [/COLOR]**[COLOR=Blue]bill [COLOR=Green]root[/COLOR][/COLOR]** 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt[/SIZE]

The first part shows the permission levels for **[COLOR=Blue]owner[/COLOR]**, **[COLOR=Green]group[/COLOR]**, and [COLOR=Red]**world**[/COLOR] as indicated by the corresponding colors below:

[SIZE=2][COLOR=Red]**[COLOR=Black]-[/COLOR][COLOR=Blue]rwx[/COLOR][COLOR=Green]---[/COLOR]---**[/COLOR][/SIZE]

So, the [COLOR=Blue]**owner's**[/COLOR] permissions are: [SIZE=2][COLOR=Red]**[COLOR=Blue]rwx[/COLOR]**[/COLOR][/SIZE], which means [COLOR=Black]**R**[/COLOR]ead, **W**rite, and e[COLOR=Black]**X**[/COLOR]ecute.
The three green dashes ([SIZE=2][COLOR=Red]**[COLOR=Green]---[/COLOR]**[/COLOR][/SIZE]) indicate the permissions for the **[COLOR=Green]group[/COLOR]**. Since there are no instances of r, w, or x here, the **[COLOR=Green]group[/COLOR]** has no permissions. Same for the three red dashes ([SIZE=2][COLOR=Red]**---**[/COLOR][/SIZE]), which indicate that the [COLOR=Red]**world**[/COLOR] has no permissions.

So, from the output you got, we know that the **[COLOR=Blue]owner[/COLOR]** of this file has full privileges. He has permission to read from, write to, and execute (run), the file.

Now, let's look at the part that shows which user _owns_ the file. It shows this:

[SIZE=2]**[COLOR=Blue]bill [COLOR=Green]root[/COLOR][/COLOR]**[/SIZE]

It tells us that user: [SIZE=1]**[COLOR=Blue]bill[/COLOR]**[/SIZE] is the owner and his primary group is [SIZE=1]**[COLOR=Blue][COLOR=Green]root[/COLOR][/COLOR]**[/SIZE].

_In conclusion:_ We are being told by the system that bill owns the file and has full privileges. So, you should be able to do anything you want with that file now, without having to use **sudo**.

[/INDENT]How's that?...Clear as mud?

By the way...you seem to elevate your status to becoming root unnecessarily. Your use of **sudo su** kind of gives that away when you may have been able to use just **sudo** to get single commands to run with root permissions. Also, the user: bill is a member of the group: root. I don't recommend that. But, I'm tired of beating that horse, and you're probably tired of hearing it. So I'll leave it at that.

Thanks again for posting your output. Most other newbies wouldn't have done that if they thought the command failed and I would have had to ask them a second time.

Good luck,

Crusty

---

### Post by bj218 on 2010-11-14
> **Crusty Old Fart said:**
> Howdy Bill:

Thank you for posting your output, especially since you thought the second command wasn't working. It worked the first time, and the second time, but it didn't work the third time because you had wrapped your file name in too many quotation marks. Let's take a look at what happened the first time you entered the command:
```

[COLOR=Green]***~~~ You entered: ~~~***[/COLOR]
 ls -l  '/media/test my data/My  Notes 1.odt' 
[COLOR=Red][I][B]
~~~ output ~~~
[/B][/I][/COLOR]-rwx------ 1 bill root 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt

```Perhaps you didn't think it worked because you only got one line of output. But that's because the **ls -l** command was only given one file to list, _as intended_.

Now, let's focus on the first part of the line of output, which is marked up in different colors below:[INDENT][SIZE=1][COLOR=Red]**[COLOR=Black]-[/COLOR][COLOR=Blue]rwx[/COLOR][COLOR=Green]---[/COLOR]---**[/COLOR][COLOR=Black] 1 [/COLOR]**[COLOR=Blue]bill [COLOR=Green]root[/COLOR][/COLOR]** 31550 2010-11-10 15:50 /media/test my data/My  Notes 1.odt[/SIZE]

The first part shows the permission levels for **[COLOR=Blue]owner[/COLOR]**, **[COLOR=Green]group[/COLOR]**, and [COLOR=Red]**world**[/COLOR] as indicated by the corresponding colors below:

[SIZE=2][COLOR=Red]**[COLOR=Black]-[/COLOR][COLOR=Blue]rwx[/COLOR][COLOR=Green]---[/COLOR]---**[/COLOR][/SIZE]

So, the [COLOR=Blue]**owner's**[/COLOR] permissions are: [SIZE=2][COLOR=Red]**[COLOR=Blue]rwx[/COLOR]**[/COLOR][/SIZE], which means [COLOR=Black]**R**[/COLOR]ead, **W**rite, and e[COLOR=Black]**X**[/COLOR]ecute.
The three green dashes ([SIZE=2][COLOR=Red]**[COLOR=Green]---[/COLOR]**[/COLOR][/SIZE]) indicate the permissions for the **[COLOR=Green]group[/COLOR]**. Since there are no instances of r, w, or x here, the **[COLOR=Green]group[/COLOR]** has no permissions. Same for the three red dashes ([SIZE=2][COLOR=Red]**---**[/COLOR][/SIZE]), which indicate that the [COLOR=Red]**world**[/COLOR] has no permissions.

So, from the output you got, we know that the **[COLOR=Blue]owner[/COLOR]** of this file has full privileges. He has permission to read from, write to, and execute (run), the file.

Now, let's look at the part that shows which user _owns_ the file. It shows this:

[SIZE=2]**[COLOR=Blue]bill [COLOR=Green]root[/COLOR][/COLOR]**[/SIZE]

It tells us that user: [SIZE=1]**[COLOR=Blue]bill[/COLOR]**[/SIZE] is the owner and his primary group is [SIZE=1]**[COLOR=Blue][COLOR=Green]root[/COLOR][/COLOR]**[/SIZE].

_In conclusion:_ We are being told by the system that bill owns the file and has full privileges. So, you should be able to do anything you want with that file now, without having to use **sudo**.

[/INDENT]How's that?...Clear as mud?

By the way...you seem to elevate your status to becoming root unnecessarily. Your use of **sudo su** kind of gives that away when you may have been able to use just **sudo** to get single commands to run with root permissions. Also, the user: bill is a member of the group: root. I don't recommend that. But, I'm tired of beating that horse, and you're probably tired of hearing it. So I'll leave it at that.

Thanks again for posting your output. Most other newbies wouldn't have done that if they thought the command failed and I would have had to ask them a second time.

Good luck,

Crusty

Thanks for the explanation every little helps me to learn a bit more.

---

### Post by Crusty Old Fart on 2010-11-14
You're mighty welcome.

---

