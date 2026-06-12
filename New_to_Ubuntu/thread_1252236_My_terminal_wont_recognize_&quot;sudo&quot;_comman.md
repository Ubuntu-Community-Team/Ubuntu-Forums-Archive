---
title: "My terminal wont recognize &quot;sudo&quot; command!!!"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Cannon1230 on 2009-08-28
Oh CRAP! Please tell me I didn't mess something up....I think I added something to my sources list that I shouldnt have...heres what I added to the terminal.. gksu gedit /ept/apt/sources.list
then I removed the # from the following commands in the source list
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
then I added this to the source list, and terminal, because I'm a stoopid noob and dont know what I'm doing...
 sudo aptitude update && sudo aptitude install ubuntu-restricted-extras non-free-codecs libdvdcss2 -y
Now my terminal will not recognize the "sudo" command!!!!!! 

I was just following instructions on how to set up my 9.04 jaunty from some web site
This is what my terminal says now when I try to enter a "sudo" command......
cannon@lappy:~$ sudo aptitude install preload
E: Type 'sudo' is not known on line 50 in source list /etc/apt/sources.list
E: Type 'sudo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'sudo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
cannon@lappy:~$ 

Someone please tell me I'm not screwed on this, and how to fix it! I'm still learning, and I guess this is part of the process! SOMEONE PLEASE HELP!

Cannon

---

### Post by scrooge_74 on 2009-08-28
just open a terminal type sudo nano /etc/apt/sources.list

Start there so you can fix any mistakes you made, you can even post what is in the file so others can take a look at it

---

### Post by MTGap on 2009-08-28
What are you trying to do /etc/apt/sources.list is for repositories. Just edit the file again and undo those changes you made. (You can still use sudo it's just because you were trying to upgrade and you add random crap in your sources.list)

---

### Post by scrooge_74 on 2009-08-28
that is why I told him to fix the file ;)

---

### Post by snowpine on 2009-08-28
Please post the output of 

```
cat /etc/apt/sources.list
```

Whatever is on line 50 of that file is wrong.

---

### Post by MTGap on 2009-08-28
Well I'm sorry, but I did quick reply and at the time your reply wasn't up. Is there even a delete message thing?

---

### Post by Cannon1230 on 2009-08-28
> **snowpine said:**
> Please post the output of 

```
cat /etc/apt/sources.list
```Whatever is on line 50 of that file is wrong.


this is the output...

cannon@lappy:~$ cat /ect/apt/sources.list
cat: /ect/apt/sources.list: No such file or directory

thanks!

---

### Post by oldos2er on 2009-08-28
Please copy and paste the command snowpine gave you. It's etc, not ect.

---

### Post by jerome1232 on 2009-08-28
You need to remove the line that looks like this in your source file.

```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras non-free-codecs libdvdcss2 -y
```

just do the gksu gedit /etc/apt/sources.lst command again and fix the file up.

---

### Post by Cannon1230 on 2009-08-28
> **jerome1232 said:**
> You need to remove the line that looks like this in your source file.

```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras non-free-codecs libdvdcss2 -y
```

just do the gksu gedit /etc/apt/sources.lst command again and fix the file up.
My man!!! That did it! Thanks so much dude!

---

### Post by colau on 2009-09-01
> **Cannon1230 said:**
> this is the output...

cannon@lappy:~$ cat /ect/apt/sources.list
cat: /ect/apt/sources.list: No such file or directory

thanks!
That was 
```

cat /etc/apt/sources.list

```
not
```

cat /[COLOR="Red"]**ect**[/COLOR]/apt/sources.list

```

---

