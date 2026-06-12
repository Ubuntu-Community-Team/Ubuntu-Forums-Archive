---
title: "Script to log in through SSH"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by steve228 on 2010-06-15
I am looking for a way to write a bash or shell script to log in to an SSH account.

Currently I only have a bash alias that interprets the command.

I want to be able to write something that I can run the script and it logs me into the SSH account without any password-asking intervention.

Can anyone point me to a tutorial or maybe a code snippet?

Thanks

---

### Post by bodhi.zazen on 2010-06-15
Use a key to log into ssh.

You can use and empty key (no password) if you wish.

I am sure you understand the security implications of disabling the password requirement.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

The other option is to write a script on the server. You then run the script with ssh.

ssh user@server /path/to/script

---

### Post by steve228 on 2010-06-17
Yeah that script your talking about... I have an ssh account that I log into to write source code... I want to be able to have a script that automatically enters the password...

But if I use a key like you posted, would that change the password I use to login?

---

### Post by sdennie on 2010-06-17
If you use an ssh key, you will only be prompted for a password if you give a password to the key that you create with ssh-keygen.

---

