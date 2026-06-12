---
title: "Moving a folder into WWW (chown)"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-08
I've been away from the computer for over a month- and have forgotten so much of what I've learned of linux.  I  am  trying to  copy and paste a folder into var/www from the desktop  (a folder with the Joomla CMS).  I tried (in the var directory)  'chown b***dy /www (so I could have ownership of www thus having permission to paste into it) but it says that is not permitted. I think I was successful in  changing the ownership of var (chown b***dy /var) but how do I move a folder into /var/www? Thanks in advance.

---

### Post by taurus on 2009-03-08
You need root privilege if you want to write to somewhere outside your $HOME.  If you need to move something to /var/www, open a terminal and run nautilus with root privilege.

```
gksudo nautilus
```
or
```
sudo mv filename /var/www
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lakeside5 on 2009-03-08
Thanks, I have tried that and  just tried it again but must be doing something wrong. I don't really use the   command that lets me be root, I usually use sud, os    I typed (in the Desktop  dir. where Joomla folder is)  sudo mv  /Joomla /var/www and it  says  mv: cannot stat `/Joomla': No such file or directory.  I get the  same result for sudo mv /Desktop/ Joomla /var/www when I am at the  root  directory

---

### Post by taurus on 2009-03-08
> **Lakeside5 said:**
> Thanks, I have tried that and  just tried it again but must be doing something wrong. I don't really use the   command that lets me be root, I usually use sud, os    I typed (in the Desktop  dir. where Joomla folder is)  sudo mv  /Joomla /var/www and it  says  mv: cannot stat `/Joomla': No such file or directory.  I get the  same result for sudo mv **[COLOR="Red"]/Desktop[/COLOR]**/ Joomla /var/www when I am at the  root  directory

If Joomla is on your desktop, then it should look like this.

```
sudo mv **[COLOR="Blue"]~/Desktop[/COLOR]**/Joomla /var/www
```

---

### Post by Lakeside5 on 2009-03-08
Must have finally  'chowned' www properly, seems I can cut and paste into www, even create a Joomla  folder there, just don't have the hang of moving folders in the terminal I guess, keeps saying that the Joomla folder doesn't  exist, hmm  thanks agian

---

