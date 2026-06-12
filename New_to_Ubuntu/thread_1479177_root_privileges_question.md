---
title: "root privileges question"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-10
I recently installed Ubuntu and also read the free pocket guide book. According to the book, by default ubuntu doesnot create root account. We can create one by typing 

sudo passwd root 

Say the password is p_root

I am logged in as an ordinary user sid and say the password is p_sid.
When I am doing system admin task like update manager etc. it is asking for a password. But not the root password but p_sid. This seems confusing. In other distros we have 

root and p_root password
sid  and p_sid password

and for doing admin task we have to enter p_root.

Please could someone remove this confusion...

---

### Post by Paqman on 2010-05-10
> **oaridus said:**
> 
Please could someone remove this confusion...

Ubuntu uses a different security model from other distros. You don't need a root password, just enter your user password when prompted.

For commands in the terminal, prefix your command with "sudo" to execute it as root.

---

### Post by parn on 2010-05-10
umm you dont really need to login as root. Because the user account you are using has administrative privilege (sudoer), you can use p_sid to accomplish administrative task.

It has been like this for a few year...

---

### Post by Calash on 2010-05-10
Please see the following guide.  Basically the Root account is disable as Ubuntu uses a different security model.  Unless you have an actual need to use that account, and as of yet I have not seen one in my experience, stick with sudo.


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oaridus on 2010-05-10
thanks, another small question. I didn't find the user sid in the sudoers list file. Then how is sid able to do admin task in ubuntu.

---

### Post by Calash on 2010-05-10
By default the admin group is listed in the sudoers file.  As long as your user is a member of the admin group they will have Sudo rights.

---

### Post by oaridus on 2010-05-10
thanks for clarifying.

---

### Post by emoguitarist06 on 2010-05-10
Please mark as solved:)

---

### Post by philinux on 2010-05-10
> **emoguitarist06 said:**
> Please mark as solved:)

you do that yourself with Thread Tools

---

