---
title: "unable to record passphrase"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by n213978745 on 2011-02-03
hi, everyone

Recently I switched to xubuntu from ubuntu, and I have use the options and encrypt my home directory.

After I have install the OS into my computer, I tried to "run this action now" in the following image:
[IMG]http://img220.imageshack.us/img220/582/screenshot0203201101444.png[/IMG]


It's a windows that prompt me to record my passphrase after a login into my newly created account.  But unfortunately when I click "Run this action now", nothing happens at all.

As a result I am unable to record my passphrase and I am not sure will this affect my security of Home Directory or not.


I also tried to run the following command as shown in the windows:
```
$ ecryptfs-unwrap-passphrase
```and the output is:
```
Passphrase:
```And there has nothing following after passphrase
when I click enter again, it said:
```
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs

```May I ask how should I fix this problem?  I don't mind to work on the CLI and I am used to it already.  Thank you for everyone who's trying to help me.

---

### Post by Kirboosy on 2011-02-03
Did you try to enter your login password?

---

### Post by n213978745 on 2011-02-03
> **Caboose885 said:**
> Did you try to enter your login password?


It works and after I enter the password, it outputs a series of number(or passphrase).  I thank you for answering my question.

I just want to say that the command output of encryptfs-unwrap-passphrase is confusing to me.  Even though I tried to read the manual via $ man ecryptfs-unwrap-passphrase , it doesn't help much.

And when it said "passphrase:" on the output, I misunderstand it as "output a _passphrase_ for my home directory", rather "asking for input of your user's _password_."

I really wish they can change the command a bit :3

Thanks for solving my problem and I appreciate your help :)

---

