---
title: "Installing A Program"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by GaryPG2 on 2009-08-03
For the first time I installed a program (Sweet Home 3D) that did not come from the Add Program command. I downloaded the file and expanded it to a folder on the desktop. The program runs by double clicking a file which is a shell script. My question is where should this folder be stored? I know Windows puts them in Program Files. Is there an equivalent in Ubuntu?

Also how do I add this program to the Applications Menu?

Thanks for your help.

---

### Post by Bruce M. on 2009-08-03
> **GaryPG2 said:**
> For the first time I installed a program (Sweet Home 3D) that did not come from the Add Program command. I downloaded the file and expanded it to a folder on the desktop. The program runs by double clicking a file which is a shell script. My question is where should this folder be stored? I know Windows puts them in Program Files. Is there an equivalent in Ubuntu?

Also how do I add this program to the Applications Menu?

Thanks for your help.

Yes there is an equivalent it's called your "home" directory:

/home/your_user_name.

So you have SH3D in: /home/your_user_name/Desktop/SH3D (for example)

Move SH3D to /home/your_user_name/

Now right click on your desktop, and "Create Launcher"

Name: SHome 3D  (example)
Comment: (whatever you want)
Command: use the folder icon and browse to the "shell script" that starts it. Then get an icon and click on "Use startup notification", [Create] and your done.

Have a nice day.
Bruce

---

### Post by bodhi.zazen on 2009-08-03
The linux file system is a bit different then windows.

The preferred location for apps outside the repos, is /usr/local/

There is nothing wrong with leaving it in $HOME or moving it to ~/bin 

There are tons of referances on Google, but this is not a bad one to get you started :

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

