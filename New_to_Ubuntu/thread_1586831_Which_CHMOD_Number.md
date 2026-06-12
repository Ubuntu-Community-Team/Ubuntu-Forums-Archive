---
title: "Which CHMOD Number?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by adamjkok on 2010-10-02
I want to create a public_html directory in a user's home folder for Apache2 to serve.

[LIST]
[*]I'll do this as root by using *sudo*
[*]Needs to be readable by everybody
[*]Needs to be owned, readable, and writable by user
[/LIST]
Which CHMOD number do I use? Is there something else that I need to run?

---

### Post by Lateralis on 2010-10-02
If you run the sudo command then the directory will be owned by root.  If you want to set the user as the owner then you need to run the chown command.  

[This page]("http://catcode.com/teachmod/") gives a good guide to the use of chmod.

---

### Post by gzarkadas on 2010-10-02
755 (rw for user r for group, others). You must also make sure that the user's home folder has the others' x bit activated. You can do all of this inside a terminal window by typing the following commands (substitute [account-name] with the account's login name):

```

sudo -i
cd /home
chmod g+x,o+x [account-name]
mkdir -p -m 755 /home/[account-name]/public_html
chown [account-name]:[account-name] /home/[account-name]/public_html
exit

```See [http://en.wikipedia.org/wiki/Filesystem_permissions](http://en.wikipedia.org/wiki/Filesystem_permissions), section "Notation of traditional Unix permissions" for a detailed presentation and mapping between permissions and chmod numbers.

---

### Post by sisco311 on 2010-10-02
Assuming that you have a world-readable home directory, create it as your regular user:
```
mkdir ~/public_html
```

---

### Post by abohsin on 2010-10-02
I recommend you try '755', so owner has full permission, others have read and execute, without the ability to write. I have learned that with permissions, sometimes you need to use trial and error.

---

