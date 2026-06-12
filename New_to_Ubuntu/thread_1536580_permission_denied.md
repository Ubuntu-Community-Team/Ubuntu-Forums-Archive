---
title: "permission denied"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Franz01 on 2010-07-22
I am running this command

sudo df > out.out

and what I receive is

-bash: out.out: Permission denied

What do I miss? 
I am 99% sure I ran it previously...

Thank you!

---

### Post by sisco311 on 2010-07-22
[https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo](https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo)

You need write and execute permission for the directory where out.txt is created or in if the file exist, execute permission for the directory and write permission for the file. 

```
sudo command | sudo tee /root/out.txt
```
or
```
sudo command > /tmp/out.txt
```

---

### Post by texpat on 2010-07-22
Must be that you don't have permission to write to that part of the file system you're trying to output onto. I also thought sudo would take care of this, but apparently it doesn't.

Try specifying a location that you _do_ have write permission for.

---

### Post by The Cog on 2010-07-22
There are 2 separate problems here. 

Firstly, **sudo df > out.out** opens the file out.out for writing to before launching the command **sudo df**. So it is trying to open out.out with your credentials, not roots. This is why you are gettiong permission denied.

Secondly, if you tried to run such a command and write to a file that you **are** allowed to write to, it would apparently freeze because the **[sudo] password for Franz01** prompt would get written to file instead of appearing on the screen.

Probably the best approach is to do:
> sudo bash -c 'df > /out.out'
if you want to output to a file that you don't have rights to write to.

---

### Post by texpat on 2010-07-22
> **The Cog said:**
> 
Secondly, if you tried to run such a command and write to a file that you **are** allowed to write to, it would apparently freeze because the **[sudo] password for Franz01** prompt would get written to file instead of appearing on the screen.


Hating to contradict here, but I *can* run ```
sudo df > out.txt
``` perfectly well. I am asked the password and, after entering it correctly, the command gets executed. Not sure why to use 'sudo' anyway, since it works without, too.

---

### Post by The Cog on 2010-07-22
> **texpat said:**
> Hating to contradict here, but I *can* run ```
sudo df > out.txt
``` perfectly well. I am asked the password and, after entering it correctly, the command gets executed.
You're right. I don't know where I got that idea from then. I must be remembering something slightly different.
>  Not sure why to use 'sudo' anyway, since it works without, too.Not if you don't have write permission to out.out.

---

### Post by texpat on 2010-07-23
> Not if you don't have write permission to out.out.

Which under normal circumstances would be anywhere outside the home directory, of course... Ack!

---

