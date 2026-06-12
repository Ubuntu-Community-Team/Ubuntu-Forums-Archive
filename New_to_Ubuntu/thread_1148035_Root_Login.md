---
title: "Root Login"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Marvin666 on 2009-05-04
How do I enable root login on xubuntu 9.04? Also, I already have a password set for it.

---

### Post by tommynz1975 on 2009-05-04
in short ubuntu dosent login via root,  and no password for root..

we use the command Sudo  to  imitate root..  and this is YOUR normal password....

all your users who are set as ADMIN can use root in this way..

example

```
sudo apt-get update
```  



I think the reason root came with NO password is that a phreaker will try and access your system, and think  I have the user name  ROOT and then will only need to guess the password..

I suggest setting root back to NO password.  if you need help do ask..

---

### Post by Marvin666 on 2009-05-04
I know that, but I know there's an option somewhere that lets you login as root at the normal screen, instead of bringing up a command line.

---

### Post by lisati on 2009-05-04
The preferred method for doing stuff which requires "root" privileges in Ubuntu is through the use of "sudo", which has already been illustrated by tommynz1975

You might want to have a look here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm)

---

### Post by SunnyRabbiera on 2009-05-04
Root login is not advised anyhow, its not good for your system.

---

### Post by Didius Falco on 2009-05-04
> **Marvin666 said:**
> How do I enable root login on xubuntu 9.04? Also, I already have a password set for it.

Read this:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by _Purple_ on 2009-05-04
> **Marvin666 said:**
> I know that, but I know there's an option somewhere that lets you login as root at the normal screen, instead of bringing up a command line.

Once you activate the root account, you will be able to login using root account in login screen but it is not at all a good idea to run everything as root. Please check the links given earlier.

---

### Post by inobe on 2009-05-04
> **Marvin666 said:**
> How do I enable root login on xubuntu 9.04? Also, I already have a password set for it.


sudo

edit: there is absolutely "no reason" to do what you are describing, it is very dangerous and not recommended :)

---

### Post by Marvin666 on 2009-05-04
I only intend to login as root when absolutely necessary, and know the possible implications of using root when not needed. I saw something that told you how to log in as root, but I accidentally closed sea monkey with it up, and haven't been able to find it since.

---

### Post by inobe on 2009-05-04
just tell us what you need to do and we will help you with that so to avoid something completely taboo ..

---

### Post by aysiu on 2009-05-04
> **Marvin666 said:**
> I only intend to login as root when absolutely necessary It's not absolutely necessary.

More details here... > **Didius Falco said:**
> Read this:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

