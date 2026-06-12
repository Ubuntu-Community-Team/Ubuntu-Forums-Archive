---
title: "lost admin password"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by clkbubba on 2010-12-14
Hello
I am using ubuntu 10.10 amd was installing some software from the free software feature and the system wanted a restart. Now it will not recognize my login password. Is there some way I can reset it? In the recovery mode mode it will recognize it and welcome me in the text that it runs, but how do I get the GUI to load and stop all that command line stuff that I know squat about.
Oh great wizards what is the secret command? 
Please help. Thanks in advance.
Bubba

---

### Post by theozzlives on 2010-12-14
> **clkbubba said:**
> Hello
I am using ubuntu 10.10 amd was installing some software from the free software feature and the system wanted a restart. Now it will not recognize my login password. Is there some way I can reset it? In the recovery mode mode it will recognize it and welcome me in the text that it runs, but how do I get the GUI to load and stop all that command line stuff that I know squat about.
Oh great wizards what is the secret command? 
Please help. Thanks in advance.
Bubba

Go to Recovery mode > root prompt and type:
```
passwd <yourusername>
```
it'll ask twice, but that should fix it.

---

### Post by clkbubba on 2010-12-14
Sorry i lied I am using 10.40 

In recovery it asks for the login which is administrator and the for my password ****** and it then says welcome to Ubuntu 
* documentation Then the help url 
0 packages can be updated
0 updates are security updates
I now have a prompt that 
administrator@ubuntu:~$


What do I do now?

---

### Post by coffeecat on 2010-12-14
I guess you've gone to the wrong option in the recovery mode. After you select recovery mode from the grub menu, you are presented with another menu. Choose 'drop to root prompt' at the bottom of this menu. You will end up with a # prompt, not a $ prompt and no prompt for a password. This is a root shell, so be careful. Now, simply do the command that theozzlives posted.

If you want a fuller howto, have a look here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by clkbubba on 2010-12-14
Thanks for the info. All was well untill.......
ls /home took me to the administrator.
root@ubuntu:~# passwd *****   Responds with 
passwd: user <*****> does not exist

Now what to do?

---

### Post by coffeecat on 2010-12-14
> **clkbubba said:**
> ls /home took me to the administrator.

ls /home doesn't take you anywhere. It simply lists the names of the folders to be found in the /home directory. The names of the folders **are** the names of any user accounts on the computer. You simply need to substitute whichever user account name you need to change the password for in:

```
passwd <username>
```

If you get an error you are typing in something wrong.

---

