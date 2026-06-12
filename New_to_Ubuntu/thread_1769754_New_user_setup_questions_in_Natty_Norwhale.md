---
title: "New user setup questions in Natty Norwhale"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-05-28
Recent install of Ubuntu 11.04 desktop.   I have three users set up on the system.   It seems by default that Natty allows different users to read each others files.     What would be the best way to set up so that the different users cannot not see or read each others files? 

All help and advise is appreciated.

---

### Post by frankbooth on 2011-05-28
Sounds strange...

Anyway, a simple solution would be to change the rights of the home folders.

But maybe there's a better way?

---

### Post by Paqman on 2011-05-28
You should just be able to:
```
sudo chmod -R o= /home
```

This takes away all permissions for "others" in your home folder. Users will only be able to read files from their own home.

I've not tried it though, it might be safer to apply it to each user's home folder, rather than /home itself.

---

### Post by bodhi.zazen on 2011-05-28
> **rbowen1 said:**
> Recent install of Ubuntu 11.04 desktop.   I have three users set up on the system.   It seems by default that Natty allows different users to read each others files.     What would be the best way to set up so that the different users cannot not see or read each others files? 

All help and advise is appreciated.

This is indeed the default behavior of Ubuntu (home directories are world readable).

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)

You can fix this by setting preferred permissions for home directories.

---

### Post by rbowen1 on 2011-05-28
> **bodhi.zazen said:**
> This is indeed the default behavior of Ubuntu (home directories are world readable).

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)

You can fix this by setting preferred permissions for home directories.

Partial fix!   I can go to my home directory and view properties/permissions, select others and then change to none on folder access which will make my files not be seen or read by other users.  However I cannot change the folder permissions for the home directory of the other users.  It is grayed out.     Since the other users have already set their passwords, I have no way to login as them to change the folder permissions for their home directory.  

How do I log in as the root account so I can change the user home directory folder permissions?

---

### Post by Thewhistlingwind on 2011-05-28
> **rbowen1 said:**
> 
How do I log in as the root account so I can change the user home directory folder permissions?

Sudo -s

or 

gksudo nautilus

Warning, these are both incredibly dangerous.

---

### Post by Paqman on 2011-05-29
> **rbowen1 said:**
> 
How do I log in as the root account so I can change the user home directory folder permissions?

On Ubuntu you don't log in as root. You prefix terminal commands with "sudo" to temporarily gain root's privileges, or for graphical apps like the Nautilus file browser you can launch them with the prefix "gksudo".

So for example to launch a root file browser, hit alt-F2 and type:
```
gksudo nautilus
```

---

### Post by rbowen1 on 2011-05-29
> **Paqman said:**
> On Ubuntu you don't log in as root. You prefix terminal commands with "sudo" to temporarily gain root's privileges, or for graphical apps like the Nautilus file browser you can launch them with the prefix "gksudo".

So for example to launch a root file browser, hit alt-F2 and type:
```
gksudo nautilus
```


Is this the best way (safest) to change the privileges on the other users home directories so that they will not be able to see each others files?

---

### Post by bodhi.zazen on 2011-05-29
> **rbowen1 said:**
> Is this the best way (safest) to change the privileges on the other users home directories so that they will not be able to see each others files?

There is no best way, use what works.

If you wish a graphical interface, use gksu nautilus.

If you want to use the command line, use sudo -i

Or you can script it ..

for i in `ls /home` do ...

---

### Post by Paqman on 2011-05-30
Absolutely. Using the command line or the file browser achieves exactly the same thing, you're just changing the privileges on those files and folders. Use whichever method you prefer.

You'll find that pretty much anything on Linux can be done either through the command line, or through a graphical tool. They both do exactly the same thing.

---

### Post by rbowen1 on 2011-05-31
Thanks to everyone for their assistance.    gksudo nautilus works great as a graphic interface.

 I am trying to expand my knowledge of Linux and would like to learn more on the command line.    Can anyone recommend any links that have the command line codes listed in a fairly straight forward (easy) to understand fashion? 

 What commands would I use to get to the home directories?   What command to view the current properties of the home directories?  What command to change the properties of the home directories?  

Thanks again for all assistance

---

### Post by bodhi.zazen on 2011-05-31
> **rbowen1 said:**
> Can anyone recommend any links that have the command line codes listed in a fairly straight forward (easy) to understand fashion? 

[http://linuxcommand.org/](http://linuxcommand.org/)

At least the first few pages of that tutorial.

Best way to learn the command line is to use the command line, learn to read the man pages.

---

### Post by mikodo on 2011-05-31
Welcome,

Along with the above mentioned tutorial by bodhi.zazen and probably more suggestions to follow, I want to add three browsers that always show a wealth of information when searching CLI topics:

[http://crunchbang.org/ubuntu-search-engine](http://crunchbang.org/ubuntu-search-engine)

[http://www.google.com/linux](http://www.google.com/linux)

[http://www.go2linux.org/arch-google/arch-search-engine.html](http://www.go2linux.org/arch-google/arch-search-engine.html)

A few other useful resources on Ubuntu:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)


Enjoy!

---

### Post by rbowen1 on 2011-05-31
This issue is solved.    :p:p:p:p
Thanks again for everyone's help.  I just changes the permissions of the home directories using the command line.   :KS:KS:KS:KS

---

