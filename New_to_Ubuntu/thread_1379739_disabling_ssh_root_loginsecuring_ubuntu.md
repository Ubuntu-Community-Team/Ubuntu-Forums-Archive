---
title: "disabling ssh root login/securing ubuntu"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Fika on 2010-01-12
As part of trying to secure my ubuntu 9.10 system, I am trying to follow the steps in this article. 

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

The one I am having trouble with


[LIST]
[*]*Disabling SSH root login*
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:PermitRootLogin yes
to
PermitRootLogin no




When I open this file which is ssh_config, not sshd_config as in the post, there is no line that says permit root login. Is there supposed to be according to this article? Same with the steps they give about reconfiguring shared memory; when I try to edit the fstab file it is read only and won't let me save changes. 

[/LIST]

---

### Post by spiderbatdad on 2010-01-12
You may be trying to secure services you are not running. Have you actually installed openssh and are running the server? I think not, as you don't know how to edit files belonging to root.
Your Ubuntu system is generally safe as a default installation. Be sure to only install software from the repositories and trusted sources. Use noscript add-on for firefox. Mucking around system files without knowing what you're doing will only break your system and or introduce vulnerabilities. I hope I have not sounded harsh toward you. Just a tad irritated at the article that presumes to educate linux users about security.

---

### Post by CharlesA on 2010-01-12
Huh?

The config file that SSH uses on my Ubuntu box is /etc/ssh/sshd_config

Running Ubuntu 9.10.

---

### Post by spiderbatdad on 2010-01-12
You may be trying to secure services you are not running. Have you actually installed openssh and are running the server? I think not, as you don't know how to edit files belonging to root.
Your Ubuntu system is generally safe as a default installation. Be sure to only install software from the repositories and trusted sources. Use noscript add-on for firefox. Mucking around system files without knowing what you're doing will only break your system and or introduce vulnerabilities. I hope I have not sounded harsh toward you. Just a tad irritated at the article that presumes to educate linux users about security, without supplying any real explanations...like do this and you're safe.
If you must edit root files, you have to open the files as super-user. Run the command from your terminal. To edit a root owned file, run ```
gksu gedit /directory/file
```

---

